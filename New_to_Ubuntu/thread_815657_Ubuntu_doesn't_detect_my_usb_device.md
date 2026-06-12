---
title: "Ubuntu doesn't detect my usb device"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by slymi2005 on 2008-06-01
I think this began after upgrading to ubuntu 8.04, before I was able to plug in my sony walkman nwz s615f mp3 player and simply drag and drop files but now it won't even detect it. There is a kde application that's called usb devices that lists it when I plug the walkman in but it doesn't allow me to do anything with it. Is kde better for usb detection than gnome? I am able to mount and edit photos from a camera so the usb detection isn't completely nonexistent. Any help would be greatly appreciated.

---

### Post by tamoneya on 2008-06-01
post the results of the two following commands in terminal:```
lsusb
sudo fdisk -l
```The usb detection is not done in KDE and gnome so it should be very much the same between ubuntu and kubuntu.  Sometimes it helps to just unplug it and plug it back in again.

---

### Post by slymi2005 on 2008-06-01
```
~$ lsusb
Bus 001 Device 007: ID 054c:0327 Sony Corp. 
Bus 001 Device 001: ID 0000:0000  

```

```
Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001da31

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        2434     9783585   83  Linux
Note: sector size is 2048 (not 512)

Disk /dev/sdb: 1841 MB, 1841299456 bytes
1 heads, 62 sectors/track, 14501 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.
Note: sector size is 2048 (not 512)

Disk /dev/sdb1: 2199.0 GB, 2199023253504 bytes
1 heads, 62 sectors/track, 17318416 cylinders
Units = cylinders of 62 * 2048 = 126976 bytes
Disk identifier: 0x00000000

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1               1    69273667  4294967294   ff  BBT
Partition 1 does not end on cylinder boundary.

```

I assure you I've tried unplugging and replugging multiple times.

---

### Post by tamoneya on 2008-06-01
its probably because it doesnt recognize the BBT partition.  I have never seen a BBT partition and have no idea how to get that working.  Im sure its pretty simple like apt-getting one application or something but i dont know what it is.  Does any one know about BBT partitions.

---

### Post by slymi2005 on 2008-06-01
Wait so ubuntu 7.10 recognized bbt partitions but 8.04 doesn't? I have no idea what bbt partitions are so hopefully someone can help me out here.

---

### Post by SunnyRabbiera on 2008-06-01
BBT seems to be a xenix filesystem from what I am reading... very unusual.

---

### Post by tamoneya on 2008-06-01
ive also never seen this "/dev/sdb1p1" thing.  It says it is a 2+ TB partition.  What is this exactly?

---

### Post by slymi2005 on 2008-06-01
I have a livecd for ubuntu 8.04 and for kubuntu 7.10, I will try them and see if they detect the walkman. Thanks for the help and I'll check back later if you guys find anything else.

---

### Post by slymi2005 on 2008-06-01
Alright so I tried it on ubuntu 8.04 live cd but it didn't work and now I am on the kubuntu 7.10 cd and it works. It detects the walkman and I am able to see the files on it. So could this have something to do with the differences between 7.10 and 8.04 because 7.10 detected it and asked me what I wanted to do 8.04 didn't ask or detect and it was impossible to find it?

---

### Post by SunnyRabbiera on 2008-06-01
well there were kernel changes between the two...
if 7.10 worked better then go back to it till its end of life comes within the next year.
By then Ibex will be out and maybe that will do a little better, or another distor will take up the slack.
I am very tempted to go back to mandriva as mandriva 2008.1 is looking to be real good and I am addicted to its live CD.

---

### Post by slymi2005 on 2008-06-01
Ubuntu is the only linux derivative that I have tried out, what's special about mandriva? Any other distros you'd recommend over ubuntu. I only ask out of curiousity as ubuntu has been good to me, this is the only problem I am currently having with it so I am a happy user.

---

### Post by SunnyRabbiera on 2008-06-01
> **slymi2005 said:**
> Ubuntu is the only linux derivative that I have tried out, what's special about mandriva? Any other distros you'd recommend over ubuntu. I only ask out of curiousity as ubuntu has been good to me, this is the only problem I am currently having with it so I am a happy user.

well Mandriva sometimes has better hardware detection then ubuntu, plus its control center is pretty neat.
Each linux flavor has its benefits and pitfalls, I would say mandrivas biggest pitfall is its community as I never got any real help over there... Ubuntu is far more helpful in its community to be honest.
But thats the beauty of linux, its open nature, when one doesnt do the job another might.

---

### Post by slymi2005 on 2008-06-01
Well here is another interesting find. Nautilus, thunar, and dolphin failed to even detect the walkman but pcman filemanager detects it but when I click mount media it says unable to mount device. Frustrating.

---

### Post by anewguy on 2008-06-01
I don't know any specifics of your device, but I had USb devices in 7.10 that worked and then stopped when I went to 8.04.  Try to think back - when in 7.10 did anyone have you do anything in the /etc/udev/rules.d files, such as 40-permissions.rules or similar?  I ask this because the syntax has changed for USB device specifications in those files as of 8.04.  Many people thought I was crazy, but I found the problem and enlightened them.  I'm not going to go out on a limb here and say that's your problem, but it's possible.  If this sounds vaguely familiar, you may want to take a look at that post:

[http://ubuntuforums.org/showthread.php?t=784639]("http://ubuntuforums.org/showthread.php?t=784639")

I wish I could help you more, but I don't know your device.  Have you tried running any of the things that fail via sudo or as root?

:)

---

### Post by SunnyRabbiera on 2008-06-01
> **slymi2005 said:**
> Well here is another interesting find. Nautilus, thunar, and dolphin failed to even detect the walkman but pcman filemanager detects it but when I click mount media it says unable to mount device. Frustrating.

its a interesting scenario to be sure.

---

### Post by slymi2005 on 2008-06-01
I've decided to give up, you'd think something like this would work without such hassle it's 8.04 for crying out loud, stable, long term and all. I am going to download kde 3 or 4 later and see if that works better ( I recall using kde 4 and it working fine previously ).

Anewguy - the device is a sony walkman nwz-s615f, I don't recall if I ever changed anything with that file or whatever so I'm not going to mess with it, thanks for trying to help though.

---

### Post by slymi2005 on 2008-06-03
Alright so kde 4 didn't detect it either so it has got something to do with the changes from 7.10 to 8.04. Since it works with the kubuntu live cd I was wondering if anyone knew how to accesss files on my hd so that I could just transfer that way. Everytime I click on my files it just doesn't let me view the contents. Any help would be greatly appreciated.

---

### Post by ntrapped on 2009-06-23
I see the lsat post is of 2008 ... but my ubuntu is also unable to detect pen drive. 
Its working fine on my macbook though.

Also, I think I unchecked the pen drive symbol  - as far as I remember - this is happening since then. 

Pls suggest what to do ?

---

