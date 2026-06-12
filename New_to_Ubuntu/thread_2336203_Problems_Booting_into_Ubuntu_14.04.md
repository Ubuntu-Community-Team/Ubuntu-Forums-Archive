---
title: "Problems Booting into Ubuntu 14.04"
date: 2016-09-05
forum: New to Ubuntu
---

### Post by jdo300 on 2016-09-05
Hello,

I have a copy of Ubuntu 14.04 (desktop version) running on an old IBM HS22 Blade Server. Another colleague configured the server to be a master node of an MPICH cluster that we setup for running simulation work, and up until recently it appeared to be working fine. One day, he rebooted the server and it refused to boot back into the desktop. Booting into the system through GRUB's advanced options menu showed that the system was getting stuck on the line that says, "Loading initial ramdisk ..." but no errors reported afterward.

I did some research online and came across this post here:
[https://ubuntuforums.org/showthread.php?t=1756703](https://ubuntuforums.org/showthread.php?t=1756703)

and I tried to fix it by booting into a Live CD to update the initrd.img file (thinking that it was somehow corrupted), according to the instructions in this article here: [http://linoxide.com/linux-how-to/fixing-broken-initrd-image-linux/](http://linoxide.com/linux-how-to/fixing-broken-initrd-image-linux/)

but with no luck either (behavior remains the same). I should not though, that if I boot into recovery mode, that it does make it past the loading ramdisk line and go into the command prompt.

My most recent attempt was to download and run the Boot-Repair utility to fix the problem. I installed and executed the program successfully using the Live CD, but again, no change in behavior after rebooting. Below is a link to the paste-bin dump from the computer:

[http://paste.ubuntu.com/23139212/](http://paste.ubuntu.com/23139212/)

At this point, I'm really not sure what else to try. I want to reinstall everyting as a last resort, as I would have to do a lot of reconfiguration to get the cluster up and running again. Any advice is greatly appreciated.

Thank you,
Jason O

---

### Post by jdo300 on 2016-09-05
Ok, I'm still investigating more and found, what may be another clue. I read that the GRUB bootloader is supposed to display a recovery menu with options to select when you boot into the recover mode for the OS. In my case, however, GRUB never displays the menu, but rather drops directly to a command prompt. I attached a screenshot of what is displaying (looks like more problems), but not sure what they mean:

[ATTACH=CONFIG]270993[/ATTACH]

---

### Post by mook765 on 2016-09-06
> Alert! /dev/disk/by-UUID/77fb67af-b700-4847-a475-bceb2eae6140 does not exist.
The screenshot shows that the system cannot find your root-partition.
Check the UUID for all devices with```
sudo blkid
```
Look for UUID of sdb3.
If sdb3 has not the UUID 77fb67af-b700-4847-a475-bceb2eae6140 you are hopefully able to reset UUID with
```
sudo tune2fs /dev/sdb3 -U 77fb67af-b700-4847-a475-bceb2eae6140
```
I hope this helps, I have never tried that, in doubt please refer to:
```
man tune2fs
```
Take a look into your bootinfo-summary as well, there is plenty of information...
***
The other way around would be to edit the file /etc/fstab on sdb3...

---

### Post by yancek on 2016-09-06
The UUID shown in the last attachment you posted with the UUID is also the UUID in the  grub.cfg file so if that is not the actual UUID of sdb3 that would be the problem.  A UUID does not geneerally change unless partitions are modified in some way.  Another problem I see is that you are using GPT/UEFI yet you have Grub boot code in the MBR.  That should not happen and generally leads to problems booting if you mix these two options.  The boot repair output you posted shows that was not done so maybe it happened with an earlier attempt with boot repair?

Running sudo blkid should show you the UUID for sdb3.

---

### Post by oldfred on 2016-09-06
Part of issues is that system is sdb. And you show a floppy drive as sda.
In UEFI mode, grub only installs to the ESP on sda. And you show /EFI/ubuntu folder, so it must have installed correctly in beginning. 
Did you add a new floppy drive? 

I have had issues with both an older BIOS system and a newer UEFI system with SATA drives/ports where I did not have all hard drives in first SATA ports starting at SATA0. And have other drives like DVD or floppy after hard drives.

---

### Post by jdo300 on 2016-09-10
> **mook765 said:**
> The screenshot shows that the system cannot find your root-partition.
Check the UUID for all devices with```
sudo blkid
```
Look for UUID of sdb3.
If sdb3 has not the UUID 77fb67af-b700-4847-a475-bceb2eae6140 you are hopefully able to reset UUID with
```
sudo tune2fs /dev/sdb3 -U 77fb67af-b700-4847-a475-bceb2eae6140
```
I hope this helps, I have never tried that, in doubt please refer to:
```
man tune2fs
```
Take a look into your bootinfo-summary as well, there is plenty of information...
***
The other way around would be to edit the file /etc/fstab on sdb3...

Hello mook765,

Thank you for the information. I booted into the recovery disk to check the UUIDs and the below is what was returned:

[ATTACH=CONFIG]271067[/ATTACH]

It looks like the UUID for sdb3 is correct, so I have no idea why it is having a problem with it.

As for the bootinfo-summary, I did generate one using the Boot repair utility, which is here:

[http://paste.ubuntu.com/23139212/](http://paste.ubuntu.com/23139212/)

[QUOTE=yancek]The UUID shown in the last attachment you posted with the UUID is also the UUID in the  grub.cfg file so if that is not the actual UUID of sdb3 that would be the problem.  A UUID does not geneerally change unless partitions are modified in some way.  Another problem I see is that you are using GPT/UEFI yet you have Grub boot code in the MBR.  That should not happen and generally leads to problems booting if you mix these two options.  The boot repair output you posted shows that was not done so maybe it happened with an earlier attempt with boot repair?

Running sudo blkid should show you the UUID for sdb3.[/QUOTE]

Hi Yancek, I'm glad you mentioned the Grub config files. I posted screenshots of both the standard and recovery mode config files here in case there is anything weird going on there (I never edited the files directly myself):

[ATTACH=CONFIG]271065[/ATTACH][ATTACH=CONFIG]271066[/ATTACH]

As for the GPT/UEFI thing, I am not sure but I did run the Boot Repair utility to have it try to fix any problems with Grub, so maybe it changed something here?

[QUOTE=oldfred]Part of issues is that system is sdb. And you show a floppy drive as sda.
 In UEFI mode, grub only installs to the ESP on sda. And you show /EFI/ubuntu folder, so it must have installed correctly in beginning. 
 Did you add a new floppy drive? 

 I have had issues with both an older BIOS system and a newer UEFI system with SATA drives/ports where I did not have all hard drives in first SATA ports starting at SATA0. And have other drives like DVD or floppy after hard drives.[/QUOTE]

We did not make any hardware changes to the system (e.g. adding or removing any drives) since we originally installed the OS on the system. We do have a floppy drive on the server though. So what do you mean that it is a problem that it is sdb instead of sda?

I'm not sure what to try next from here. Any ideas?

Thank you all :-).

- Jason O

---

### Post by oldfred on 2016-09-10
To make sure system works in future, I would move SSD to SATA0 and floppy some port higher. But that may break booting. Grub is supposed to use UUID and should based on find, but hint and device entries all show hd1 which will get changed to hd0 on sudo update-grub once booted.

It also looks like you do not have the newest 14.04 that is supported for 5 years. You have to either have the original 14.04, or if you have installed the enablement stack which includes a newer kernel to work with newer hardware, you have to update enablement stack to have same kernel as 16.04.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)
You have and will need to update:
 Ubuntu 14.04.3 -> kernel 3.19 (from Ubuntu 15.04)

---

### Post by jdo300 on 2016-09-29
Hello Everyone,

Here's an update on my troubleshooting progress.  As I mentioned in my previous post, I wiped and reinstalled Ubuntu on  the SSD and got the same errors as mentioned above. Well, I later  realized that when I was having the Live CD reinstall the OS, it wasn't  wiping the partitions and starting fresh (or at least it didn't appear  to be). So I went through the manual install options and re-partitioned  the drive myself to ensure that none of the old settings remained.

I  deleted the old partitions and created an efi, swap, and root  partition. The efi was set to 100MB in size, the swap set to 32GB, (the  server computer has 48GB of RAM), and the remainder of the 250GB drive  went to the root partition. Then I let the installation complete as  normal and rebooted the machine.

This time, the machine jept  rebooting again and again, so I went into the bios, selected the Boot  manager, and added the HDD with a reference to grubx64.efi inside the  efi partition. Now, when I reboot, the computer goes in, but this time,  rather than rebooting again and again, it drops to this prompt:

[FONT=courier new]BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash) Enter 'help' for a list of built-in commands.

(initramfs)[/FONT]

Now, I found that if I type in [FONT=courier new]exit[/FONT], then it loads up Ubuntu and everything seems to work fine after this. But I am rather perplexed as to why this BusyBox prompt keeps coming up every time I reboot the machine. Could there be a boot script somewhere that is missing some information? Or could this be related to a BIOS setting?

Thanks,

---

### Post by oldfred on 2016-09-29
Is UEFI set to boot in UEFI mode, not BIOS/CSM/legacy? And is grubx64.efi first entry in UEFI.
Post this:
sudo efibootmgr -v

And is Secure Boot off. Do not think it would boot at all if secure boot is one.

I normally boot shimx64.efi, even though I have Secure boot off, but grubx64.efi should work, but only when Secure Boot is off in UEFI.

---

### Post by jdo300 on 2016-10-11
Hello Everyone,

For those who may have [FONT=verdana]had [/FONT]this same problem  before, I finally found the solution and it had nothing to do with the  partition ty[SIZE=2][FONT=verdana]pe, bootloader type, or issues with mis-installation of  grub. [/FONT][/SIZE][COLOR=#000000][FONT=Cambria][SIZE=2][FONT=verdana]The  root issue was that the SCSI controller, was taking longer than usual  to initialize during the boot sequence, tricking GRUB into thinking that  the SSD was non-existant/non-booting, and thus dropping to the BusyBox  prompt. All I had to do to solve this problem was change the [SIZE=3][FONT=courier new]rootdelay[/FONT][/SIZE] parameter.

[LIST=1]
[*]When you reach the BusyBox command prompt, simply type [SIZE=3][FONT=courier new]exit[/FONT][/SIZE] to boot into the Ubuntu login screen. 
[*]Once logged in, open a terminal and type: [SIZE=3][FONT=courier new]sudo gedit /etc/default/grub[/FONT][/SIZE] 
[*]In GEdit, look for the line that says, [SIZE=3][FONT=courier new]GRUB_CMDLINE_LINUX=" "[/FONT][/SIZE], (This defines command line parameters to be passed into the Linux kernel), and modify it to read, [SIZE=3][FONT=courier new]GRUB_CMDLINE_LINUX="rootdelay=90"[/FONT][/SIZE] (This forces the bootloader to give the SCSI controller more time to finish initializing before proceeding). 
[*]Save and exit out of GEdit, and type in the following line to update the GRUB config file:
[SIZE=3][FONT=courier new]sudo update-grub[/FONT][/SIZE] 
[*]All Done! Reboot and enjoy! 
[/LIST]
[/FONT][/SIZE][/FONT][/COLOR] - Jason O

---

