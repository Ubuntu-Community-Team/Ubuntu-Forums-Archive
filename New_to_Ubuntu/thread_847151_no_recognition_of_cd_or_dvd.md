---
title: "no recognition of cd or dvd"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by lyni on 2008-07-02
I have ubuntu 8.04 and I have tried to play a cd and a dvd but the computer is just not recognising them. nothing comes up on the screen when I insert the cd or dvd and when I go to a media player it doesn't detect them either. I tried several media players with no response. 
lyn

---

### Post by scragar on 2008-07-02
hmn, first thing to check would be to see if it's mounted,so run:
```
mount | grep cdrom
```
if you got 1 or more lines then your media is mounted, but for some reason they arn't being played, try opening the folder with the filemanager to check them:```
nautilus /media/cdrom
```

if you didn't get any lines then for some reason they are not mounting, so the next thing to check is if the media is detected, run:```
cat /proc/partitions
```and look for either cd or dvd as required.
If it's listed then the media is being detected,just not mounted,check the preferences for "removable drives and media" for options to automount etc.

if it's still not detected,open and close the tray,wait 5 seconds or so, then run:```
dmesg | tail
```and post back here.

---

### Post by lyni on 2008-07-02
hi Scragar thanks for your reply. I tried the first suggestion and it just said 'name desktop'.
for your second suggestion which folder would have the file manager?  in the File System folder there is a folder named CD but it is empty.
lyn

---

### Post by scragar on 2008-07-02
if the folder is empty then the DVD/CD isn't mounted, check if it's detected, if you choose to enable automount in the options you may need to open/close the disk tray again for it to mount.

---

### Post by drs305 on 2008-07-02
> **scragar said:**
> 
```
mount | grep cdrom
```
if you got 1 or more lines then your media is mounted

On my machine, with a cd mounted that command doesn't return anything because mount shows:
```

/dev/scd0 on /media/Ubuntu 8.04 i386 type iso9660 (ro,nosuid,nodev,uhelper=hal,uid=1000,utf8)

```


You can check your fstab to see if there is an automount reference:
```
cat /etc/fstab
```

Mine looks like this:
```

/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

```

---

### Post by lyni on 2008-07-02
I just tried your second suggestion and this is what I got -
Initializing nautilus-share extension
seahorse nautilus module initialized

** (nautilus:9779): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown
 

I don't know what that means but it doesn't look too hopeful.
lyn

---

### Post by bobpur on 2008-07-02
"I tried several media players with no response."

I'm not so much into the programming as I am the hardware. I can't type worth nothing:)
So, with the above statement, I'm wondering if you placed the jumpers correctly on these drives when you installed them? This is for PATA or IDE drives not SATA drives.
If your optical drives have a wide, flat ribbon cable plugged into the back,along with a four pin molex connector for power, this info is for you.
First of all, at the end is the master connection. On your optical drive,where the other connections are, you will find 6 or 8 pins in a group with a small jumper. This jumper should be in the "MA" position for this connection. Usually, the topmost optical drive in the case.
Towards the center of the cable is the slave connection. This optical drive should have the jumper in the "SL" position. Usually, mounted just under the master in the case.
Just one optical drive? Set as master ("MA") and connect at the end of the cable.
Have you replaced the cable lately?
This is pretty basic, but if all your connections are correct you shouldn't have any problems getting your drives recognized.

Good Luck.

---

### Post by tipiglen on 2008-07-04
Bob,

Try this 

[http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount](http://ubuntuforums.org/showthread.php?t=847645&highlight=cdrom+mount)

Hope it helps
ed

---

