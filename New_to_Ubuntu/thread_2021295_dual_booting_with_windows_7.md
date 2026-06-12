---
title: "dual booting with windows 7"
date: 2012-07-09
forum: New to Ubuntu
---

### Post by jboyskate on 2012-07-09
hi i was wondering how to dual boot windows 7 and ubuntu with using the wubi software?

---

### Post by jboyskate on 2012-07-09
i mean with out using the wubi software

---

### Post by c2tarun on 2012-07-09
> **jboyskate said:**
> hi i was wondering how to dual boot windows 7 and ubuntu with using the wubi software?
 
Download the ISO burn it to a CD and try installing it from inside of windows like a normal software. It will not take more than 15 mins.
 
You can download ISO from [http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by c2tarun on 2012-07-09
> **jboyskate said:**
> i mean with out using the wubi software
 
You can simply boot from CD and install it. It is also very easy. If this is your first time with linux try going through Wubi first.

---

### Post by jboyskate on 2012-07-09
i already tried wubi, now i really want to dual boot with out using the software

---

### Post by c2tarun on 2012-07-09
> **jboyskate said:**
> i already tried wubi, now i really want to dual boot with out using the software
 
Try this tutorial: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) this might be an old one but you'll get a fair idea of what you are trying to do.

---

### Post by Ubun2to on 2012-07-09
Well,  you're in luck. I figured out how to do it.
However, you need to make a backup before you do this. Playing around with stuff like this always leaves the possibility of total failure.
First, burn the ISO onto a CD. Then, boot into it, and select "Try Ubuntu." I'm assuming you already have a new partition created for Ubuntu, formated with the ext3 or ext4 filesystem.
Type the following command:
```
sudo mount /dev/sda2 /mnt
```
Replace /dev/sda2 with your Windows partition. You can find your Windows partition by going into GParted. It usually has the manufacturer's name, like HP, ASUS, DELL, and sometimes it can be WINDOWS, unless you renamed the partition. But, don't go by the name-go by the /dev/sda# or /dev/sdb# thing that is next to the name.
I'm also assuming you have picked up the Wubi move file from [here]("https://help.ubuntu.com/community/MigrateWubi?action=AttachFile&do=view&target=wubi-move-2.2.tar.gz"). If not, download it, extract it to your Downloads folder, and do this:
```
cd /home/ubuntu/Downloads/wubi-move-2.2/
```
Mount your hard drive into the /mnt folder, and type the following command:
```
sudo bash wubi-move-2.2.sh --root-disk=/mnt/ubuntu/disks/root.disk /dev/sda3 /dev/sda4
```
Now, make the following changes to the command:
1. Replace /dev/sda3 with the partition you want to move Ubuntu to. If you're not sure what partition you want, look at your partition tables on GParted.
2. Replace /dev/sda4 with the swap partition. If you have none and don't want one, remove /dev/sda4 from the command.
3. Replace /mnt/ubuntu/disks/root.disk with the location of the root.disk file. I'm not sure if your location is the same as mine. But, if you didn't mess around with the settings of Wubi when you installed, it should be the same. However, you should double check this by going to /mnt/ubuntu/disks/ and seeing if there is a root.disk file in that folder. If not, you might need to look around for it.
Once you have finalized the command, press enter. This will begin the move. It may ask you some questions along the way, so come back and check on it every half hour or so. Make sure you have everything but Terminal (and maybe Firefox) closed as a precaution.
I hope this helps. If you have any questions, feel free to ask them. Not asking questions when dealing with things like this is dangerous for your computer (and you, if you could lose lots of valuable data).

---

