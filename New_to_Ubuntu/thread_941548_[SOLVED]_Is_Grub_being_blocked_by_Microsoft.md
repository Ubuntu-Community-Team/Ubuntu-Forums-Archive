---
title: "[SOLVED] Is Grub being blocked by Microsoft"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Scunnered on 2008-10-08
I have been flirting with Linux off and on and found that it was possible to work with both Linux and Doz.  I wished to move over to Linux but found that having installed the OS on an external USB hard drive that as long as I kept the external drive switched on I could work with the Linux.  However if on being given the choice of using Ubuntu or Linux Mint and that of XP if I selected XP I was unable to acces it. Grub error messages are displayed.

Has there been either a change with Grub that causes this problem or is there a way around it.

I am more than happy that I can so far achieve what I want but she who must be obeyed still insists on XP and therefore as my life is at stake I must bend the knee.

Am I able to keep the OSs totally apart or must I work on individual partitions.  This is not my preferred option as XP has been a pain in the nether region and the reason why I want to totally avoid Microsoft.  

If you can offer up a means of having Ubuntu as the main OS and XP as a secondary choice which will work I will be most interested in that.

I hope that you will be able to assist me is a complete switch over to Linux.

---

### Post by handydan918 on 2008-10-08
If I understand you correctly, you have installed Ubu on an external (usb?) drive. This often gets more complicated than just installing it on it's own partition alongside Windows.
You really needn't be concerned about sharing a disk with Windows. It can't even natively read, let alone write, to Ubu's ext3 file system.
I'd recommend reinstalling on an internal disk.

---

### Post by philinux on 2008-10-08
Boot up into ubuntu on your external drive. Open a terminal from the accessories menu.

Use these two commands and paste the output of each back here.


```
sudo fdisk -l

cat /boot/grub/menu.lst
```

---

### Post by Scunnered on 2008-10-08
**handydan918** 

I appreciate that there are problems with this type of install. I am being forced to keep Doz and Linux apart as my partner does not wish to get involved with Linux.

I would much prefer to have 2 different drives each booting independantly of each other but it seems to me that Windows is screwing matters up.  Earlier in my experience with Linux I was able to boot Linux and go back and forward to XP without any problem but not now.  I had thought of using an old system but I would need to set up a wireless network and as space is a problem I would much prefer to have one system with 2 HDs.

Of late I have been having major problems with XP as I totally lost one HD and had to resort to a data recovery company.  A second HD failed but this time as I was running Puppy from a CD I was able to save data via that OS.  Now I have far too much data on the HD to use a live cd/dvd option therefore the need for 2 HDs

**philinux**

I will have a look at this later as I am currently at work.  Will have to reinstall as I had to fix the master boot record so that she who must be obeyed had her wish.

Many thanks to you both for your assistance

---

### Post by gregorio on 2008-10-08
Scunnered,

She who must be obeyed wouldn't happen to be named Hilda?
(sorry about diverting the subject, but couldn't resist asking, I being one who enjoyed Rumpole of the Bailey)

---

### Post by handydan918 on 2008-10-09
> **Scunnered said:**
> **handydan918** 

I appreciate that there are problems with this type of install. I am being forced to keep Doz and Linux apart as my partner does not wish to get involved with Linux.I understand perfectly ;-)> 

I would much prefer to have 2 different drives each booting independently of each other but it seems to me that Windows is screwing matters up.  Earlier in my experience with Linux I was able to boot Linux and go back and forward to XP without any problem but not now.  I had thought of using an old system but I would need to set up a wireless network and as space is a problem I would much prefer to have one system with 2 HDs.
This is precisely what I was thinking of-but not with an external (usb?) drive. That seems to be the sticking point on so many of these things. If you can stuff another disk into the case, and install Ubu on that, dedicating the MBR to GRUB will work just fine for kyou. Just make sure that Windows gets the first partition of the first drive, and it will all go smoothly.

---

### Post by drowner on 2008-10-09
> **Scunnered said:**
> **handydan918** 

I appreciate that there are problems with this type of install. I am being forced to keep Doz and Linux apart as my partner does not wish to get involved with Linux.

I would much prefer to have 2 different drives each booting independantly of each other but it seems to me that Windows is screwing matters up.  Earlier in my experience with Linux I was able to boot Linux and go back and forward to XP without any problem but not now.  I had thought of using an old system but I would need to set up a wireless network and as space is a problem I would much prefer to have one system with 2 HDs.

Of late I have been having major problems with XP as I totally lost one HD and had to resort to a data recovery company.  A second HD failed but this time as I was running Puppy from a CD I was able to save data via that OS.  Now I have far too much data on the HD to use a live cd/dvd option therefore the need for 2 HDs

**philinux**

I will have a look at this later as I am currently at work.  Will have to reinstall as I had to fix the master boot record so that she who must be obeyed had her wish.

Many thanks to you both for your assistance

If you fix the MBR you won't have to reinstall, you will just have to reinstall GRUB later.

