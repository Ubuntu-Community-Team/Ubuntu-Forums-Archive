---
title: "Successful Dual Boot with Lenovo Y500"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by pc PIL0T on 2013-03-19
The goal is to dual boot with said machine *without changing the HDD/win 8 partition*.
  There is a couple reasons for this : 
   1) I have to keep win 8 for work
   2) I'm not capable yet to mess with the partitions that hold win 8 
  Thus I don't want to touch it and mess with the HDD and just work around it. 

What I have done so far: 
 
  I first started here, [Lenovo Ideapad Y500 LiveUSB Problem]("http://ubuntuforums.org/showthread.php?t=2095063&page=2"), to actually boot the gui install. After that, I have been following [[SIZE=5][SIZE=2]HOW TO Avoid Wubi & Install Ubuntu on USB Drive[/SIZE][/SIZE]]("http://ubuntuforums.org/showthread.php?t=1650699") to do dual boot without touching the HDD. After getting to step involving GParted, around step 15 is where I stall and can't follow through. The usb had a key icon on it, which means it's locked and the option I have is to unmount which I don't want to do. Then when I go to check everything else out, it turned to a black screen then grub menu appeared and then from there i was completely lost. 

  Specifics of the process that i've done already : backed up win 8 to a image,  disabled secure boot, enabled legacy to boot gui install, changed the bios to boot from usb first, got to gui install, gparted to create partitions, got stuck on the grub menu

   How should i tackle this? Is there no other way but to shrink the win 8 partition?

---

### Post by Mark Phelps on 2013-03-19
First of all, do NOT use Gparted to shrink the Win8 OS partition. Doing so risks corrupting the filesystem and rendering Win8 unbootable. Use the Win8 Disk Management tool to do the shrinkage.  And, when done, reboot into Win8 a couple of times to let it do filesystem adjustments.  Wubi doesn't  create partitions, so if you want to use Wubi, then you won't have to mess around with partitioning at all.

Second thing to do, after that, is to download and install the free version of Macrium Reflect.  Once that is installed, image off the Win8 OS to an external drive or USB stick.  NOW, you have a backup that you can restore if anything goes terribly wrong with Win8.

Third, use the Win8 option to create a Repair disk.  I don't know if it will also work with USB, but if it does, you should choose that option.  This allows you to repair any Win8 boot loader problems without having to boot into Win8.

---

### Post by oldfred on 2013-03-20
A Windows 8 repair is different to support the UEFI.
 Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

I do not think I have seen an install of Ubuntu to flash drive with UEFI boot. And since Windows is UEFI, it would be better to install to flash drive in UEFI mode. 
I have used gpt partitioning on a flash drive so I know that works without any issue.
It may be just install to the flash drive just like any install to a second drive, and like any install to a second drive you want to be sure to install grub to the flash drive's efi partition not the internal drive's efi partition. You may have to create partitions in advance or it may automatically use the existing efi on the hard drive.

      
 UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by pc PIL0T on 2013-03-20
@ mark phelps : this was actually part of the guides that i've followed in , [SIZE=2]so no problems there. Thanks for the heads up [SIZE=2]about the gparted tip on win[SIZE=2]8 partition[SIZE=2], [SIZE=2]will avoid doing that :).[/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]
@oldfred:  If I'm following you correctly, the flash drive will act as a second  drive for the instructions that are linked? would there be a particular  reason why the liveusb would be locked from partitioning?

---

### Post by oldfred on 2013-03-20
You cannot change partitions on the flash drive you boot from.

But you should not have any issue, using gparted on another flash drive. That was how I installed the first couple of times. Although now I directly boot ISO with grub2 from hard drive to install to another drive whether hard drive or flash drive.

But I have not tried a UEFI install and the few we have seen, seem to have issues with where the efi partition is or which drive is used. One install looked like it never created an efi partition on the second drive but just used the one on the first drive. If you partition in advance, use manual install or Something else you should get the option on where to install grub2's boot loader. If not you still need the efi partition on the flash drive to copy/install grub2's efi boot files into.

---

### Post by pc PIL0T on 2013-03-24
I'm able to boot from usb but the brightness is hurting my eyes. I'm confused on the nvidiabl process explained [here]("http://ubuntuforums.org/showthread.php?t=2095063&p=12434372#post12434372") in the Lenovo ideapad, how do i find the correct deb file and load it in the module?

---

