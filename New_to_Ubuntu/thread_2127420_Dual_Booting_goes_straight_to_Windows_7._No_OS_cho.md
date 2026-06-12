---
title: "Dual Booting goes straight to Windows 7. No OS choice given."
date: 2013-03-20
forum: New to Ubuntu
---

### Post by Tresus on 2013-03-20
I have been reading to see if I may fix the problem by copying another user's advice, but it seems that problems are a bit unique in Linux. I'm a windows user, so using the command line is kind of foreign to me, but I did follow some instructions and have the boot repair report.

[http://paste.ubuntu.com/5630231/](http://paste.ubuntu.com/5630231/)


I duel booted onto the same 2TB HDD, partitioning a section off for the Ubuntu installation which I installed by using a USB flash drive, having to follow the additional instructions of renaming isolinux to syslinus and doing the same to isolinux.cfg and isolinux.bin. Dunno if it means anything to you, but I know it was something I had to do that wasn't automatically done for me, so I figured that's a possible source of user error.

Not sure what other information to give as I can't really think of any more details.


[SOLVED] In the boot menu where I could select my USB to install Ubuntu from,  there was one option that literally had "UEFI:" before the USB stick  name. Don't pick that one. That will apparently tell your PC to NOT put  GRUB in sda. [SOLVED]

---

### Post by fantab on 2013-03-20
I don't know how but I think you have installed GRUB to /dev/sda5, when it should have been installed to /dev/sda. Meaning, Grub should be installed on the HDD (/dev/sda) and not on the partition (/dev/sda5).

The simplest method will be to REINSTALL UBUNTU and when doing so you have choose "Something Else" option to manually control the installation. [Read Here]("https://help.ubuntu.com/community/GraphicalInstall"). And select /dev/sda to install GRUB (be warned that this will overwrite Winodows Boot Loader but that is normal).

Or You can remove Grub and reinstall it using Ubuntu LiveCD/DVD/USB. See [How To]("http://ubuntuforums.org/showthread.php?t=1581099").

---

### Post by Tresus on 2013-03-20
So deleting the windows boot loader wouldn't provide any negative side effects?

---

### Post by fantab on 2013-03-20
NONE. Instead of Windows Boot Loader you will have a far better, GRUB (GRand Unified Bootloader). Windows boot loader will not boot Linux on its own, on the other hand Grub boots both Windows and Linux. 
I hope you have Windows Install Disk? If not, then I suggest that you make a Windows Repair Disc from within Windows-Control Panel before you Overwrite Windows bootloader. This will be helpful, in case, in future you want to remove Ubuntu and only have Windows.

There is, however a way to boot Ubuntu from Windows Boot Loader.. [See here]("http://neosmart.net/wiki/display/EBCD/Ubuntu"). Actually, you can do this considering your situation.
But I recommend that you use GRUB on /dev/sda.

Good Luck...

---

### Post by Mark Phelps on 2013-03-20
> **fantab said:**
> NONE. Instead of Windows Boot Loader you will have a far better, GRUB (GRand Unified Bootloader). Windows boot loader will not boot Linux on its own, on the other hand Grub boots both Windows and Linux.

Unfortunately, this is not true.  The Windows boot loader is REQUIRED in order to boot into Windows.

When you have an entry in the GRUB config file for Windows, all that really does is hand off the boot process to the Windows boot loader in that partition.

---

### Post by fantab on 2013-03-20
@Mark Phelps: We will confuse the OP. We know that GRUB will NOT actually delete the Winodows Boot Loader. I just tried to give the simplest possible answer to a beginner. Perhaps I did not come across as clear as I hoped to. 
What I wanted to tell the OP is that Grub WILL mess up the Windows Boot Loader and if he/she wanted to revert back to Ubuntu he has to FIX Windows first to boot. May be you can put it in better words. Thanks.

---

### Post by Tresus on 2013-03-20
Ok, so to put it simply.

Reinstall Ubuntu.
Install GRUB in sda.
GRUB will take control of boot process.
GRUB can then either boot into Ubuntu or hand control over to Windows boot loader to boot into Win 7.
But in order to go back to JUST Windows 7, I'd have to repair the installation.

So unless I, for some god awful reason, wanted to get rid of Ubuntu later, installing GRUB to sda would be just fine, then?

Sorry for so many questions. I'm just kinda nervous about messing with critical files. :P

---

### Post by oldfred on 2013-03-20
Since you already have Boot-Repair you can just use it to install grub to MBR. It could also reinstall a Windows type boot loader to the MBR if grub does ever have issues.

But a reinstall may still be a good idea. You have a large 2TB drive. There used to be a bug in grub supposedly fixed with either very large / (root) partitions or partition beyond about 500GB on a large drive. With some BIOS we still see the same issue, so cannot guarantee it will boot. Most seem to work but not all. Sometimes just having a smaller / (root) of 25GB and use the rest of the space for /home works also. So if you reinstall you have to use manual install or Something Else to choose partitions and can then create the separte partition for /home.

I generally prefer smaller system partitions and larger data partitions. That way hard drive does not have to jump all over drive to load the most used files. So I also have smaller Windows system partition and separate NTFS data partition for any data you may want to share with Linux.

       Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by Mark Phelps on 2013-03-20
> **Tresus said:**
> ... So unless I, for some god awful reason, wanted to get rid of Ubuntu later, installing GRUB to sda would be just fine, then?

But, to be safe, after you do that, open a terminal in Ubuntu and enter "sudo update-grub".  That will regenerate the GRUB config file and add an entry for Win7.

When you reboot after that, you should be seeing a GRUB menu.

---

### Post by Tresus on 2013-03-21
Well I've attempted to reinstall several times. Installed GRUB to sda, the hard drive. Windows said "nope."

Installed GRUB to sda1, the windows boot partition. Windows said "nope."

This is becoming incredibly frustrating.

Using a UEFI BIOS if that means anything to you.

---

### Post by fantab on 2013-03-21
Post the output from [Boot Info Script]("http://bootinfoscript.sourceforge.net/").

Also read [Here]("https://help.ubuntu.com/community/Boot-Info").

---

### Post by Tresus on 2013-03-21
Here is my new boot info from the boot repair application.
[B][http://paste.ubuntu.com/5634045/](http://paste.ubuntu.com/5634045/)

[/B]I KNOW I told it to install GRUB to sda in the drop down menu on the bottom when I was creating partitions for the Ubuntu OS and swap files.

Hell, I did this twice and told it to install to sda1 that was the same partition as the windows bootloader.

But, for some reason, there it is again, all the way in sda6.

---

### Post by tancrackers on 2013-03-21
Try installing to /dev/sda not /dev/sda1. If you cannot, then you might have problems.
Also, make sure that an Ubuntu partition is actually flagged as bootable.

---

### Post by Tresus on 2013-03-21
Do you mean to mount it as /boot and not /?

Or do you mean to create ANOTHER partition of x size and make it an ext4 /boot partition?

---

### Post by oldfred on 2013-03-21
No.

There are many parts to grub. You just want the boot loader part in the MBR as computers (in BIOS mode) only boot from the MBR. The MBR code then redirects to more boot code. Never install grub to a NTFS partition.
If you want to understand how MBR booting works just review pictures:
       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

But you are showing grub4dos in your Windows partition. Are you trying to use EasyBCD?

You also need to be booting live installer or repair disks in BIOS/legacy/CSM mode, not in UEFI mode. Then run the repairs Boot-Repair suggests, but not if in UEFI mode.

---

### Post by Tresus on 2013-03-21
I'm an idiot. I was hitting F8, going to the boot selection screen. It had UEFI: <My USB Stick> and I was clicking that because it was my very first choice, but there are other choices available.

Also, yes, I attempted EasyBCD at one point, but it didn't work.

---

### Post by Tresus on 2013-03-21
Well that was my problem. Didn't fully understand the implications of UEFI. Booting it regularly solved all my problems and I just made this post on my brand new, WORKING, Ubuntu OS.

Thanks for all your help. :3

Also, for anyone that may not understand what I just did and has the same problem.

In the boot menu where I could select my USB to install Ubuntu from, there was one option that literally had "UEFI:" before the USB stick name. Don't pick that one. That will apparently tell your PC to NOT put GRUB in sda.

---

