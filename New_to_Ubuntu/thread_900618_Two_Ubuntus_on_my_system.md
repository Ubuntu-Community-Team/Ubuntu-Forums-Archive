---
title: "Two Ubuntus on my system"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by tcyk on 2008-08-25
I recently tried to boot a Solaris 10 DVD and it stalled, just like the stable version of OpenSolaris. I thought that perhaps the program was a bit long so I left and got myself something to eat. When I returned, I still had the same three lines of text at the top of the screen and nothing had happened. I turned the computer off and tried to reboot my Ubunto Hoary Heron system. It failed. After a rather long wait, it started testing and I repeatedly saw the following:
ata2.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
Of course this meant nothing to me. I decided I needed to reinstall Ubuntu.
I gave it 40 GB as before. During the process I  was asked if I wanted to import x and y and I thought, "Goody, I'm not going to lose all my files."

When installation was finished and I restarted the computer, Grub came up with two Ubuntu choices complete with safe and text on both of them. The windows choice was in the middle of the six Ubuntu choices. I selected the top one and a brand new bare system was loaded. I clicked the bottom one (four down) and my old system loaded. Everything was like always except a new drive showed up on the desktop. The drive was labeled, "121.6 GB Media" and it contained Linux files. I thought I must have lost a big chunk of windows but when I rebooted windows, everything was normal. 

Going back to the original Ubuntu, I checked properties of the new drive and found that it was located on my external hard drive. I didn't tell it to do that and I don't need two Ubuntu operating systems on the same computer. What am I supposed to do?

A perplexed newby -- Charlie ... and plenty mad at Sun and Solaris

---

### Post by kansasnoob on 2008-08-25
Would you please post the output of:

```
sudo fdisk -l
```

That's an L at the end rather than a one.

---

### Post by candtalan on 2008-08-25
In general, an automated ubuntu install will resize an existing system and install an additional system. It will not generally overwrite the existing system unless you tell it to (although be careful - situations can be very complicated and data can be lost).

What may have happened is that the first ubuntu partitons have been added to with another partition (or partitions). It will be useful to note carefully which ubuntu works ok (or if both do?) and also windows - you tried that. Also look at the  size of the windows drive, to assess where the disk space for the second ubuntu came from.

Be sure to have backed up your data in case of disasters.
Then decide which install you want to keep and why.

Decide on any partition resizing that might be necessary.

Plan the actions and checks that you might want to proceed with.

Go gently, and good luck.

---

### Post by kansasnoob on 2008-08-25
> **candtalan said:**
> In general, an automated ubuntu install will resize an existing system and install an additional system. It will not generally overwrite the existing system unless you tell it to (although be careful - situations can be very complicated and data can be lost).

What may have happened is that the first ubuntu partitons have been added to with another partition (or partitions). It will be useful to note carefully which ubuntu works ok (or if both do?) and also windows - you tried that. Also look at the  size of the windows drive, to assess where the disk space for the second ubuntu came from.

Be sure to have backed up your data in case of disasters.
Then decide which install you want to keep and why.

Decide on any partition resizing that might be necessary.

Plan the actions and checks that you might want to proceed with.

Go gently, and good luck.


It sounds rather like the OP also had an external data drive plugged in while (re)installing Ubuntu, so I rather suspect that we have two Ubuntu's on two separate drives.

I'm thinking,

#1: Make sure both Ubuntu's are truly bootable and work! If the original Ubuntu is badly messed up the OP may want to just reinstall it properly. If it seems OK other, than not booting without the external drive plugged in, then restore Grub to the original Ubuntu.

#2: If the external drive was purely a data drive see what can be recovered and then delete the unwanted "new" Ubuntu. And in the future leave no external drives plugged in during the install of a new OS, unless the new OS is intended to install on that external drive, which will require some fiddling with Grub if one ever wants to boot without that drive plugged in.

---

### Post by tcyk on 2008-09-04
> **kansasnoob said:**
> Would you please post the output of:

```
sudo fdisk -l
```

That's an L at the end rather than a one.

Sorry to be so slow about getting back to you. It seems someone neglected to pay for our Internet service and I wasn't informed until after I discovered I had a problem :)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2               7        1312    10485760    7  HPFS/NTFS
/dev/sda3   *        1312       52818   413718750    7  HPFS/NTFS
/dev/sda4           52819       60801    64123447+   5  Extended
/dev/sda5           52819       60470    61464658+  83  Linux
/dev/sda6           60471       60801     2658726   82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       45385   364554981    c  W95 FAT32 (LBA)
/dev/sdc2           45386       60801   123829020    5  Extended
/dev/sdc5           45386       60169   118752448+  83  Linux
/dev/sdc6           60170       60801     5076508+  82  Linux swap / Solaris

I believe my original Ubuntu is now on the external hard drive dev/sdc5.

---

### Post by tcyk on 2008-09-04
> **kansasnoob said:**
> It sounds rather like the OP also had an external data drive plugged in while (re)installing Ubuntu, so I rather suspect that we have two Ubuntu's on two separate drives.

I'm thinking,

#1: Make sure both Ubuntu's are truly bootable and work! If the original Ubuntu is badly messed up the OP may want to just reinstall it properly. If it seems OK other, than not booting without the external drive plugged in, then restore Grub to the original Ubuntu.

#2: If the external drive was purely a data drive see what can be recovered and then delete the unwanted "new" Ubuntu. And in the future leave no external drives plugged in during the install of a new OS, unless the new OS is intended to install on that external drive, which will require some fiddling with Grub if one ever wants to boot without that drive plugged in.

You are correct. I saw no need to unplug the external drive I was asked the normal petitioning questions and then I was asked if I wanted to save my users to which I replied yes. I am quite sure that the original Ubuntu is on the external hard drive and the new unadulterated one is on the internal drive. Maybe I can put another distro there if I decide to try something else. If the Flash player worked on Bridgebase.com I might give up windows altogether. ... but that's another problem.

---

### Post by tcyk on 2008-09-04
I forgot to mention that both Ubuntos work fine.

---

