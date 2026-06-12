---
title: "Alert! /dev/disk/by-uuid/xxx-xxx-xx-xxx does not exist dropping to shell"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by fedenuche on 2012-07-05
Hi, I have installed ubuntu 12.04 and works great. After that I added a HD to move my backups. After move my files, i removed the HD and then when I try to boot my PC it returns me 

**Alert! /dev/disk/by-uuid/4636ea0e-8134-4a38-a1a0-1aad92597a11 does not exit dropping to shell**

After a while and before a lots of kills by signal 9 I can start my ubuntu

I tried this [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix) but it doesn't solve my problem. I think it is because I'm not trying to recognizing the device because I'm trying to remove it.

This is the result for **sudo blkid**

/dev/sda1: LABEL="Disco 1 - Sistema" UUID="DE9CC7C69CC79803" TYPE="ntfs" 
/dev/sda5: LABEL="Disco 1 - Datos" UUID="0A3C21883C216FBD" TYPE="ntfs" 
/dev/sda6: UUID="4636ea0e-8134-4a38-a1a0-1aad92597a11" TYPE="ext4" 
/dev/sda7: UUID="92d3a0b5-a60e-40f2-9c94-d0825f6117c4" TYPE="swap" 

This is the result for **sudo blkid -p /dev/sda6**

/dev/sda6: UUID="4636ea0e-8134-4a38-a1a0-1aad92597a11" VERSION="1.0" TYPE="ext4" USAGE="filesystem" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x83" PART_ENTRY_NUMBER="6" PART_ENTRY_OFFSET="57427968" PART_ENTRY_SIZE="100395008" PART_ENTRY_DISK="8:0" 

Can someone help me?

Thanks in advance.-

---

### Post by NikTh on 2012-07-05
I don't know how this happened but try this ... just to boot in your system .. 
At grub menu and when you highlight the Ubuntu entry hit 'e' key .. then go to line that says.. root=UUID=xxxxxx delete all the numbers and UUID .. and write /dev/sda6 
The line should be like this.. 
** ```
root=/dev/sda6 ro quiet splash $vt_handoff** 
```
then hit F10 to boot in your system 
If boot in to your system .... try to change accordingly the /etc/fstab.
If you have questions about /etc/fstab then post back.

---

### Post by fedenuche on 2012-07-06
NikTh thanks for you reply I'm going to do that right now, but I think that the removed disc was the dev/sda6, so if I try to boot from that disk... But I'm going to do that right now and I will write an update after that.

---

### Post by cipherboy_loc on 2012-07-06
What are the contents of /etc/fstab? Did you have the device in fstab, set to mount on boot? Also, is this your root partition you cannot mount?


Cipherboy

---

### Post by fedenuche on 2012-07-06
**NikTh:** The result of that change was the same result (a lot of kills with error: Alert! /dev/sda6 does not exist. Dropping to shell).

**cipherboy_loc:** I don't know how to see if it are set to mount on boot, but this is the result of sudo gedit /etc/fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=4636ea0e-8134-4a38-a1a0-1aad92597a11 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=92d3a0b5-a60e-40f2-9c94-d0825f6117c4 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by NikTh on 2012-07-06
> **fedenuche said:**
> Hi, I have installed ubuntu 12.04 and works great. After that I added a HD to move my backups. After move my files, i removed the HD and then when I try to boot my PC it returns me 

How did you backup your files ? what program or command ? 
Did you copy the files or move them ? is it possible that you moved system files also? by mistake ?  did you run update-grub or something similar ? 

Try this program --> [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) from a LiveCD.

---

### Post by fedenuche on 2012-07-06
I just copy the personal files.


[LIST]
[*]Files on desktop
[*]Thunderbird files
[*]Files in download folder
[*]Files in Documents folder
[/LIST]
I think that I haven't copied files system. I put all the backuped files on a folder and now when I go to this folder, I can't see any strange file (even pressing ctrl + h).


May be, the other HD was root on the other machine, so when Ubuntu detect mark it as a systems disk... I don't know if it has sense

---

### Post by s1baker on 2012-07-06
I will be interested in watching this thread. I also installed 12.04 on a HD and later I hooked up another HD that had 10.10 on it to copy some files over to 12.04. After I had done this and disconnected the 10.10 HD and tried to boot up into 12.04 I got errors similar to what you are talking about. Got it to working correctly, can't remember exactly what I did, I think I had to do a grub update on the 12.04 HD. I'm just a novice though, let the experts recommend.
 I have got to do this again in a month or so.

---

### Post by NikTh on 2012-07-06
Did you try this ? 

