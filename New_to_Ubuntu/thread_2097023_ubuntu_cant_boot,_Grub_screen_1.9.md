---
title: "ubuntu cant boot, Grub screen 1.9"
date: 2012-12-21
forum: New to Ubuntu
---

### Post by Inphi on 2012-12-21
Hello I'm typing on my phone and im in a hhurry so bear with me. 
I am unable to boot Ubuntu precise (dual boot). 
I got the grub screen. Don't know what it it, so I checked online for a related problem, followed instructions. But none of them seemed to work.
The ls output is something like:
(Hda) (loop) (hda1, msdos1) (hda2, msdos3), etc.
Search -f vmlinuz returns an errror. Can't run boot. Tried holding shift. Don't have access to a live CD. Please let me know how to fix. I'm at a country with limited internet right now so I can't Download any Images for the time being. 
I know my post is a little cryptic but please bear with me. I'm sorry 
Please answer a fix or an approximate solution as soon as possible 
And also please don't send me a link to a related solved problem . I've checked them ALL
Ps.: I may be unable to provide more details till Sunday, when I'm settled in the country
PSS: I have a persistent backtrack r5 USB on me.

I'm begging you to help me before I get back to my country. Need to work on my Ubuntu.
Pass: my Ubuntu disk is sda3, however the ls output on grub only shows up hdas. I checked to see if vmlinuz is present in sda1 via btr5. Its there, iso I think it may be corrupted. 



Again sorry for the bad typing

---

### Post by Bashing-om on 2012-12-21
Inphi; HI !

See if this will get you back up:
From a cold boot, when the grub menu appears, choose the "recovery mode" kernel to boot. In that next menu choose grub, See if that option repairs your grub.

[INDENT][INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT][/INDENT]

---

### Post by Inphi on 2012-12-23
Hello, 
sorry for taking so long to respond. 

The problem is that when I choose the Ubuntu OS at the dual-boot screen, I am presented with the grub command line interface, instead of the usual grub menu screen.

I installed Ubuntu on Windows using wubi (a foolish act on my part). From my research on this issue, I have discovered that there have been a lot of problems regarding the wubi install.
Also, I tried mounting the sda* device from a BT5 pendrive. For some reason, I was unsuccessful. I thought the bootloader was corrupt, now I'm not so sure.

The only eventful modification that I have performed on my Ubuntu OS was to increase the size of the wubi partition. This was done 2 weeks ago, so I doubt this grub issue cropped up because of that.

Lastly, I cannot find my installed 3.2 kernel files anywhere on Windows. I could only see initrd.img-2.6.32-41-generic, vmcoreinfo-2.6.32-41-generic, etc. This was from C:/ubuntu/disks/boot. Could the 3.2 files have been deleted (overwritten), or are the 3.2 files located somewhere else?

---

### Post by Inphi on 2012-12-23
One another note:
The grub.cfg is not present at /boot/grub of the mounted Ubuntu disk. In fact the /boot directory is empty (no hidden files either). As such, there is a broken symbolic link /initrd.img to /boot/initrd.img-2.6.32-41-generic
Will post the output of the bootinfoscript soon.

---

### Post by Bashing-om on 2012-12-23
Inphi;
Regret to say, I have no knowledge or experience with "wubi" install.
Wait for others, with the experience, to pick up on this thread.
I Hope there is a resolution soonest.

[INDENT][INDENT]Best to you <== BDQ

[/INDENT][/INDENT]

---

### Post by SpiderSkull on 2012-12-23
Try this:

Boot up windows, Windows should start with a Check Disk screen. Let windows complete this. When windows is done, restart you computer and try to boot up ubuntu this was enough to fix a friend his computer.

Edit: When windows doesn't start this screen by it's self. you can run cmd and enter: "chkdsk /X /F" (without the quotes) Restart windows.

---

### Post by Inphi on 2012-12-23
I already tried running chkdsk, and I got no errors. I also tried fsck root.disk via bt5. No errors.

---

### Post by Inphi on 2012-12-24
Guys I'm truly in deep s**t:
So after hours of trying to find my Ubuntu kernel 3.2, I tried booting the 2.6 kernel. It worked fine, BUT, all the work and data that I had put in since the 3.2 kernel are not present in the 2.6. 

The kernel source i used was C:/ubuntu/disks/boot/vmlinuz-2.6.32-41-generic.
The initrd source is initrd-img-2.6.32-41-generic (on the same path as above).

As stated earlier, I had to extend the wubi partition because I was running out of space. So I have a G: local disk, with the label 'Ubuntu' on Win7. Could the data after the upgrade be there? I am unable to verify this because ext2explore wouldn't even open the root.disk in the G: local disk.


Here's the bootinfoscript output:
[http://pastebin.com/0WKGJUWD](http://pastebin.com/0WKGJUWD)

Also, I just noticed that fdisk -l reported that Partition 3 (the  wubi extended partition) does not start on physical sector boundary.
The output was something like this:
```

Disk /dev/sda: 1000.2 GB, 1000204866016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x84ca151b

   Device Boot   Start     End      Blocks   Id    System
/dev/sda1    *       1      26      203776    7    HPFS/NTFS
Parition 1 does not end on cylinder boundary. 
/dev/sda2           26   112388   902544383   7    HPFS/NTFS
/dev/sda3       112388   121601    74010848   f    W95 Ext'd (LBA)
Partition 3 does not start on physical sector boundary.
/dev/sda5       112388   118762    51198944   7    HPFS/NTFS
/dev/sda6       118762   121601    22810848+  7    HPFS/NTFS


```

---

