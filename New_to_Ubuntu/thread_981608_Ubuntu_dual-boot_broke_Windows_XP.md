---
title: "Ubuntu dual-boot broke Windows XP?"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by seanbow on 2008-11-13
I recently installed Ubuntu 8.10 in a dual-boot setup with Windows XP. The installation went great and Ubuntu is working very well, but when I tried to go back to XP, about 5 seconds after the splash screen with loading bar comes up, I get a "halt" BSOD. 

My hard drive was originally in 3 partitions: a ~100 MB recovery partition, a ~150GB Windows partition, and a ~150GB partition for random crap. I chose to reduce the Windows partition by 35 GB or so in the Ubuntu installation, leading to the current setup of 100MB recovery, ~115GB Windows, ~35GB Ubuntu, and ~150gb whatever. When I try to access the other partitions through Ubuntu, I can access the 150gb one fine, but the windows partition fails to mount.

---

### Post by kansasnoob on 2008-11-13
So, you do get the Grub screen on reboot where you can choose which system to boot?

It might help to see the output of:

```
 sudo fdisk -l
```

That's a lower case L.

---

### Post by bumanie on 2008-11-13
Go into console mode on windows (via install cd) and do a fsck to check the filsystem. Did you defrag before shrinking?

---

### Post by Hospadar on 2008-11-13
I think most likely something got messed up when you resized the windows partition.  Maybe try repairing with a windows install cd.  If that doesn't work, maybe you can use chkdisk (or whatever the windows partition repair tool is called) to try and fix your windows partition.

It's also possible that when ubuntu installed grub it didn't properly relocate your windows bootloader (that's just a guess), so maybe re-installing your windows boot loader will fix the problem.

You'll need to:
Copy over the windows boot loader from the windows installation cd (google how to do it)
Then re-install grub, there are guides on how to do this in the community docs link in my sig

---

### Post by seanbow on 2008-11-13
Windows does show up in the boot loader, yes.
Sudo fdisk -l outputs:
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95f22c37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
/dev/sda2   *          14       12046    96655072+   7  HPFS/NTFS
/dev/sda3           16621       34249   141604942+   7  HPFS/NTFS
/dev/sda4           34250       38913    37463580    5  Extended
/dev/sda5           34250       38716    35881146   83  Linux
/dev/sda6           38717       38913     1582371   82  Linux swap / Solaris

```

I messed around with partitions before installing Ubuntu; my goal was to get it to install in the now empty 37gb "Extended" section, but I couldn't really figure out how to do it so I just had it shrink the windows partition.

No, I didn't defragment before it. Was I supposed to? Argh.

I actually don't have a Windows CD with me, it's at home (I live in a dorm). I'll run home and pick it up soon, maybe tomorrow, so I can try the other options.

Thanks for the help.

---

### Post by R.Bucky on 2008-11-14
Uhhh. Yup. You were supposed to defrag the Windoz partition at least once before you install the dual boot. NTFS partitions write data all over the hard-disks. Defragging consolidates most or all of the data into sections. Sounds like you overwrote some core data bits. If you have the XP disk, you might want to think about a fresh install.

I am sure that others might have recovery suggestions... anyone?

---

### Post by bumanie on 2008-11-14
I'd try the filesystem check first and if that doesn't work, other options can be looked at. You could even run xfix from within ubuntu - but we'll get to that later if necessary.

---

### Post by ugm6hr on 2008-11-14
> **seanbow said:**
> I messed around with partitions before installing Ubuntu; my goal was to get it to install in the now empty 37gb "Extended" section, but I couldn't really figure out how to do it so I just had it shrink the windows partition.

For your info, it looks like Ubuntu [B]is[B] in the Extended (sda4) partition - with sda5 & 6 being within sda4.

And for future reference - if you intend to *mess around with partitions*, make sure you have decent backups first.  Re-partitioning puts all your data at risk.

Sorry, I can't add anything to your current issue.

---

### Post by underground on 2008-11-14
Please post the output of /boot/grub/menu.lst file

---

### Post by caljohnsmith on 2008-11-14
Seanbow, do you have your Windows Install CD? I would begin by booting that, go to the "recovery console", and doing:
```
chkdsk /r
```
And run that as many times as it takes until it reports no errors. If you don't have a Windows Install CD, you can download a Windows XP Repair CD from [here]("http://www.webtree.ca/windowsxp/tools/bootdiscs/xp_rec_con.zip"). How about giving that a shot first, reboot XP, and let us know how far you get. Also, please post your /boot/grub/menu.lst like Underground asked for so we can make sure Grub is booting XP correctly.

---

### Post by seanbow on 2008-11-18
Awesome. I got my Windows CD today and ran chkdsk /r a couple times, and I'm now posting this from within Windows XP. Everything seems to be running well. Thanks for the help everyone!

I would love to be able to back up my data before I resize partitions and such, but I really have no way to back up ~100gb of stuff. I should invest in an external hard drive...

---