### Post by c2tarun on 2012-07-09
> **Ubun2to said:**
> Well, you're in luck. I figured out how to do it.
However, you need to make a backup before you do this. Playing around with stuff like this always leaves the possibility of total failure.
First, burn the ISO onto a CD. Then, boot into it, and select "Try Ubuntu." I'm assuming you already have a new partition created for Ubuntu, formated with the ext3 or ext4 filesystem.
Type the following command:
```
sudo mount /dev/sda2 /mnt
```
Replace /dev/sda2 with your Windows partition. You can find your Windows partition by going into GParted. It usually has the manufacturer's name, like HP, ASUS, DELL, and sometimes it can be WINDOWS, unless you renamed the partition. But, don't go by the name-go by the /dev/sda# or /dev/sdb# thing that is next to the name.
I'm also assuming you have picked up the Wubi move file from [here]("https://help.ubuntu.com/community/MigrateWubi?action=AttachFile&do=view&target=wubi-move-2.2.tar.gz"). If not, download it, extract it to your Downloads folder, and do this:
```
cd /home/ubuntu/Downloads/wubi-move-2.2/
```
Mount your hard drive into the /mnt folder, and type the following command:
```
sudo bash wubi-move-2.2.sh --root-disk=/mnt/ubuntu/disks/root.disk /dev/sda3 /dev/sda4
```
Now, make the following changes to the command:
1. Replace /dev/sda3 with the partition you want to move Ubuntu to. If you're not sure what partition you want, look at your partition tables on GParted.
2. Replace /dev/sda4 with the swap partition. If you have none and don't want one, remove /dev/sda4 from the command.
3. Replace /mnt/ubuntu/disks/root.disk with the location of the root.disk file. I'm not sure if your location is the same as mine. But, if you didn't mess around with the settings of Wubi when you installed, it should be the same. However, you should double check this by going to /mnt/ubuntu/disks/ and seeing if there is a root.disk file in that folder. If not, you might need to look around for it.
Once you have finalized the command, press enter. This will begin the move. It may ask you some questions along the way, so come back and check on it every half hour or so. Make sure you have everything but Terminal (and maybe Firefox) closed as a precaution.
I hope this helps. If you have any questions, feel free to ask them. Not asking questions when dealing with things like this is dangerous for your computer (and you, if you could lose lots of valuable data).
 
 
By god... :( I installed Ubuntu a million times (figuratively) in many different ways (separate home, separate boot etc) but I couldn't figure out what you are trying to do.
BTW :) I totally agree with your comment ;)
>  Playing around with stuff **like this** always leaves the possibility of total failure.

---

### Post by oldfred on 2012-07-09
HOWTO: migrate wubi install to partition - bcbc 
[https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi)
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

You can also just install and copy /home over if that is all you want.

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Ubun2to on 2012-07-09
> **c2tarun said:**
> By god... :( I installed Ubuntu a million times (figuratively) in many different ways (separate home, separate boot etc) but I couldn't figure out what you are trying to do.
BTW :) I totally agree with your comment ;)

Well, I took the command from [https://help.ubuntu.com/community/MigrateWubi](https://help.ubuntu.com/community/MigrateWubi) for live CDs and USBs and modified it so /dev/sda3 is the target partition, and /dev/sda4 is the swap space.
--root-disk=/mnt/ubuntu/disks/root.disk is the location of the Wubi drive where I mounted Windows, where the Wubi drive resides.
sudo bash wubi-move-2.2.sh is the command terminal executes.
cd /home/ubuntu/Downloads/wubi-move-2.2/ changes the directory to the location in which the Wubi move script lives.
sudo mount /dev/sda2 /mnt mounts my Windows (/dev/sda2) partition in the /mnt folder (more convenient than mounting it in /media, if you ask me-with /media, it is /media/WINDOWS/folderhere, whereas /mnt is /mnt/folderhere-less to type).

---

### Post by sudo smith on 2012-07-11
> **jboyskate said:**
> hi i was wondering how to dual boot windows 7 and ubuntu with using the wubi software?

Well what I did is just get an external hdd and installed Ubuntu on that. This way you dont have to risk messing up your Windows and you can run Ubuntu on any PC that is capable of booting off usb. (I like being able to carry Ubuntu in my pocket everywhere I go :) )

---

