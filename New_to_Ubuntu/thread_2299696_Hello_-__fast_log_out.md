---
title: "Hello -  fast log out"
date: 2015-10-20
forum: New to Ubuntu
---

### Post by Hakan__Venderlof on 2015-10-20
I have ubuntu 15.4.
If I leave the computer  it logs out very fast.
Where are settings to make it stay on desktop longer?

---

### Post by howefield on 2015-10-20
Try System Settings > Brightness & Lock > Turn Screen off After..... ?

---

### Post by Hakan__Venderlof on 2015-10-20
[COLOR=#000000]Try System Settings > Brightness & Lock

HM on system setting i can only see Backup....

[/COLOR]

---

### Post by howefield on 2015-10-20
> **Hakan__Venderlof said:**
> HM on system setting i can only see Backup....

Not sure what you mean by "HM"

---

### Post by Hakan__Venderlof on 2015-10-20
Hm is an expression meaning  -
this is confusing me.


Anyway  the only choice i see on system setting
is backup.....

---

### Post by howefield on 2015-10-20
> **Hakan__Venderlof said:**
> Hm is an expression meaning  - this is confusing me.

I understand, I usually see it written "Hmm". Irrelevant in any case.

> Anyway  the only choice i see on system setting is backup.....

So, can you open the Dash by pressing the Super + A keys and type Lock ?

---

### Post by deadflowr on 2015-10-20
Sounds like you need to try to install/reinstall unity-control-center.
Either try to remove it and re-install from the software center or run
```
sudo apt-get install --reinstall unity-control-center
```

---

### Post by Hakan__Venderlof on 2015-10-20
Super + A  means?

---

### Post by deadflowr on 2015-10-20
> **Hakan__Venderlof said:**
> Super + A  means?

Open the dash directly in the applications section.

Pressing and holding down the super key should make a special window show on the desktop with all the default unity key shortcuts, fwiw.

Super key = the key that has the Windows icon (usually) on it. 
Normally between the ctrl and alt keys.

---

### Post by Geoffrey_Arndt on 2015-10-20
Methinks Hakan is not running Unity desktop.

Hakan, are you on the KDE desktop?

---

### Post by deadflowr on 2015-10-20
No reason to suspect otherwise, until the Op gives us a reason that it's not Ubuntu.
From [Posting Guidelines]("http://ubuntuforums.org/showthread.php?t=2158945"):
> [COLOR=#000000]Always assume the the user has a default installation unless you are told otherwise[/COLOR]

---

### Post by Geoffrey_Arndt on 2015-10-20
Imho . . it's a reasonable question, considering this post in last 24 hours:

[http://ubuntuforums.org/showthread.php?t=2299547](http://ubuntuforums.org/showthread.php?t=2299547)

So, that and the lack of the standard view in "System Settings"  . . . ??

---

### Post by Hakan__Venderlof on 2015-10-21
No i am on Gnome but  i would like to change to KDE....
i think i will do a new install with only KDE....


tx for all answers...

---

### Post by Hakan__Venderlof on 2015-10-21
No I am on GNOME but i would like to
get KDE.

I guess i will make a new install with only  KDE...

Tx for all answers...

---

### Post by Geoffrey_Arndt on 2015-10-21
Hakan,  if you want KDE you should simply install a distro that is designed for KDE.   Such as Kubuntu or OpenSuse.     Much simpler, and much more reliable.

---

### Post by deadflowr on 2015-10-21
If you want to install kde, then perhaps continue with you other thread on the best way to do so, instead of this one.
You left everyone who posted in that thread hanging...

Also here is a quick one-timer one liner that will turn off the screensaver and power management settings so you won't get lock screen every 5 or 10 minutes
in a terminal try
```
xset dpms 0 s off
```
This will set it so the screensaver and power manager never kick unless you want them to.
you can also try it with
```
xset dpms 0 s 0 0
```
the two zeros at the end will set the screensaver to not only disable but also turn off the lock screen settings.
So if it ever powers down, you won't need to unlock the system.

Basic information on these setting can be found within your system from a manual page.
To view the man page open a terminal and run
```
man xset
```
press q to quit.

Hope it helps, and good luck with kde

---

### Post by Hakan__Venderlof on 2015-10-22
No i have  gnome.
KDE is what i want to install.

---

### Post by deadflowr on 2015-10-22
> **Hakan__Venderlof said:**
> No i have  gnome.
KDE is what i want to install.

We know that.
I stated you should post about how to install kde in your other thread, 
[http://ubuntuforums.org/showthread.php?t=2299547](http://ubuntuforums.org/showthread.php?t=2299547)
Other users have taken their time to respond to that thread.
Don't simply leave them hanging...

---

