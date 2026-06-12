---
title: "[SOLVED] I just deleted my partition table and GRUB"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by raycosm on 2008-10-25
While trying to remove GRUB from the MBR of a USB using dd from a Live CD, I accidentally used it on my hard drive instead of my USB drive

```
dd count=1 bs=512 if=/dev/zero of=/dev/sda

```

I copied and pasted that from some website, it gave me permission denied, so I sudo'd, and ran the command on my computer's hard drive (sda) instead of my USB drive (sdb).

Well now I have no partition table and GRUB on my hard drive. I'm still in the Live CD at the moment, and I haven't touched anything yet, so how would I get my partition table (and GRUB) back?

---

### Post by Duck2006 on 2008-10-25
Reinstall again.

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Edit: that should have read: reinstall grub again.

---

### Post by bpowell2005 on 2008-10-25
> **raycosm said:**
> While trying to remove GRUB from the MBR of a USB using dd from a Live CD, I accidentally used it on my hard drive instead of my USB drive

```
dd count=1 bs=512 if=/dev/zero of=/dev/sda

```

I copied and pasted that from some website, it gave me permission denied, so I sudo'd, and ran the command on my computer's hard drive (sda) instead of my USB drive (sdb).

Well now I have no partition table and GRUB on my hard drive. I'm still in the Live CD at the moment, and I haven't touched anything yet, so how would I get my partition table (and GRUB) back?

Take a look here:

