---
title: "System getting hanged at bootup showing a smiley instead of grub"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by pra14gpk on 2008-04-24
Hai!

I used to have grub with two options windows and linux(fc3) boot.
I formated windows partition and installed windows again. The old grub is gone and only windows boot is possible.
I know that this is very normal.
Now I tried to install grub to recover grub screen, so that I can boot in to my linux partion also. 
I boot using ubuntu CD. I have no seperate boot partition. My linux partition was in /dev/sda9 and /dev/sda10 was my swap partition. 
then I did,

1.sudo grub

2.find /boot/grub/stage1    -> this was just for confirmation

o/p was (hd0,8)  -> as expected.

3. root (hd0, 8)
4. setup (hd0)
o/p was normal lines of text showing grub installation.
5. quit

My grub.conf was also very simple,

default=0
timeout=10
splashimage=(hd0,8)/boot/grub/splash.xpm.gz
title Fedora Core 
      root (hd0,8)
      kernel /boot/vmlinuz  -> and some parameters i did not remember exactly but they were like normal grub entries.
      initrd /boot/initrd.img 
title Dos
      rootnoverify (hd0,0)
      chainloader +1

I checked the existense of each entry is at their respective loaction.

Now I rebooted my system. 
Then instead of grub screen, I am getting a blank screen with a smiley kind of icon at right bottom corner of my screen.

Nothing goes forward. Neither I can boot into linux nor windows. Only boot from CD working.

I did this kind of grub installation (when windows removes grub) earlier also (not on my system). But this time it is really making me crazy.

Please somebody help me in sorting out this problem. or Please tell what could be causing this problem.

---

### Post by milosz.galazka on 2008-04-25
[Here]("http://ubuntuforums.org/showthread.php?t=354978") is a link to [supergrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html"). Maybe it will help...

---

