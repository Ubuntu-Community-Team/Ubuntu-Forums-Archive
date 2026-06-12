---
title: "notify error"
date: 2011-08-04
forum: Programming Talk
---

### Post by Script Warlock on 2011-08-04
can anyone help me on this:

> void
ClientWin::dispMessage(FXString &msgstr, int timeout)
{
  //FXMessageBox::information(getRoot(),
  //			    MBOX_OK,_("Admin Message!"), msgstr.text());
#ifdef HAVE_NOTIFICATION
  NotifyNotification* notification;
  gboolean            success = true;
  GError*             error = NULL;

  //if (notify_init ("mkahawa-client"))
  {
    notify_init("mkahawa-client");
    /* try the mkahawa-client notification */
    notification = notify_notification_new (
					    "Message from Cyber Admin:",
					    msgstr.text(),
					    "/usr/share/pixmaps/mkahawa-icon.png",
					    NULL);
    error = NULL;
    notify_notification_set_timeout(notification, timeout * 1000);
    success = notify_notification_show (notification, &error);
    notify_uninit();
  }
  if (!success)
    {
    //use alternative
#endif
  FXDialogBox dialog(getRoot(),_("Admin Message"));
  FXLabel lbl1(&dialog,_("Message from Administrator"));
  FXLabel lbl2(&dialog, msgstr);
  FXVerticalFrame *vframe =
    new FXVerticalFrame(&dialog,LAYOUT_FILL_X|LAYOUT_FILL_Y,0,0,0,0,0,0,0,0,0,0);
  FXHorizontalFrame *hframe =
    new FXHorizontalFrame(vframe,LAYOUT_FILL_X|LAYOUT_FILL_Y);
  FXButton okbtn(hframe,_("   Ok   "),NULL,&dialog,FXDialogBox::ID_ACCEPT, 
		 LAYOUT_TOP|LAYOUT_CENTER_X);
  okbtn.setWidth(100);
  if (dialog.execute(PLACEMENT_SCREEN)){
    // do nothing
  }

#ifdef HAVE_NOTIFICATION
}
#endif
  
}

and the result is:

** (process:1668): CRITICAL **: dbux_g_proxy_disconnect: assertion 'DBUS_G_PROXY_DISTROYED (proxy)' failed

i have a [video]("http://www.youtube.com/watch?v=5q0aeDJMdH8") clip that demos the result starting at 6:40

---

### Post by hakermania on 2011-08-04
I am too lazy to take a look to your code ( :D )
I'll post a part of my code here that actually shows a notification and then updates it. It works without warnings/errors:
```


    QString body;
    if(warning_notification==0){
        if(!QFile(qimage).exists() || QImage(qimage).isNull())
            return;
        body=QObject::tr("Your current wallpaper has changed!");
    }
    else if(warning_notification==1)
        body=QObject::tr("There are lots of invalid images or too few from the ones you have selected. Please 'clear' your selected images and try again!");
    else if(warning_notification==2)
        body=QObject::tr("You didn't have more than 1 picture in the list!");
    else if(warning_notification==3)
        body=QObject::tr("Unable to connect") + ". " + QObject::tr("Check your internet connection!");
    else if(warning_notification==4)
        body=QObject::tr("Live Earth Wallpaper is active and it will change every 30 minutes!");
    else if(warning_notification==5)
        body=QObject::tr("Requested Graphical User Interface! Every prior process has stopped!");
    if (!notify_init ("update-notifications"))
            return;
    if(notification_first_time_main){
        notification_first_time_main=false;
        /* try the icon-summary-body case */
        if(warning_notification==0)
            notification_main = notify_notification_new ( "Wallch", body.toLocal8Bit().data(), qimage.toLocal8Bit().data(), NULL);
        else
            notification_main = notify_notification_new ( "Wallch", body.toLocal8Bit().data(), NULL, NULL);
        error_main = NULL;
        success_main = notify_notification_show (notification_main, &error_main);
        if (!success_main)
        {
                g_print ("That did not work ... \"%s\".\n", error_main->message);
                g_error_free (error_main);
        }

        g_signal_connect (G_OBJECT (notification_main), "closed", G_CALLBACK (closed_handler), NULL);
        return;
    }
    /* update the current notification with new content */
    if(warning_notification==0)
        success_main = notify_notification_update (notification_main, "Wallch", body.toLocal8Bit().data(), qimage.toLocal8Bit().data());
    else
        success_main = notify_notification_update (notification_main, "Wallch", body.toLocal8Bit().data(), NULL);
    error_main = NULL;
    success_main = notify_notification_show (notification_main, &error_main);
    if (!success_main)
    {
            g_print ("That did not work ... \"%s\".\n", error_main->message);
            g_error_free (error_main);
            return;
    }
    g_signal_connect (G_OBJECT (notification_main), "closed", G_CALLBACK (closed_handler), NULL);

```

---

