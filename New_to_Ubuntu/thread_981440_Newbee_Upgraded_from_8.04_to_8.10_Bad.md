---
title: "Newbee: Upgraded from 8.04 to 8.10: Bad"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by silverwolf636 on 2008-11-13
I just followed the online instructions to upgrade from 8.04 to 8.10. Everything appeared to have went fine till the reboot. When it comes to the login screen it just sits there then the screen turns bright and the mouse locks up. There is nothing on the screen just a slight color of tan then it brightens up then locks.
I am running an AMD Sempron 2800+ Processor, 1.6GHz, 1G ram, VIA/S3G UniChrome Pro IGP Video.
8.04 was running great with no problems.

Any help would be apreciated
Oh, this is a dual boot system with Windoze XP
Thnx

---

### Post by Crafty Kisses on 2008-11-13
Press the following:
```
Ctrl+Alt+F1
```
Once you've done that run this command:
```
sudo dpkg-reconfigure xserver-xorg
```
Let's see if that gets you up and running.

---

### Post by silverwolf636 on 2008-11-13
Still doing the same thing.

---

### Post by jerrylamos on 2008-11-13
I had 2 pc's do fine with 8.10.  On an IBM laptop with Intel video 8.10 was a bear until I removed compiz.  That's the software package that does "eye candy" fades & splashes & animation and has nothing to do with function.  There were major changes in compiz and X windows on 8.10.

I don't have your hardware configuration.  Here's a couple things to try:

Select rescue mode which is the second line on the boot screen.

Select root shell prompt
sudo apt-get remove compiz compiz-core
exit
resume normal boot

compiz can be installed later if you're able to boot up.

If that doesn't work, then boot in rescue mode again
select xfix
resume normal boot

By the way, you're by no means alone, not that that is any help.

Jerry

---

### Post by silverwolf636 on 2008-11-14
Crap,  still didn't work. Same stuff...

---

### Post by Snappo on 2008-11-17
I have the same video card and I'm fighting to keep this session online enough to post this reply, I will keep checking this thread to see if there is any updates. :(

---

### Post by silverwolf636 on 2008-11-18
There must not be a fix for it.  Look at the dates of my last response. There aren't too many suggestions.  I've since repartitioned one of hd's and install 8.04 back on until I can get this resolved...

---

