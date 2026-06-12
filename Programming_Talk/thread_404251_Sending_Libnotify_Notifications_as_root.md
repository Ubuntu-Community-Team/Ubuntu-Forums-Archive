---
title: "Sending Libnotify Notifications as root"
date: 2007-04-08
forum: Programming Talk
---

### Post by simplyw00x on 2007-04-08
I've tried to have procmail send me notifications when I have new mail:
```
:0 c
| formail -fc -x Subject |  sed -e 's/carl.*2007  //' | sed -e 's/<.*>//' | sed 
-e 's/^/\"/g' | sed -e 's/$/\"/g' | xargs -t notify-send -i stock_mail "New Mail
"
```

My procmail log shows me that notify-send is whining about dbus:
> From carl  Sun Apr  8 09:59:49 2007
 Subject: Test #3
  Folder: /home/carl/Mail/new/1176022789.13457_0.puzzlement                2099
notify-send -i stock_mail New Mail  Test #3 
libnotify-Message: Unable to get session bus: Failed to execute dbus-launch to a
utolaunch D-Bus session

I've tried guides like [http://gnome-hacks.web.com/hacks.html?id=82](http://gnome-hacks.web.com/hacks.html?id=82) and [http://blog.drinsama.de/erich/en/linux/2006021003-gnome-hack-of-the-day.html](http://blog.drinsama.de/erich/en/linux/2006021003-gnome-hack-of-the-day.html), but there are a few problems:

**I don't have gnome-session running. Should I?**
```
carl@puzzlement:~$ ps -e | grep gnome-session
carl@puzzlement:~$ gnome-session
gnome-session: you're already running a session manager
carl@puzzlement:~$
```

**Notification-daemon is ignoring env vars**
```
carl@puzzlement:~$ echo $DBUS_SESSION_BUS_ADDRESS
unix:abstract=/tmp/dbus-XJKEnaHUDC,guid=d8a9946c6fecedde09dd0d004618b261
carl@puzzlement:~$ sudo -s
Password:
root@puzzlement:~# export DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-XJKEnaHUDC,guid=d8a9946c6fecedde09dd0d004618b261
root@puzzlement:~# notify-send Test Test
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```
This is not right. I've confirmed that this is the right bus address on numerous occasions but no dice. Any help?

---

### Post by kcnnc on 2008-10-24
Has anyone found a solution for this?

---

### Post by FuturePusher on 2010-06-07
Old thread I know, but I stumbled upon this via Google when looking around for causes of errors where libnotify can't connect to the dbus daemon... just thought I should throw in my solution to this, in case original posters or anyone else reading gets use of it:


Quite simple really - all You need to do is make the job/script running as root, run the notify-send as the user who's on display :0 ... (in other words, the user running the GUI; X in our case).

This, with commands taking arguments (like notify-send), is easiest achieved with for example:   sudo -u carl sh -c 'notify-send ...'
(Replace "carl" with relevant username! Lab around with it... ;) )


As for finding out who's on the GUI, try the followin to get an idea... (NOTE: copy-&-paste this so You don't lose any less visible space character!) :

 GUI_user="$( who | grep ' tty' | grep ' (:0' | cut -d ' ' -f 1 )"

(Now You have that user's username in the variable GUI_user, do this to see:   echo $GUI_user  )

---

