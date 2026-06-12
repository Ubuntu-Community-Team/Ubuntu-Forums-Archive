---
title: "Reinstall Android from Ubuntu Touch on Nexus 7"
date: 2014-08-31
forum: New to Ubuntu
---

### Post by taro2 on 2014-08-31
Hi guys,

I hope that somebody can help me.

I've tried Ubuntu Touch, but cannot get along with it. I was hoping that it would be more like the regular edition. For mobiles it might be good, but for my Nexus 7, I feel that I can get more out of it with Android.

Anyway, I would like to reinstall Android and I'm having some trouble. I am following the following guide from OMG Ubuntu;

[http://www.omgubuntu.co.uk/2013/02/how-to-reinstall-android-on-nexus-devicescd](http://www.omgubuntu.co.uk/2013/02/how-to-reinstall-android-on-nexus-devicescd) 
> Desktop/<name of extracted folder; hit TAB to autocomplete>
sudo ./flash-all.sh

So I've downloaded the android file, and saved it to my desktop. I find the folder by typing the following in the terminal;

> cd Desktop/razor-ktu84p/

Once I have got to that location, I type;

Sudo ./flash-all.sh

> [sudo] password for user: 
sending 'bootloader' (3911 KB)...
OKAY [  0.169s]
writing 'bootloader'...
OKAY [  1.461s]
finished. total time: 1.631s
rebooting into bootloader...
OKAY [  0.006s]
finished. total time: 0.006s
[B]archive does not contain 'boot.sig'
archive does not contain 'recovery.sig'
failed to allocate 754455404 bytes
error: update package missing system.img[/B]

I've tried this many time and tried different version of android.

Is there something simple that I have missed?

---

### Post by taro2 on 2014-08-31
I've tried using these commands and now I can get the android logo (four colours) to show, but the android os isn't loading.

fastboot erase boot
fastboot erase cache
fastboot erase recovery
fastboot erase system
fastboot erase userdata

then;

fastboot flash boot boot.img
fastboot flash system system.img
fastboot flash recovery recovery.img
fastboot flash userdata userdata.img

If I manage to fix it myself, I will write what I did here.

---

### Post by taro2 on 2014-08-31
I can't believe it, I actually got it to work.

I did what I wrote above, but tried a different Android version. I had been running 4.4.4 so I thought that it would be fine, but this time I tried Razor-jss15r, and it worked first time.

I hope this helps somebody else.

---

