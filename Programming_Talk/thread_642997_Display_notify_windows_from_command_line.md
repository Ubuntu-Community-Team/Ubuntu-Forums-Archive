---
title: "Display notify windows from command line"
date: 2007-12-17
forum: Programming Talk
---

### Post by nsg on 2007-12-17
I'm not sure what it's called, but the notify-window that displays information like "It's now safe to remove the removable device ...", "Low diskspace on ..." and so on. (notification-daemon?).

Is there any way to display a message from the command line? like:

```
> foobar hello world
```

... to display "hello world" in the notification window.

I like to write small scripts to monitor things, and a easy way to display messages would be nice.

I have used xosd_cat (XOSD) before for the same ting, but it's so ugly.

---

### Post by mridkash on 2007-12-17
try zenity
see man zenity

---

### Post by nsg on 2007-12-17
> **mridkash said:**
> try zenity
see man zenity

```
zenity  --notification  --text "foobar"
```

could work in some of my scripts, but still I need a window  to write text in, zenity  --info  is not a option, I need something discrete in the corner of the screen.

---

### Post by nsg on 2007-12-17
Found it!

Command:
```
notify-send
```

In package:
```
sudo apt-get install libnotify-bin
```

---

### Post by biji on 2009-04-09
nice found :)

---

### Post by 3rag0n on 2009-04-09
for kde u can use knotify... just see its man page.

---

### Post by tonychen123 on 2009-09-04
Hi, I have a problem with notify-send. 
I command that[COLOR=DarkGreen] _notify-send "Click me to close me." -t 0_[/COLOR], but my computer display a window instead of notify tips. 

i.e. in my computer the notify-send could not specify the time, or it will display the window instead.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127392&stc=1&d=1252056873[/IMG]

---

### Post by KIAaze on 2009-09-17
Strange.

I'm currently under OpenSUSE 10.3 with KDE 3.

I copy/pasted your command in my terminal and it displayed a nice notification bubble in the bottom-right corner of my screen.
I had to click it to close it.

---

### Post by justinjstark on 2010-03-29
> **tonychen123 said:**
> Hi, I have a problem with notify-send. 
I command that[COLOR=DarkGreen] _notify-send "Click me to close me." -t 0_[/COLOR], but my computer display a window instead of notify tips. 

i.e. in my computer the notify-send could not specify the time, or it will display the window instead.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=127392&stc=1&d=1252056873[/IMG]

You cannot do this with ubuntu's new notification system.  Notification bubbles are only to be displayed for a very short time.  If you try to make it clickable or add buttons it will appear as a window because the notification bubbles are not meant for the behavior you want.

---

