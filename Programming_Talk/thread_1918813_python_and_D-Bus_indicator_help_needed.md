---
title: "python and D-Bus indicator help needed"
date: 2012-02-01
forum: Programming Talk
---

### Post by xaegis on 2012-02-01
Hello I'm writing a small program to notify me that I have a message. How do I get the little Blue Envelope to light up and add messages to the  message counter there. I cant figure out how the D-Bus works. I suspect i have to call the dbus mmodule and send a signal to"
 Telepathy @: "org.freedesktop.Telepathy.Connection.Interface.MailNotification.UnreadMailsChanged"

I found this site but cant figure out how to use it properly.
[http://developer.ubuntu.com/api/ubuntu-11.10/python/Indicate-0.6.html](http://developer.ubuntu.com/api/ubuntu-11.10/python/Indicate-0.6.html)

Does anyone have any clues to start me down the right track?

Thanks,

-e

---

### Post by ofnuts on 2012-02-02
In a bash script you would use notify-send for this. [This page]("http://blog.mpathirage.com/2009/09/12/using-libnotify-in-ubuntu-9-04/") explains how to send notifications in various languages including python**.**

---

### Post by xaegis on 2012-02-02
Thank you for the reply. Pynotify will send onscreen messages but will not Light up the "Blue Envelope" in the message bar, I also cannot locate the API command to increment/decrement the email messages icons.

Would you know which API I would have to use to get that functionality, or did I just miss it?

Thanks again.

:D

---

### Post by ofnuts on 2012-02-03
> **xaegis said:**
> Thank you for the reply. Pynotify will send onscreen messages but will not Light up the "Blue Envelope" in the message bar, I also cannot locate the API command to increment/decrement the email messages icons.

Would you know which API I would have to use to get that functionality, or did I just miss it?

Thanks again.

:DI'm using the KDE desktop and  there is no "Blue envelope" on it.  So the first thing I would do is to figure out what is behind this widget (Gnome? Unity? a specific messaging application?) and how/what is spies on the D-Bus.

---

### Post by xaegis on 2012-02-05
Ok after some research I suspect what I am really looking for is access to the indicator-applet.

I am following the tutorial [HERE]("http://www.gnomejournal.org/article/67/an-introduction-to-the-message-indicator"):

I keep getting errors even after I have changed a questionable part of the code. from:

```

    # Setup the message
    indicator = indicate.IndicatorMessage()
    indicator.set_property("subtype", "im")
    indicator.set_property("sender", "Test message")
    indicator.set_property("body", "Test message body")
    indicator.set_property_time("time", time())
    indicator.show()
    indicator.connect("user-display", display)


```

to

```

    # Setup the message
    indicator = indicate.Indicate()
    indicator.set_property("subtype", "im")
    #indicator.set_property("subtype", "email")
    indicator.set_property("sender", "Test message")
    indicator.set_property("body", "Test message body")
    indicator.set_property_time("time", time())
    indicator.show()
    indicator.connect("user-display", display)


```

The code seems to run with the changes but there is no output at all.
any suggestions?

---