There are several ways you could approach this problem. I understand your partner does not wish to use linux, but surely a small partition on the drive is not going to affect anything?

---

### Post by Scunnered on 2008-10-10
I have managed to completely mess things up so much so that I am having to use a live DVD to work with.  The boot cycle has totally gone.  I know not what I have done and am messing about to see if I can resolve matters.

If and when I can get things to work properly I will come back to this post.

Meantime my sincere thanks for your kind assistance. 

S

PS  gregorio No she in not called Hilda but Grumpy as she is anoyed at not having her beloved XP.

---

### Post by caljohnsmith on 2008-10-10
If you want help sorting out the mess, how about posting:
```
sudo fdisk -lu

```
And for each drive listed, like sda, sdb, etc, do:
```
sudo dd if=/dev/[COLOR="Blue"]sda[/COLOR] bs=512 count=1 2>/dev/null | strings | grep -i grub
```
And replace sda with each of your drives. If you post the output, we will at least know which drives have Grub installed to the MBR (Master Boot Record), and we can go from there.

---

### Post by Scunnered on 2008-10-11
caljohnsmith

Many thanks for your reply.  I doubt very much if I will be able to provide the information.  

I am currently writing this using Puppy and when I mount my internal HD I can see all the different folders that I expect.   However any attempt to boot from the HD fails. The screen displays DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER.

When I follow this instruction Ubuntu will run from DVD but will not work from the HD.

I am under orders to get a new system for madam and I think that I will see if I can get an older system to work before I drive myself and others into an early grave.

I think that it would be best for all to leave thingsat this stage.

Once again thanks

---

### Post by caljohnsmith on 2008-10-11
Sorry to hear you are having so many difficulties; in the meantime, if you want to try to just get Windows booting again so you don't meet with an early divorce, if you can boot up your Windows Install CD and go to the "recovery console", run:
```
fixmbr
fixboot
chkdsk /r
```
And there's a good chance at least Windows should work from that HDD again.

---

### Post by Scunnered on 2008-10-11
caljohnsmith

Many thanks for your suggestion. I tried your suggestion and it looked like it had worked until I tried to run Windows.  Again system totally rejected me and if I was not so thick skinned I might take it personally.

I took out insurance and have ordered a laptop for madam so all should be well in that department.

I think that I will have a word with the manufacturer on Monday and see if they can solve the problem.

I was not at all bothered if I never loaded Windows again but as the system will not even boot Ubuntu from the HD I hope the manufacturer can assist otherwise it is back to the drawing board.

Once again thanks

---

### Post by caljohnsmith on 2008-10-11
Well if you want any more help recovering Windows, I might be able to help; do you have a Windows Install CD, or maybe just a Manufacturer's OEM Windows CD? It's up to you if you don't want to pursue it further, I just thought I would offer in case you want to give a shot at fixing it yourself before turning to more costly steps. :)

---

### Post by Scunnered on 2008-10-11
caljohnsmith

I have an OEM Windows XP CD but I think that I have screwed things up so bad that that the boot sequence is not being read.  When I followed your suggestion the HD was shown up as something like 0000-0000.

I fully appreciate your desire to assist but what I do not want is to have you end up as frustrated as I am.

I have comitted to the laptop and if I can get this system to boot and run Ubuntu I will be happy.

I retire in 2 weeks and it was my intent that I treat myself to a new system. With the current financial situation as it is it might be my last chance to have any cash to spend ever.

I will be pleased to accept any offer of help if you feel that you can resolve matters.  

My sincere thanks

---

### Post by DemonBob on 2008-10-11
I have ubuntu installed on an external drive, and totally indepent of windows. 

Does your computer support booting from usb?

Heres how i installed it; go through the installation as usually until you get to the last page before the acctual install, click the advanced button, and tell grub to install only to your usb drive. 

I.e my internel hdd showed up as /dev/sda, so i told grub to install to /dev/sdb, then set in my boot order in the bios to boot to usb devices first. You may have to do an sudo fdisk -l from the command line to figure out which disk is what. 

Now if i want to get into windows, i just reboot ubuntu unplug the usb drive, and vola it goes stright into windows, and if i want to boot ubuntu, shutdown windows, plug indrive, and just let it boot.

---

### Post by caljohnsmith on 2008-10-11
Before we try anything further, do you have important data in your Windows partition that you need to save? It sounds like a complete reinstall is going to be necessary, because that may be your only choice if you have an OEM Windows CD; usually those CDs only allow you to install a fresh copy of Windows and not repair an existing one. When you boot your OEM Windows CD, what options does it give you? 

Also, from any of your Live CDs, please post:
```
sudo fdisk -lu
```
So I can see your setup.

---

### Post by Scunnered on 2008-10-11
Caljohnsmith

the following displayed using the sudo fdisk - lu

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

This is working from the Ubunto 8.04 DVD.

As far as Windows is concerned I have given up all hope of anything there so a full install is not a problem.