> **NikTh said:**
> 
Try this program --> [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) from a LiveCD.

---

### Post by s1baker on 2012-07-06
~also, if I remeber correctly, I think I ran gparted off of an .iso cd and had gparted to check the partitions. Gparted gave a message that an error was discovered and asked if I wanted for it to try to fix it, which I replied 'yes'.

I think that did the job. Gparted fixed it

---

### Post by fedenuche on 2012-07-06
> **NikTh said:**
> Did you try this ?

I did this and the problems is still there. This is the result of the BootRepair

[http://paste.ubuntu.com/1078579/](http://paste.ubuntu.com/1078579/)

> **s1baker said:**
> ~also, if I remeber correctly, I think I ran  gparted off of an .iso cd and had gparted to check the partitions.  Gparted gave a message that an error was discovered and asked if I  wanted for it to try to fix it, which I replied 'yes'.

I think that did the job. Gparted fixed it

I did it too, but after open gparted, it check my partitions (automatically) but none error was reported. I tried the grub update too, but it still there.

Thanks for you time.-

---

### Post by NikTh on 2012-07-06
.....Post Deleted ....

---

### Post by drs305 on 2012-07-06
NikTh had the right idea but there was a typo in the command he posted.

Boot to the Grub menu, press 'e' to edit the menuentry. Use the cursor keys and DEL to remove the "search" line completely.

On the 'linux' line, change the UUID=xxx and remainder to:
```
root=/dev/sda**6** ro   quiet splash $vt_handoff
```

If it boots, try running "sudo update-grub" again.

---

### Post by NikTh on 2012-07-06
> **drs305 said:**
> NikTh had the right idea but **there was a typo in the command he posted**.

Absolutely right. I corrected in 2nd post. 
Thanks and sorry :)

---

### Post by fedenuche on 2012-07-10
Sorry about the delay, i was in travel

> **drs305 said:**
> NikTh had the right idea but there was a typo in the command he posted.

Boot to the Grub menu, press 'e' to edit the menuentry. Use the cursor keys and DEL to remove the "search" line completely.

On the 'linux' line, change the UUID=xxx and remainder to:
```
root=/dev/sda**6** ro   quiet splash $vt_handoff
```If it boots, try running "sudo update-grub" again.

I did this, When i tried to boot with /dev/sda6 i could, but with the same errors. Any way, I did the "sudo update-grub", but,when I restart the errors still there.

```
evo3@evo3:~$ sudo update-grub
[sudo] password for evo3: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.0.0-19-generic
Found initrd image: /boot/initrd.img-3.0.0-19-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done
```

---

### Post by drs305 on 2012-07-10
> **fedenuche said:**
> 
I did this, When i tried to boot with /dev/sda6 i could, but with the same errors. Any way, I did the "sudo update-grub", but,when I restart the errors still there.


I have a few things you can try but none of them are really based on known solutions. I'm not sure what is going on with your system.

1. There was an old bug which caused the error message you are getting. Try running the following commands and see if you get any odd returns such as "ambivalent result":
```
sudo blkid /dev/sda6
sudo blkid -p /dev/sda6
```

2. Boot Repair found "Flexnet" issues, which is a situation in which Windows apps such as Dell Data Safe, HP Protect Tools, etc write to the same part of the disk as does Grub. In earlier editions of Grub 2, these apps had to be removed. In Grub 1.99 (grub-install -v), workarounds are automatically provided. 

You might try running the Boot Repair fix of this problem anyway. It's available under the Advanced/Grub Options, Reset Extra Space (Flexnet).

3. There could be errors on your partition which fsck might repair. This needs to be run with sda6 unmounted, so you would need to do it from a LiveCD or rescue CD/USB. Boot the CD, then run the following command on sda6:
```
sudo e2fsck -fyv /dev/sda6
```

---

### Post by fedenuche on 2012-07-10
> **drs305 said:**
> I have a few things you can try but none of them are really based on known solutions. I'm not sure what is going on with your system.

1. There was an old bug which caused the error message you are getting. Try running the following commands and see if you get any odd returns such as "ambivalent result":
```
sudo blkid /dev/sda6
sudo blkid -p /dev/sda6
```

Thi is the result of those commands:

