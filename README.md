# notifications
code about permission and interfaces 
initialisation:
FlutterLocalNotificationsPlugin flutterLocalNotificationsPlugin = FlutterLocalNotificationsPlugin();
//head project. icon drawable mein dalna hsain abhi (reminder)

var initializationSettingsAndroid = AndroidInitializationSettings('app_icon');
var initializationSettingsIOS = IOSInitializationSettings(
    onDidReceiveLocalNotification: onDidReceiveLocalNotification);
var initializationSettings = InitializationSettings(
    initializationSettingsAndroid, initializationSettingsIOS);
await flutterLocalNotificationsPlugin.initialize(initializationSettings,
    onSelectNotification: selectNotification);

IOSInitializationSettings class:
//3 parameter leti hon sound ,alert aur badge ki permission k lia

FlutterLocalNotificationsPlugin flutterLocalNotificationsPlugin =  FlutterLocalNotificationsPlugin();
var initializationSettingsAndroid =
    AndroidInitializationSettings('app_icon');
var initializationSettingsIOS = IOSInitializationSettings(
        requestSoundPermission: false,
        requestBadgePermission: false,
        requestAlertPermission: false,  // filhal  error hai .run after create interface
        onDidReceiveLocalNotification: onDidReceiveLocalNotification,
    );
var initializationSettings = InitializationSettings(
    initializationSettingsAndroid, initializationSettingsIOS);
await flutterLocalNotificationsPlugin.initialize(initializationSettings,
   onSelectNotification: onSelectNotification);


Grouping Notification: 
String groupKey = 'com.android.example.WORK_EMAIL';
String groupChannelId = 'channel id';
String groupChannelName = 'channel name';
String groupChannelDescription = 'grouped channel description';

AndroidNotificationDetails firstNotificationAndroidSpecifics =
 AndroidNotificationDetails(
     groupChannelId, groupChannelName, groupChannelDescription
       importance: Importance.Max,
     priority: Priority.High,
     groupKey: groupKey);

// multiple notification k lia...
NotificationDetails firstNotificationPlatformSpecifics =
    NotificationDetails(firstNotificationAndroidSpecifics, null);
await flutterLocalNotificationsPlugin.show(1, 'text',
    'text', firstNotificationPlatformSpecifics);
AndroidNotificationDetails secondNotificationAndroidSpecifics =
    AndroidNotificationDetails(
        groupChannelId, groupChannelName, groupChannelDescription,
        importance: Importance.Max,
        priority: Priority.High,
        groupKey: groupKey);
NotificationDetails secondNotificationPlatformSpecifics =
    NotificationDetails(secondNotificationAndroidSpecifics, null);
await flutterLocalNotificationsPlugin.show(
    2,
    'Rehan Butt',
    
    secondNotificationPlatformSpecifics);

// create the summary notification 
List<String> lines = List<String>();


// yahan interface banne k bad list add krni hai


InboxStyleInformation inboxStyleInformation = InboxStyleInformation(
    lines,
    contentTitle: '5 new messages',
    summaryText: 'Rehanbutt@gmail.com');
    
    
    // handled their interaction with the previous notification.
val repliedNotification = Notification.Builder(context, CHANNEL_ID)
        .setSmallIcon(R.drawable.ic_message)
        .setContentText(getString(R.string.replied))
        .build()

// Issue the new notification.
NotificationManagerCompat.from(this).apply {
    notificationManager.notify(notificationId, repliedNotification)
}
val builder = NotificationCompat.Builder(this, CHANNEL_ID).apply {
    setContentTitle("Picture Download")
    setContentText("Download in progress")
    setSmallIcon(R.drawable.ic_notification)
    setPriority(NotificationCompat.PRIORITY_LOW
}
val PROGRESS_MAX = 100
val PROGRESS_CURRENT = 0
NotificationManagerCompat.from(this).apply {
    // Issue the initial notification with zero progress
    builder.setProgress(PROGRESS_MAX, PROGRESS_CURRENT, false)
    notify(notificationId, builder.build())

    builder.setContentText("Download complete")
            .setProgress(0, 0, false)
    notify(notificationId, builder.build())
}

Intent fullScreenIntent = new Intent(this, ImportantActivity.class);
PendingIntent fullScreenPendingIntent = PendingIntent.getActivity(this, 0,
        fullScreenIntent, PendingIntent.FLAG_UPDATE_CURRENT);

NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID)
        .setSmallIcon(R.drawable.notification_icon)
        .setContentTitle("My notification")
        .setContentText("Hello World!")
        .setPriority(NotificationCompat.PRIORITY_DEFAULT)
        
        Intent intent = new Intent(this, AlertDetails.class);
intent.setFlags(Intent.FLAG_ACTIVITY_NEW_TASK | Intent.FLAG_ACTIVITY_CLEAR_TASK);
PendingIntent pendingIntent = PendingIntent.getActivity(this, 0, intent, 0);

NotificationCompat.Builder builder = new NotificationCompat.Builder(this, CHANNEL_ID)
        .setSmallIcon(R.drawable.notification_icon)
        .setContentTitle("My notification")
        .setContentText("Hello World!")
        .setPriority(NotificationCompat.PRIORITY_DEFAULT)
        // Set the intent that will fire when the user taps the notification
        .setContentIntent(pendingIntent)
        .setAutoCancel(true);
        
