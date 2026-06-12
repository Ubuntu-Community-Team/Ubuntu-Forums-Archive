---
title: "Python-libnotify showing weird behaviour with xfce4-notifyd and notify-osd"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by ranrag on 2012-07-01
I am trying to play with libnotify's python bindings. I got** [this code]("http://pastie.org/4181931") **from* /usr/share/doc/python-notify/examples* and it is showing different behaviour with xfce4-notifyd and notify-osd.

**Case-1 with xfce4-notifyd**

[IMG]http://i.stack.imgur.com/jqfgG.png[/IMG]


**Case-2 with notify-osd**

[IMG]http://i.stack.imgur.com/FQjdC.png[/IMG]

You can see the difference in both the cases. In 1st case the **action** is integrated in the form of** button** in xfce4-notifyd whereas in 2nd case this is not happening. In 2nd case it just shows up as a **new window**.

So, can anyone tell me why I am observing this weird behaviour and how do I add action buttons to notify-osd notifications.

PS: I am using the patched version of notify-osd. My notification with notify-osd looks like

[IMG]http://i.stack.imgur.com/C5ADX.png[/IMG]

---

