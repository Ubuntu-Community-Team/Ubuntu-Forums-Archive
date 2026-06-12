---
title: "How to enable Numlock on startup in KDE"
date: 2006-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by PigCorpse on 2006-11-08
This guide is for _KDE_ users who want to have Numlock on at startup. numlockx only works in GNOME, but in KDE, this feature is already built in.

All you need to do is:

Open up /etc/kde3/kdm/kdmrc in a text editor. Search for "NumLock" and you should arrive at something that looks like the following:

```
# What to do with the Num Lock modifier for the time the greeter is running:
# "Off" - turn off
# "On" - turn on
# "Keep" - do not change the state
# Default is Keep
#NumLock=Off
```

Uncomment the last line so it looks like:

```
# What to do with the Num Lock modifier for the time the greeter is running:
# "Off" - turn off
# "On" - turn on
# "Keep" - do not change the state
# Default is Keep
NumLock=On
```

It's that simple!

---

### Post by TheWizzard on 2006-11-09
why not
**Menu -> System Settings -> Hardware -> Keyboard -> NumLock on KDE startup -> Turn on**

---

### Post by darkghost on 2006-11-09
This tip is nice (both ways work). I was thinking to set this problem, but I've been lazy recently and didn't search around.

Thanks for supporting a lazy Kubuntu user :D :D :D

Andy

---

### Post by PigCorpse on 2006-11-09
Because that turns it on after login. If you want it to turn on at bootup, then this is the way to do it.

---

### Post by anystupidname on 2008-02-14
The information above seems to be out of date. I was unable to follow it.
Instead, I did this:
Control Panel -> Peripherals -> Keyboards
(Turn On - Numlock at Startup)

---

### Post by drubin on 2008-02-27
[https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

---

### Post by drubin on 2008-02-27
Something funny in that file
```
#!/bin/sh
# Stolen from the debian kdm setup, aren't I sneaky
# Plus a lot of fun stuff added
#  -George
```

---

### Post by aysiu on 2008-02-27
> **anystupidname said:**
> The information above seems to be out of date. I was unable to follow it.
Instead, I did this:
Control Panel -> Peripherals -> Keyboards
(Turn On - Numlock at Startup)

> **TheWizzard said:**
> why not
**Menu -> System Settings -> Hardware -> Keyboard -> NumLock on KDE startup -> Turn on** Yes, I'm not quite sure why this tutorial has people editing configuration files. Even in 2005 (when I first started out with Mepis), KDE had the option to keep numlock on at startup.

---

### Post by dodle on 2008-08-24
I wanted to post how I got numlockx to work at kdm startup in case it helps somebody.  I didn't notice this posted anywhere in this thread and this was the only way that I got it to work.  The options in the control center only effect numlock after you log in.  

Open /etc/kde3/kdm/Xsetup and add the following to it:```
if [ -x /usr/bin/numlockx ]; then
      /usr/bin/numlockx on
fi
```

Edit:  I was able to figure this out with help from this page:  [http://wiki.archlinux.org/index.php/Activating_Numlock_on_Bootup]("http://wiki.archlinux.org/index.php/Activating_Numlock_on_Bootup").  According to this page Xsetup is located in /usr/share/config/kdm/Xsetup.  But I found it in /etc/kde3/kdm/Xsetup, I'm guessing that is because I am using a different version of kdm, or linux, or something.  Also this page says that all you have to add is "numlockx on".  I did not try this so I don't know if it works.

---

### Post by drubin on 2008-08-25
> **rubinboy said:**
> [https://help.ubuntu.com/community/NumLock](https://help.ubuntu.com/community/NumLock)

> **dodle said:**
> 
Open /etc/kde3/kdm/Xsetup and add the following to it:```
if [ -x /usr/bin/numlockx ]; then
      /usr/bin/numlockx on
fi
```


Very similar to "my" way for Gnome.  Maybe think about adding it to the wiki.

---

### Post by dodle on 2008-08-25
Thanks Rubinboy, I didn't know that I could do that.  I've never contributed to a Wiki before.

---

### Post by drubin on 2008-08-26
> **dodle said:**
> Thanks Rubinboy, I didn't know that I could do that.  I've never contributed to a Wiki before.

Ye it is pretty easy once you get the hang of the formatting. If you need a hand  just post a thread every one will be glad to help you.

---