My OEM disk can offer a recovery OK as I have used this in the past.  When I could not get XP to boot the only way was to use fixmbr and then XP could be loaded.

I will try a full install just now and see what happens and report back.

Once again thanks


DemonBob

If you dont mind I would like to leave your suggestion in abeyance to see if I could in the first instance once again boot the internal hd.  I still like the idea of being able to have a full install on my external drive and will follow through on this once I get the other matter out of the way.

I will get back to you on this and in the meantime my thanks for your interest and assistance.

---

### Post by caljohnsmith on 2008-10-11
OK, about that fdisk command, the "-lu" is a lowercase L and not a one, so please try it again and post the output:
```
sudo fdisk -lu
```

---

### Post by Scunnered on 2008-10-11
Right here goes again, sorry for initial confusion.

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe760e760

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   613361699   306680818+   7  HPFS/NTFS
/dev/sda2       613361700   625137344     5887822+   5  Extended
/dev/sda5       613361763   625137344     5887791   82  Linux swap / Solaris
ubuntu@ubuntu:~$ 

Went back to the OEM disk and tried again. The cycle displayed as follows:

Boot from CD - this offered the Windows setup with the options of full install, Recovers or quiting.

I accepted the full install which then showed

305243 MB disk 0 at Id 0 on Bus 0 on ATAPI [MBR]

C: Partition1 [FAT]  299493 MB < 9 MB free>
E: Partition 2 [Unknown]  5750 MB <5749 MB free>

As partition C was a FAT one refused to load and requested me to delete C. Did so and formatted using quick method.

At the end of the cycle I was asked to reboot.  Removed CD and prayed 

Again received Bisk boot failure message.

Hope this means a lot more to you than me.

---

### Post by caljohnsmith on 2008-10-11
OK, so is the 320 GB sda disk your internal disk I assume? You have an external USB drive somewhere? And you said previously that you were able to successfully boot linux from the USB drive? So do you want to give Windows back the entire internal HDD and put Linux on the USB drive, or do you want to let Windows and linux share the internal drive? 

Either way, I think a prudent next step would be to boot your Ubuntu Live CD, press ALT + F2, and type:
```
gksudo gparted
```
And use the Ubuntu's partition editor to first set up whatever partitions you want on your internal drive, even if it is just one large NTFS partition for Windows. If you need help with that, let me know, but maybe your OEM Windows CD will work better if the partitioning is all in place when you run it.

---

### Post by Scunnered on 2008-10-11
Did as you said and found that there are 3 partitions on the internal drive as follows :

/dev/sda1 a NTFS partition of 292.47 which is flaged as boot
/dev/sda2 an extended partition of 5.62
/dev/sda 5 a Linux Swap of 5.62

When I had the external drive booting and fully working it was totally impossible to get into XP as I kept getting grub errors.  When I used fixmbr to get back into XP then I was unable to access Ubuntu.

It looks to me as I have screwed up the boot sequence that no matter what you try we will still end up with a disk boot failure. 

I really feel that once the laptop comes that I abandon this system to Windows and see if I can get Ubuntu onboard.

Can I suggest we leave things to later in the week when the laptop will be here and I can then remove the internal drive to see what happens then.
I think that if I strip out the internal drive and try things externally that it might just work but until I have something that I can work with I dont want to make any more major errors.

I appreciate all you are trying but I don't want you flogging a dead horse.

---

### Post by caljohnsmith on 2008-10-11
Sure, sounds like a good plan. :)

---

### Post by Scunnered on 2008-10-29
I got the laptop only to find that according to the supplier that there are problems with the kernel and they are not too sure if it will work.  Await further advice on this when 8.10 is finally issued and checked by manufacturer.

So I went back to my desktop and tried a full install by disconnecting the HD and installing on the external usb hd.  Would you believe it somehow or other the internal HD seemed to take the information on board and would not boot. I still kept on getting boot errors.

This left me up the creek without a paddle so I took the desktop to be checked and according to everything the shop tested the HD was OK and that all I needed to do was to do a full install of XP.  Not exactly what I wanted but as the shop felt that things were ok and even better did not charge anything for the messing about I took things at face value.

Having got back home and started things up low and behold Windows would not respond in any way quoting a load of old rubbish but doing nothing.  Here we go again so I used the 8.04 disk and attempted a full install and during the partitioning section of the install the internal drive showed up as having Ubuntu loaded.  Went through the full cycle and rebooted.  Everything worked a treat.   I have had the system off and on 2 or 3 times since and no problems.

I am at a total loss why the information seemed to go on to the internal drive and how the engineer did not find fault with it. I will count my blessings that I have been at least able to fully move away from Doz on the desktop.

I thank everyone who tried to assist and hope for everyones sake that another rogue like this HD does not raise its head.

---

### Post by Scunnered on 2008-11-16
Eventually advised that laptop would not work with 8.10 and have returned it to supplier.  Bought preloaded 8.10 laptop and am now making slow progress with things but at least it is progress

Once again my sincere thanks to all for their guidance and assistance

Scunnered

---