```
evo3@evo3:~$ sudo blkid /dev/sda6
[sudo] password for evo3: 
/dev/sda6: UUID="4636ea0e-8134-4a38-a1a0-1aad92597a11" TYPE="ext4" 
evo3@evo3:~$ sudo blkid -p /dev/sda6
/dev/sda6: UUID="4636ea0e-8134-4a38-a1a0-1aad92597a11" VERSION="1.0" TYPE="ext4" USAGE="filesystem" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x83" PART_ENTRY_NUMBER="6" PART_ENTRY_OFFSET="57427968" PART_ENTRY_SIZE="100395008" PART_ENTRY_DISK="8:0" 
```> **drs305 said:**
> 2. Boot Repair found "Flexnet" issues, which is a situation in which Windows apps such as Dell Data Safe, HP Protect Tools, etc write to the same part of the disk as does Grub. In earlier editions of Grub 2, these apps had to be removed. In Grub 1.99 (grub-install -v), workarounds are automatically provided. 

You might try running the Boot Repair fix of this problem anyway. It's available under the Advanced/Grub Options, Reset Extra Space (Flexnet).

This is the result of this [http://paste.ubuntu.com/1084808/](http://paste.ubuntu.com/1084808/)

> **drs305 said:**
> 3. There could be errors on your partition which fsck might repair. This needs to be run with sda6 unmounted, so you would need to do it from a LiveCD or rescue CD/USB. Boot the CD, then run the following command on sda6:
```
sudo e2fsck -fyv /dev/sda6
```

I didn't do it yet because I would like to do a backup before do that. I'm pretty new and i afraid of mess up doing this.

Thanks.-

---

### Post by NikTh on 2012-07-10
> **fedenuche said:**
> 
I did this, When i tried to boot with /dev/sda6 i could, but with the same errors. Any way, I did the "sudo update-grub", but,when I restart the errors still there.
I don't know if i understood this correct , but why you didn't edit fstab ? 
```
gksudo gedit /etc/fstab
``` and change the UUID to /dev/sda6 , or  you can set a label to partition e.g "MyRoot" and edit fstab with LABEL=MyRoot instead (UUID).

---

### Post by fedenuche on 2012-07-11
> **NikTh said:**
> I don't know if i understood this correct , but why you didn't edit fstab ? 
```
gksudo gedit /etc/fstab
``` and change the UUID to /dev/sda6 , or  you can set a label to partition e.g "MyRoot" and edit fstab with LABEL=MyRoot instead (UUID).

That I did was:

> **NikTh said:**
> I don't know how this happened but try this ... just to boot in your system .. 
At grub menu and when you highlight the Ubuntu entry hit 'e' key .. then  go to line that says.. root=UUID=xxxxxx delete all the numbers and UUID  .. and write /dev/sda6 
The line should be like this.. 
** ```
root=/dev/sda6 ro quiet splash $vt_handoff
```**then hit F10 to boot in your system 
If boot in to your system .... try to change accordingly the /etc/fstab.
If you have questions about /etc/fstab then post back.

The result of that change was the same result (a lot of kills with error: Alert! /dev/sda6 does not exist. Dropping to shell). Do you think that I have to change the fstab anyway?

---

### Post by NikTh on 2012-07-11
> **fedenuche said:**
> That I did was:
The result of that change was the same result (a lot of kills with error: Alert! /dev/sda6 does not exist. Dropping to shell). Do you think that I have to change the fstab anyway?

Probably  misunderstood . 
I thought you was able to  boot in the OS (even with some errors) and run update-grub. 

Follow drs305 :)

---

### Post by fedenuche on 2012-07-11
> **drs305 said:**
> 
3. There could be errors on your partition which fsck might repair. This needs to be run with sda6 unmounted, so you would need to do it from a LiveCD or rescue CD/USB. Boot the CD, then run the following command on sda6:
```
sudo e2fsck -fyv /dev/sda6
```

This is the result:

```
ubuntu@ubuntu:~$ sudo e2fsck -fyv /dev/sda6
e2fsck 1.41.14 (22-Dec-2010)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  326313 inodes used (10.40%)
     585 non-contiguous files (0.2%)
     493 non-contiguous directories (0.2%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 277690/261
 4814361 blocks used (38.36%)
       0 bad blocks
       1 large file

  221413 regular files
   40853 directories
      57 character device files
      25 block device files
       0 fifos
      32 links
   63954 symbolic links (48268 fast symbolic links)
       2 sockets
--------
  326336 files
ubuntu@ubuntu:~$ 
```

---

### Post by drs305 on 2012-07-11
It doesn't look like the check found errors, or if it did it fixed them. You can try rebooting. If you still get the error message I'm just about out of ideas. I think you have already tried not using UUIDs in the GRUB menu.

---

### Post by fedenuche on 2012-07-12
No problem, many thanks drs305, NikTh, cipherboy_loc and s1baker for your time and concern. I will reinstall the system.

---

