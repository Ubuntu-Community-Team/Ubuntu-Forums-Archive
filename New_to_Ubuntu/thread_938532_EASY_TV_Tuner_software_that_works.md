---
title: "*EASY* TV Tuner software that works?"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Snipersnest on 2008-10-05
Is there an easy TV tuner software out there?   I mean come on.. MythTV might end up nice - but I've been trying to get it going for 2 hours and honestly I'm shot.

Is there anything in the repo out there I can grab and get my Hauppauge HVR-950 going? I was trying to get things working out of the box.. But MythTV clearly isn't an out-of-the-box install.

I'm using 8.10 Ubuntu beta 64bit. Its running smooth no issues. Thanks for your help!

---

### Post by keplerspeed on 2008-10-05
I have a Pinnacle USB tv tuner, using the em28xx driver. This is how I got it going: [http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices](http://www.2nrds.com/digital-tv-in-linux-with-em28xx-devices)
Do you have a driver for the tuner installed?
I try to avoid kde apps, but I cant beat kaffeine as a tv viewer.

Just looking at the website above, your tv tuner is supported. Just follow the tutorial to install the firmware and v4l (video for linux) module, and using kaffeine you should be on your way. Also, MythTV will work fine once you have the driver installed.

---

### Post by Brandel Valico on 2008-10-05
I use TVtime and Xawtv myself. TVtime for watching most things and Xaw for converting VHS to DVD or recording shows.

---

### Post by wolfen69 on 2008-10-05
just google for "V4L install" (the drivers you need) then you can use any tv viewer.

---

### Post by Saiph on 2008-10-05
I have Technisat skystar 1ci and drivers are in core of UBUNTU 8.04. But you must replace 1 byte in eeprom, what I wrote here [http://ubuntuforums.org/showthread.php?t=820505.:](http://ubuntuforums.org/showthread.php?t=820505.:))

---

### Post by Snipersnest on 2008-10-05
I guess something is wrong.. even after following the easy direction on the first post when I goto "make" the driver it fails out. I'm just gonna past where it fails.. not the whole thing.

```

c:41:
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h:365: error: field 'class_dev' has incomplete type
In file included from /home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-common.h:29,
                 from /home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttvp.h:37,
                 from /home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:41:
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h:394: warning: 'struct class_device_attribute' declared inside parameter list
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h:394: warning: its scope is only this definition or declaration, which is probably not what you want
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h: In function 'video_device_create_file':
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h:396: error: implicit declaration of function 'class_device_create_file'
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h: At top level:
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h:403: warning: 'struct class_device_attribute' declared inside parameter list
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h: In function 'video_device_remove_file':
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/../linux/include/media/v4l2-dev.h:405: error: implicit declaration of function 'class_device_remove_file'
In file included from /home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:41:
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttvp.h:94:1: warning: "clamp" redefined
In file included from include/linux/cache.h:4,
                 from include/asm/pda.h:7,
                 from include/asm/current.h:19,
                 from include/asm/processor.h:15,
                 from include/linux/prefetch.h:14,
                 from include/linux/list.h:6,
                 from include/linux/module.h:9,
                 from /home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:32:
include/linux/kernel.h:376:1: warning: this is the location of the previous definition
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c: In function 'show_card':
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:172: warning: type defaults to 'int' in declaration of '__mptr'
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:172: warning: initialization from incompatible pointer type
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c: At top level:
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:176: error: expected ')' before '(' token
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c: In function 'bttv_register_video':
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:4637: error: 'class_device_attr_card' undeclared (first use in this function)
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:4637: error: (Each undeclared identifier is reported only once
/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.c:4637: error: for each function it appears in.)
make[3]: *** [/home/nate/firmware/driver/v4l-dvb-kernel/v4l/bttv-driver.o] Error 1
make[2]: *** [_module_/home/nate/firmware/driver/v4l-dvb-kernel/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.27-4-generic'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/nate/firmware/driver/v4l-dvb-kernel/v4l'
make: *** [all] Error 2

```

any ideas?

---

### Post by Snipersnest on 2008-10-05
bump...  sorry I'm getting bored.. my tv is broken and my tv tuner doesn't work.. google doesn't help me much either :(

---

### Post by fenian on 2008-10-05
First remove the default V4L drivers,in a terminal enter...

>  sudo mv /lib/modules/`uname -r`/kernel/drivers/media /root/`uname -r`-kernel-drivers-media-backup

(This doesnt really remove them but moves them to a different location)

Next Install mplayer if you don't have it...

> sudo apt-get install mplayer

Next Install the firmware,in a terminal enter these lines (seperately)...

> cd /tmp
 wget [http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip](http://www.steventoth.net/linux/xc5000/HVR-12x0-14x0-17x0_1_25_25271_WHQL.zip)
 wget [http://www.steventoth.net/linux/xc5000/extract.sh](http://www.steventoth.net/linux/xc5000/extract.sh)
 sh extract.sh
 sudo cp dvb-fe-xc5000-1.1.fw /lib/firmware/`uname -r`


NextInstall newer V4L drivers,in a terminal enter these lines (seperately)
...

 > wget [http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2](http://linuxtv.org/hg/v4l-dvb/archive/tip.tar.bz2)
 tar jxf tip.tar.bz2
 cd v4l-dvb-49ea64868f0c/
 make all
 sudo make install

Reboot

Open a terminal and enter...
> 
dmesg | less

you should see something like this...
>  [   35.391481] tveeprom 2-0050: Hauppauge model 72001, rev B2F0, serial# NNNNNNN
 [   35.391485] tveeprom 2-0050: MAC address is NN-NN-NN-NN-NN-NN
 [   35.391487] tveeprom 2-0050: tuner model is Xceive XC5000 (idx 150, type 4)
 [   35.391490] tveeprom 2-0050: TV standards NTSC(M) ATSC/DVB Digital (eeprom 0x88)
 [   35.391492] tveeprom 2-0050: audio processor is AU8522 (idx 44)
 [   35.391494] tveeprom 2-0050: decoder processor is AU8522 (idx 42)


Scan for chanels in the terminal enter...

>  sudo apt-get install dvb-utils
 scan -U /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf.atsc

Watch TV with mplayer ,in the terminal enter...
> 
 mplayer dvb://

(change channels with h and k change volume with 0 and 9)

Mythtv should also detect the card now.

---

### Post by Snipersnest on 2008-10-05
Well I followed all your instructions.. made 2 two steps from the end.. while scanning for channels I get an error.
```

>>> tune to: 57028615:8VSB
WARNING: >>> tuning failed!!!
>>> tune to: 57028615:8VSB (tuning failed)

```It kept going so i stopped it.. Does ATSC mean its going to tune to over the air HD channels or does that scan for cable channels also?   Not sure whats wrong any ideas?

---

### Post by fenian on 2008-10-06
It would scan for over the air atsc HD channels.If you were using an external cabble box I think you would have to set the HVR-950 to channel 3.

---

### Post by LowSky on 2008-10-06
Try using a version of Ubuntu that is supported by the community and Ubutnu and maybe...just maybe... things will work

[http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by Snipersnest on 2008-10-06
Is there anyway to just tell it to scan my cable?  I don't have digital cable, so I don't have a set-top box.. I don't live in a place where people steal much cable either so they don't require set-top boxes for regular cable.

I guess that error is because of the HD scan not a driver issue?

I my reason I used Ubuntu 8.10 is because it is the supported version in the next 3 weeks.. I didn't want to waste the time with an upgrade later.

---

### Post by Snipersnest on 2008-10-06
bump..  Anyone able to help me figure out where the problem is on my tuner?  I simply want to watch regular cable with no set top box. I'm so lost looking at half these threads about this card because theres like 3 different ways to install it.  

I followed the directions in this thread but I can't seem to get things going.   Is there anyway to simply double check my self to see if the tuner is installed?  Once I check that how do I check the software to see if its talking with the tuner? Thanks for the help everyone.

---

### Post by Zzl1xndd on 2008-10-07
Did some digging, looks like the card should be supported out of the box. Have you tried TVtime, it worked with my Hauppauge-150.

---

### Post by Snipersnest on 2008-10-07
> **tweakedenigma said:**
> Did some digging, looks like the card should be supported out of the box. Have you tried TVtime, it worked with my Hauppauge-150.

Well I tried TVtime - but it just tells me No Signal on screen.. It will scan for channels and allow me to change settings between HRC, NTSC and all that stuff.. But still just a big blue screen :(

I have a feeling I broke the drivers or something after doing that install in this thread. Is there some way to revert back to the old stuff?

---

### Post by Snipersnest on 2008-10-09
bump ... can anyone tell me how to uninstall and start over on my drivers?  Maybe theres some easy way to just use the regular embeded kernel one since that seems to work with TVTime.

Thanks a bunch!

---

### Post by Brandel Valico on 2008-12-11
It sounds like you have TVtime set to the wrong video device

try typing in tvtime-configure -d /dev/video0
in a terminal before starting TV-time. Then try the same command with video1 or video2 for examples I have to set mine to video1 as 0 is my webcam to get TVtime to show tv.

I tend to do this by editing the launcher in my menu to include the /dev/video1 at the end.

---

### Post by phreon on 2008-12-12
Man, I feel your pain. I have tried every manner of tv player in Ubuntu 8.04 and nothing works. Ubuntu sees my card but I can't get tv. I think I have messed up many config files and maybe deleted some important files removing and reinstalling Mythtv, tvtime, etc.

Is there any way to get back to a fresh Ubuntu without a complete reinstall of Ubuntu?

(TV in Linix is just too tough.)

Thanks
P

---

### Post by Drakkor on 2008-12-12
> Well I tried TVtime - but it just tells me No Signal on screen..
Have you tried hitting the up or down arrows on your keyboard to select 
different channels ? :p

---

### Post by adrian.todireanu on 2008-12-25
Intrepid, Leadtek Winfast TV 2000 XP
ex: crash of kmplayer when trying to select (just hovering over the menu entry) TV
> 
administrator@ubuntu:~$ kmplayer
kbuildsycoca running...
KCrash: Application 'kmplayer' crashing...
Could not find 'drkonqi' executable.
KCrash cannot reach kdeinit, launching directly.
administrator@ubuntu:~$ X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x3c0017f


No other TV application works either. I followed countless threads and HowTo-s and I'm not sure that I shouldn't reinstall Ubuntu entirely after so much tinkering.
I'd really love to make this work, since I'm quite bored of rebooting in XP to watch TV.

**[COLOR="Lime"]First sign of life ever, from my tvtuner!!![/COLOR]**

I followed this [post]("http://ubuntuforums.org/showthread.php?t=647129&highlight=bttv") and now, **[COLOR="Blue"]tvtime[/COLOR]**, finally found channels. The only strange thing is that I have to start it with **[COLOR="Magenta"]sudo[/COLOR]** in terminal, otherwise complains about not being able to use [COLOR="Lime"]/dev/video0[/COLOR], but this could be a consequence of all the messing around I previously did, trying to get things started. 
> 
Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/administrator/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/administrator/.tvtime/tvtime.xml: Permission denied.
videoinput: Cannot open capture device /dev/video0: Permission denied
I/O error : Permission denied

So, go there and see if it works for you too.

---

### Post by Drakkor on 2008-12-25
Lol, I have the opposite problem, I have to boot to Ubuntu/tvtime
to watch TV, cause Vista is not compatible with my old tv tuner card! :)

---

### Post by wolfen69 on 2008-12-25
i think you should recompile your v4l drivers.
```
sudo apt-get install module-assistant
```
then
```
sudo m-a a-i v4l
```

let it do its thing.

reboot.

install xawtv and give that a try. or try the other tv programs again. did you try tvtime? don't forget vlc either.

if none of that works, see if you can find a used Hauppauge PVR150/250 or 350. they work out of the box with ubuntu.(you just need to install *ivtv-utils*. it's a good investment if you really want to get serious with linux. i couldn't live without tv on my computer.

let us know what happens.

---

### Post by cb951303 on 2008-12-25
your usb tv tuner is supported by linux and the drivers are integrated into kernel since 2.6.26 so if you're on 8.10 you don't have to worry about drivers. But you need a firmware to make it work. 

this is the official hauppauge 950 wiki from linux dvb drivers page: [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950#Making_it_Work](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950#Making_it_Work)

---

### Post by wolfen69 on 2008-12-25
> **adrian.todireanu said:**
> Intrepid, Leadtek Winfast TV 2000 XP
ex: crash of kmplayer when trying to select (just hovering over the menu entry) TV


No other TV application works either. I followed countless threads and HowTo-s and I'm not sure that I shouldn't reinstall Ubuntu entirely after so much tinkering.
I'd really love to make this work, since I'm quite bored of rebooting in XP to watch TV.

**[COLOR="Lime"]First sign of life ever, from my tvtuner!!![/COLOR]**

I followed this [post]("http://ubuntuforums.org/showthread.php?t=647129&highlight=bttv") and now, **[COLOR="Blue"]tvtime[/COLOR]**, finally found channels. The only strange thing is that I have to start it with **[COLOR="Magenta"]sudo[/COLOR]** in terminal, otherwise complains about not being able to use [COLOR="Lime"]/dev/video0[/COLOR], but this could be a consequence of all the messing around I previously did, trying to get things started. 

So, go there and see if it works for you too.

just saw your updated post. glad you got it going.

---

