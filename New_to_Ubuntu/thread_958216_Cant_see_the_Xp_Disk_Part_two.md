---
title: "Cant see the Xp Disk: Part two"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by mr-woof on 2008-10-25
I cant't seem to find my original XP disk problem thread, so i've started this new one. 

This is the way i'm setup at the moment, i've got a 160gb sata disk with xp installed that has two partitions (install and data) and a 10gb ide drive (this ubuntu install) with a dvd writer on the same cable.

I original installed 8.04 while in windows and once installed i couldn't see the xp disk, so last night i formatted the 10gb disk and installed 7.04 while in the live cd and all was well once it booted up. I could see the xp disk and it's partitions once i installed the ntfs config tool. 

I did all the updates and noticed i could upgrade to 8.04, so i thought now i can see the windows disk i might as well. It's just finished and now i can't see the xp disk again! :confused:

I think with the 7.04 install, it proves there is nothing wrong with my xp disk and it's something to do with the 8.04 install itself. 

I've just tried sudo fdisk - l and it's only picking up the 10gb disk, anyone got any ideas?

---

### Post by mr-woof on 2008-10-25
Anyone got any ideas on this? I don't really want to downgrade to 7.04

---

### Post by Duck2006 on 2008-10-25
Can you see it under Places.

---

### Post by mr-woof on 2008-10-25
Nope, only the 10gb disk ubuntu is installed on

---

### Post by Duck2006 on 2008-10-25
Is it in your fstab? If not your have to mount the drive.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by Sponzenbroekske on 2008-10-25
check if everything is installed to read/write ntfs.

---

### Post by drowner on 2008-10-25
> **Duck2006 said:**
> Is it in your fstab? If not your have to mount the drive.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

The OP said it didn't even show up with a sudo fdisk -l, so I actually think it could be a hardware detection, rather than a mounting error.

It seems very unusual, though

Could we see the output of 

```
sudo fdisk -l
```

just for curiousity's sake?

---

### Post by ethoxyethaan on 2008-10-25
try 
```
sudo fdisk -l
```
instead of
```
sudo fdisk - l
```
might be the problem!

---

### Post by drowner on 2008-10-25
> **ethoxyethaan said:**
> try 
```
sudo fdisk -l
```
instead of
```
sudo fdisk - l
```
might be the problem!

Nice spot!

I'm gunna hunt down the OP's original thread too..... BRB

Edit: Didn't show original command.

---

### Post by mr-woof on 2008-10-25
Listen to this for weirdness, in the boot up menu you have the option of two different kernels. 2.6.24-21 and 2.6.22.15, i thought i'd try 2.6.22.15 and the xp disk was there. I mounted it, open it up all is fine. :)

Great i think, i'll restart to write the kernel numbers down to post here. I'm using 2.6.22.15 now and the disk has gone again lol :)

Output of sudo fdisk -l

isk /dev/sda: 10.0 GB, 10007101440 bytes
255 heads, 63 sectors/track, 1216 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb7b2b7b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1159     9309636   83  Linux
/dev/sda2            1160        1216      457852+   5  Extended
/dev/sda5            1160        1216      457821   82  Linux swap / Solaris

I give up lol

edit: I've just noticed something, i just ran ntfs config and the option to tick "enable write support for internal device" is greyed out

---

### Post by Paqman on 2008-10-25
Have you checked for loose cables on your drives? Give them a good push home just in case. Sometimes going right back to basics can save a lot of hassle.

---

### Post by mr-woof on 2008-10-25
Strange, i've just rebooted and tried the other kernel and the disk is now available again. :confused:

I've just ran ntfs-config again and it picked the device up and asked if i wanted to mount it, so i said yes. I can access it now, and the internal open in ntfs is now enabled. 

I'm going to give it another quick reboot to see what it does

---

### Post by mr-woof on 2008-10-25
And it's still there ::popcorn::popcorn::popcorn:

Not sure what's the difference between the two kernels, but it's working now

---

### Post by jerome1232 on 2008-10-25
Honestly doesn't sound like it's the kernels, but rather the bios not picking up the drive correctly, or a semi-loose power/ide cable. To me it says hardware all over it.

---

### Post by mr-woof on 2008-10-25
When i get back later on, i'll check the sata cable/power cable that goes into the drive and report back :)

---

### Post by mr-woof on 2008-10-26
Right, i've checked all the cables, everything is fine nothing loose. 

I've just restarted using kernel 2.6.24.21 and the drive had gone, restarted again using 2.6.22.15 and the drive is mounted and all is well.

:confused:

---

