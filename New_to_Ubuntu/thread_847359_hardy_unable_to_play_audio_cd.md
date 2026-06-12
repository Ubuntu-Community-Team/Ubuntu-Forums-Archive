---
title: "hardy unable to play audio cd"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by hp3 on 2008-07-02
hardy 32 bit, and audio works, when I insert an audio cd, it is mounted but the media player tells me that stream is empty.  grip, can not open /dev/cdrom, so I am unable to listen to audio cds.

I have not changed any config file by hand, and not tampered with anything.

This worked fine under 7.10.
Plase help.

hp3@pc-unx1:~$ ls -l /media
totalt 16
lrwxrwxrwx  1 root root    6 2007-10-27 19:06 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2007-10-27 19:06 cdrom0
drwxr-xr-x  2 root root 4096 2007-10-27 19:06 cdrom1
drwxrwxrwx 11 hp3  hp3  4096 2008-07-01 14:15 disk
drwxrwxrwx 45 root root 4096 2008-06-02 22:22 disk-1
hp3@pc-unx1:~$

---

### Post by Eisenwinter on 2008-07-02
Try using /media/cdrom0, or /media/cdrom instead.

---

### Post by hp3 on 2008-07-02
The error message in grip are gone but no tracks show up. and when I 
open the cd from the desktop icon, all tracks are visible but wont play.

---

### Post by nowshining on 2008-07-02
um, the screenshot utility is blocking the error message :D

also try re-installing the codecs & try seeing if there are any updates for your system and install them if necessary.

---

### Post by hp3 on 2008-07-02
I have removed and installed a new player, (DVD rom) same.
I have reinstalled (from synaptic) everything with the description codec.

What must be on the system to play a normal cd?
The error is posted below. vlc (open disc using /dev/scd1 or 0).
spins the drive, but no sound. I am confused since /media/xxx and /dev/cdrom and /dev/scdx is used and seams to refer to the same thing??

---

### Post by tjwoosta on 2008-07-02
do you have the right codecs installed?

```
sudo apt-get install ubuntu-restricted-extras
```

also i think you need the w32codecs

first enable medibuntu repository
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

then do 
```
sudo apt-get install w32codecs
``` (or w64codecs for 64bit ubuntu)

---

### Post by hp3 on 2008-07-02
ok, time for some more data:

I have two DVD players, one that can write media, and one that only plays media.  The writer plays audio cds if I use sound juicer.
Totem,vlc and grip does not play them, but grip can rip my cds now to mp3.

When I select open disk in VLC, it starts moving the slide bar, and stops. 

The DVD reader do not play audio cds, but works well with data disks. and dvd movies.  I can not understand this.

---

### Post by tipiglen on 2008-07-04
This might help, with suitable differences for having two drives

[http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount](http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount)

Hope it's of some use
ed

---

### Post by hp3 on 2008-07-05
It did not solv my problem. but I have one DVD player that works.
I have other issues with samba that pains me more. maybe I must 
move away from Ubuntu, or Linux until things works better.

---