[http://ubuntuforums.org/showthread.php?p=2210436](http://ubuntuforums.org/showthread.php?p=2210436)

Before you try writing to the drive. Since you're online in a live CD environment, just don't mount the drive and do some research before you make a move...I'd be worried once you start writing to the drive you could potentially overwrite some data.

The good news is it looks possible to restore your partitions. Once they're restored, you can reinstall GRUB no worries.

I'll keep fishing around for other threads that cover this.

---

### Post by caljohnsmith on 2008-10-25
You can use testdisk to rebuild your partition table:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partitions. Also let me know what your partitions should be if you can remember.

---

### Post by bpowell2005 on 2008-10-25
Okay! Looks like you're on the road to recovery. I'm newish to Linux, so I'd take the advise of those that have been around longer over mine. But I'd like to submit one more web site for you to research:

[http://www.salingfamily.net/trav/linux/lost_partition.html](http://www.salingfamily.net/trav/linux/lost_partition.html)

It looks pretty reasonable, you can avoid installing programs to floppy and rebooting and such (as the web site suggests) since you're already running in LIVECD.

I think with all of the other suggestions above, you'll be back up and running in no time!

Good luck!

---

### Post by bodhi.zazen on 2008-10-25
OUCH

Well, with that command you wrote all zeros to your hard drive. Data recovery will be difficult at best, if you need data recovery STOP using the hard drive and seek professional help.

Otherwise, yes you will be re-installing.

---

### Post by bpowell2005 on 2008-10-25
> **bodhi.zazen said:**
> OUCH

Well, with that command you wrote all zeros to your hard drive. Data recovery will be difficult at best, if you need data recovery STOP using the hard drive and seek professional help.

Otherwise, yes you will be re-installing.

Again, I'm just learning linux, and don't want to disrespect...but, I think he only wrote Zero's to one block (the first block) of 512 bytes...so the MBR and maybe the partition table...unless I'm reading the command incorrectly?

Certainly, I agree with the advice: don't use the drive! Don't mount it or write to it until you have a good plan of attack ready.

---

### Post by raycosm on 2008-10-25
> **caljohnsmith said:**
> You can use testdisk to rebuild your partition table:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help recovering your partitions. Also let me know what your partitions should be if you can remember.

Running on /dev/hda just gave me 

```
Disk /dev/hda - 512 B - CHS 1 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors


Partition sector doesn't have the endmark 0xAA55

```

Then proceeding after the Vista Y/N gives me
```
Disk /dev/hda - 512 B - CHS 1 255 63
     Partition               Start        End    Size in sectors

```

Deeper search gives me the same thing, so at this point I assume I was supposed to run it on /dev/sda.

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19457 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors


Partition sector doesn't have the endmark 0xAA55

```

After the search for Vista
```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19458 255 63
     Partition               Start        End    Size in sectors
* HPFS - NTFS              0   1  1  1018 254 63   16370172 [PQSERVICE]
P HPFS - NTFS           1019   0  1 14209 254 63  211913415 [ACER]
P Linux                14210   0  1 15090 254 63   14153265
L Linux                15091   1  1 19328 254 63   68083407
L Linux Swap           19329   1  1 19456 254 63    2056257


```

And it tells me to use the arrows to select a partition. The partitions listed on that screen are the partitions that were one my computer, so it looks like everything's still intact. The first partition is some hidden partition that came with my computer, the second is Vista. The third is Ubuntu, next is /home, and last is swap. /home and swap were on a logical partition or something like that while Ubuntu was separate.

---

### Post by bpowell2005 on 2008-10-25
Woo hoo! This is great news! I've never tried to recover partitions before, I imagine you'll be using fdisk or parted to finish this process up, but frankly, I'm going to defer to those more experienced at this point. However, I'm going to follow this thread, as I would love to learn how to recover from this, and I also want to see you post here from your recovered computer!

---

### Post by caljohnsmith on 2008-10-25
> **raycosm said:**
> 
And it tells me to use the arrows to select a partition. The partitions listed on that screen are the partitions that were one my computer, so it looks like everything's still intact. The first partition is some hidden partition that came with my computer, the second is Vista. The third is Ubuntu, next is /home, and last is swap. /home and swap were on a logical partition or something like that while Ubuntu was separate.
That's good news then; just get back to that screen after the deep search where it lists all your partitions, and go ahead and select the "write" to write that partition table to your HDD. Then reboot, and see if you can access the partitions.

---

### Post by bodhi.zazen on 2008-10-25
> **bpowell2005 said:**
> Again, I'm just learning linux, and don't want to disrespect...but, I think he only wrote Zero's to one block (the first block) of 512 bytes...so the MBR and maybe the partition table...unless I'm reading the command incorrectly?

Certainly, I agree with the advice: don't use the drive! Don't mount it or write to it until you have a good plan of attack ready.

oh, I missed that, sorry.

Congrats on getting up and going (nice to be wrong sometimes).

---

### Post by raycosm on 2008-10-25
Well that didn't seem to do anything, I wrote and rebooted, and I was presented with the Acer recovery software. It gave me the option to restore from a disk (which I don't have) and reinstall Windows, so I just quit. Then my computer just ended up in and endless restarting cycle where it only got past the bios before it restarted. So I put the Live CD back in, and now I'm trying testdisk again

---

### Post by caljohnsmith on 2008-10-25
How about posting:
```
sudo fdisk -lu
```

---

### Post by raycosm on 2008-10-25
Well I surmise that my computer was in endless rebooting because of the lack of GRUB or something like it, because I booted up Super GRUB Disk and somehow managed to log into my Ubuntu.

> **caljohnsmith said:**
> How about posting:
```
sudo fdisk -lu
```

It gives me

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xaf88af88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    16370234     8185086    7  HPFS/NTFS
/dev/sda2        16370235   228283649   105956707+   7  HPFS/NTFS
/dev/sda3   *   228283650   242436914     7076632+  83  Linux
/dev/sda4       242436915   312592769    35077927+   f  W95 Ext'd (LBA)
/dev/sda5       242436978   310520384    34041703+  83  Linux
/dev/sda6       310520448   312576704     1028128+  82  Linux swap / Solaris

```

I think everything's back to normal though.

---

### Post by garyed on 2008-10-25
I thought that just the MBR was overwritten with zero's.
Why can't he just boot from a live CD & reinstall grub?
My understanding of the dd command is that's all that happened is the first block of 512 bytes got overwritten. Someone correct me if I'm wrong.

---

### Post by raycosm on 2008-10-25
On further inspection, it seems that I cannot boot into Vista. I select it via GRUB, and my computer just restarts. It's no big deal, I do 90% of my computing in Linux anyway, and all my important data was either synced through multiple services or not important anyway, and Vista was incredibly slow compared to Ubuntu. I'd like to still be able to use it though, without having to reinstall.

> **garyed said:**
> I thought that just the MBR was overwritten with zero's.
Why can't he just boot from a live CD & reinstall grub?
My understanding of the dd command is that's all that happened is the first block of 512 bytes got overwritten. Someone correct me if I'm wrong.

The first 512 bytes contain both the MBR and the partition table, I think.

---

### Post by caljohnsmith on 2008-10-25
> **garyed said:**
> I thought that just the MBR was overwritten with zero's.
Why can't he just boot from a live CD & reinstall grub?
My understanding of the dd command is that's all that happened is the first block of 512 bytes got overwritten. Someone correct me if I'm wrong.
The MBR contains both the boot loader code and the partition table:
```

**Bytes:**
  1-440    MBR boot code
441-444    4 byte Disk signature used by Windows OSes
445-446    nulls
447-510    partition table
511-512    MBR signature, always 0xAA55 (byte 511=55, byte 512=AA)
```
So if you don't have a Windows OS on the drive, the MBR boot code can actually occupy bytes 1-446, and the rest is basically the partition table. Anyway, that was probably more than you wanted to hear. :)

---

### Post by caljohnsmith on 2008-10-25
> **raycosm said:**
> On further inspection, it seems that I cannot boot into Vista. I select it via GRUB, and my computer just restarts. It's no big deal, I do 90% of my computing in Linux anyway, and all my important data was either synced through multiple services or not important anyway, and Vista was incredibly slow compared to Ubuntu. I'd like to still be able to use it though, without having to reinstall.

Vista uses the 4 byte "disk signature" that I mentioned above, so to fix Vista, probably all you need to do is rebuild Vista's partition table so that it can deal with the change to the MBR. If you have your Vista Install CD, just go to the command line and run:
```
bootrec /rebuildbcd
```
And while you are in the Vista CD, it would be good to also run:
```
bootrec /fixboot
chkdsk /r
```
And run the chkdsk as many times as it takes until it completes with no errors. Anyway, doing the above commands would probably be all it takes to get Vista going again.

---

### Post by raycosm on 2008-10-25
> **caljohnsmith said:**
> Vista uses the 4 byte "disk signature" that I mentioned above, so to fix Vista, probably all you need to do is rebuild Vista's partition table so that it can deal with the change to the MBR. If you have your Vista Install CD, just go to the command line and run:
```
bootrec /rebuildbcd
```
And while you are in the Vista CD, it would be good to also run:
```
bootrec /fixboot
chkdsk /r
```
And run the chkdsk as many times as it takes until it completes with no errors. Anyway, doing the above commands would probably be all it takes to get Vista going again.

Oh curse you Acer and OEMs, I don't have a Vista DVD. Is there an alternative other than pirating it?

---

### Post by caljohnsmith on 2008-10-25
> **raycosm said:**
> Oh curse you Acer and OEMs, I don't have a Vista DVD. Is there an alternative other than pirating it?
Fortunately, there is; you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/").

---

### Post by raycosm on 2008-10-25
> **caljohnsmith said:**
> Fortunately, there is; you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/").

Well now everything works normally. I can't thank you enough for your help.

---

### Post by caljohnsmith on 2008-10-25
> **raycosm said:**
> Well now everything works normally. I can't thank you enough for your help.
You're certainly welcome; cheers and have fun Ubuntu-ing. :)

---

