---
title: "pure lubuntu and speed"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by lrisan on 2012-04-02
Hi all!

I have installed lubuntu on my 8 years old ThinkPad, and the speed is just fabulous. The computer was getting too slow with KDE 4.* and Unity never worked. Now it wakes up from sleep before I have opened the lid fully, like a new Mac. Great! It has never been that fast.

However, I miss some programs of KDE or Gnome, and I have enough disk space. But then, if I install a KDE-application, I also need a bunch of libraries. Will that slow down the entire computer, say on wake-up-from-sleep, or will it just affect the KDE-application in question?

Anyone got any experience with combining lubuntu and KDE or Gnome?  

-Lars

---

### Post by santosh83 on 2012-04-02
> **lrisan said:**
> Hi all!

I have installed lubuntu on my 8 years old ThinkPad, and the speed is just fabulous. The computer was getting too slow with KDE 4.* and Unity never worked. Now it wakes up from sleep before I have opened the lid fully, like a new Mac. Great! It has never been that fast.

However, I miss some programs of KDE or Gnome, and I have enough disk space. But then, if I install a KDE-application, I also need a bunch of libraries. Will that slow down the entire computer, say on wake-up-from-sleep, or will it just affect the KDE-application in question?

Anyone got any experience with combining lubuntu and KDE or Gnome?  

-Lars

If you start any KDE or GNOME application from a pure Lubuntu environment, then it's sure to load a bunch of KDE (Qt etc.) and GNOME specific libraries, which will certainly use up more RAM, and may also slow down your system in a minuscule way. The bigger culprits would be KDE and GNOME **services**, things like akonadi or gvfs or gnome-settings-daemon and so on, which will take up even more RAM.

My experience has been that KDE is a little-bit more heavy-weight than GNOME, but I still have GNOME 2.x here. GNOME 3 may be equally as big as KDE these days. Akonadi and nepomuk do seem to consume a lot of RAM, but hopefully the latter shouldn't be started simply for running KDE applications under LXDE!

If your system is low on processing power and especially RAM, try to find LXDE or Xlib based alternatives for your KDE/GNOME apps as much as possible.

---

### Post by Rodney9 on 2012-04-02
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by mastablasta on 2012-04-02
> **lrisan said:**
> However, I miss some programs of KDE or Gnome, and I have enough disk space. But then, if I install a KDE-application, I also need a bunch of libraries. Will that slow down the entire computer, say on wake-up-from-sleep, or will it just affect the KDE-application in question?
 
 
Applications are the one that will be using them. 
 
have you tried KDE with low-fat package to reduce the amount of spent ram?
 
Also (but maybe more as a test) have you eve tried RazorQT? it's kind of like KDE uses same libraries only very light. Ubuntu Razor Remix (U-R-R) can be found on the net. I gave it a try live session in virtualbox and on start up it used about 135-140 MB RAM. not bad huh? and has the usual KDE apps.

---

