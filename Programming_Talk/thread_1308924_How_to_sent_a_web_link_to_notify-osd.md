---
title: "How to sent a web link to notify-osd?"
date: 2009-11-01
forum: Programming Talk
---

### Post by kurtkraut on 2009-11-01
I'm working on a [shell script]("http://code.google.com/p/pomamonitor/") (not Python) that warns me if a host/IP stops responding ping. The warning is sent to the user using the **notify-send** command, to make it appear in notify-osd. Here is an example:

[IMG]http://pomamonitor.googlecode.com/files/animated-pomamonitor-alert.gif[/IMG]

Since many server I monitor are webserver, I'd like to make a clicable link to the server URL. In the animated GIF above, [www.textolivre.org](www.textolivre.org) is down. I'd like to allow the desktop user to click on [www.textolivre.org](www.textolivre.org) and be redirected to this website.

Any suggestions?

---

### Post by kostkon on 2009-11-01
Unfortunately, you can't. *Notify-OSD* doesn't allow any actions. For more info, you could check [here]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines").

On the other hand, it will work with *notification-daemon* (I think), i.e. in other Gnome-based OSes, but not in Ubuntu.

ADDED:
You can check if the system that the script runs on has Notify-OSD. In Python would be something like this:
```
if pynotify.get_server_info()["name"] == "notify-osd":
   etc
```

In case you want to show clickable links in systems that use the *notification-daemon*, then first of all, to be sure, you could check if the daemon accepts links in its body, in python would be something like this
```
if "body-hyperlinks" in pynotify.get_server_caps():
   etc
```
and then put your URL as an HTML link in the notification, e.g.
```
notif = pynotify.Notification("Host fora do ar", "<a href='http://www.textolivre.com/'>www.textolivre.com</a>", "")
notif.show()
```

---

