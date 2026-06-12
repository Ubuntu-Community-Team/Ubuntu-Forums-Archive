---
title: "Notifications with buttons? Only getting dialogs"
date: 2010-06-25
forum: Programming Talk
---

### Post by detrate on 2010-06-25
With the redesign of the notification system in ubuntu, as detailed in [this post](http://ubuntuforums.org/showpost.php?p=8213898&postcount=10), how can I create a notification that is either clickable or has buttons that I can click?

The examples ubuntu provides for the would be application indicator balloons "/usr/share/doc/python-notify/examples"
show me popup dialogs, which is not what a I want:

**What I'm getting**
[img]http://pics.nexuizninjaz.com/images/ez2pu6bbygk6opthxidi.png[/img]

**What I want** (more or less)
[img]http://pics.nexuizninjaz.com/images/0yl1uae6j0kl183o30dm.png[/img]

I want some sort of unobtrusive timed object kicked off by a script that I can click to execute an action.

---

### Post by detrate on 2010-06-25
it appears you cannot.

[http://projecthamster.wordpress.com/2009/04/01/ubuntu-jaunty-and-the-new-notification-sweetness/](http://projecthamster.wordpress.com/2009/04/01/ubuntu-jaunty-and-the-new-notification-sweetness/)

I tried
```
sudo apt-get remove notify-osd
```
but it didn't appear to change anything.

a popup dialog is not unobtrusive


I can't believe I'm wearing my ubuntu tshirt right now

---

### Post by juancarlospaco on 2010-06-25
I use a modified code of my Splashscreen.py
that ignore window decorator, place on the corner of the screen,
on top of all windows, get temporal focus, have buttons, and with timeout.

Or if _no clickable_ thing is needed i use Ubuntu's libnotify.

*I use Tk, and no extra lib required with this method.*

---

### Post by detrate on 2010-06-25
:-P

I was actually just coming to post that I ripped out notify-osd and installed the old system thanks to [this post](http://ubuntuforums.org/showpost.php?p=8559795&postcount=8), which has given me the popups like I wanted.

what is tk?

---

### Post by juancarlospaco on 2010-06-25
Tk = GTk = Qt = Wx

Python Built-In GUI Toolkit


This is actually my Splash Screen using Tk:
[IMG]http://file.status.net/identica/juancarlospaco-20100624T021321-qapycyp.jpeg[/IMG]

---

### Post by detrate on 2010-06-26
I ended up writing about my experience and solution here:

[http://www.doknowevil.net/2010/06/25/ubuntu-notifications-osd-notify-sucks-notifications-daemon-rocks-exploiting-the-goodness-with-compiz/](http://www.doknowevil.net/2010/06/25/ubuntu-notifications-osd-notify-sucks-notifications-daemon-rocks-exploiting-the-goodness-with-compiz/)

---

### Post by juancarlospaco on 2010-06-26
But you need to adapt the App to the environtment, not the Environtment to your app.

:s

---

### Post by detrate on 2010-06-26
I've exploited the icon functionality to show me (part of) an image preview (optionally) now:

[img]http://interwebninja.com/compiz-screenshots/screenshot31.png[/img]

Also, the behavior of this notification system is far better.

[http://interwebninja.com/videos/notification-daemon.ogv](http://interwebninja.com/videos/notification-daemon.ogv)

[video of my script in action](http://interwebninja.com/videos/compiz-screenshot-piped-to-notification-daemon-for-upload.ogv)

I'm going to adapt my environment to my app if the current environment sucks.  The new notification system does not provide actions.  I'm not interested in consumerism and being told what is best.  I like the freedom to mix and match and learn what works best for ME and my workflow.

The new notification system is nothing but an annoyance and hindrance to my workflow

---

