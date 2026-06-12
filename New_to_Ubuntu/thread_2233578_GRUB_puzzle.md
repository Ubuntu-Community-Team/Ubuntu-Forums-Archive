---
title: "GRUB puzzle"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by sea_dawg on 2014-07-09
Is GRUB installed when installingUbuntu as the only OS?  When HDDs are moved how does GRUB keep things straight?


This is the tale of two hard drives,or, adventures with GRUB.  Not so much a cry for help as a quest forunderstanding.  


I had installed Precise as the only OSon a Toshiba laptop.  When the graphics controller failed I purchaseda used Dell with Win 7.   I wanted to set up the Dell as a dual bootWin 7 and Ubuntu.  My plan seemed fairly straight forward:


1 – Attach the ex-Toshiba drive viaSATA to USB adapter
2 – Start the Dell with a live USB
3 – Install Precise as a dual boot
4 – Move data from the ex-Toshiba tothe new Precise EXT4 partition. (Yes, I have been lazy about backups)


Here's where it got interesting.  WhenI booted the live USB GRUB came up !?!  With menu entries for Win 7and Ubuntu.  Where in the world did that come from?  Spontaneousgeneration?  Divine intervention? 

GNU GRUB version 1.99-21ubuntu3.15


GRUB's menu choices were
Ubuntu
Ubuntu recovery
Previous Linux
Memory test
Memory test
Windows 7 (loader)(on /dev/sda1)


When I selected Ubuntu from the GRUBmenu I didn't get the live session. I got the old Precise setupexactly as I had last used it!


When I selected Windows from the GRUBmenu I got Windows.


Ok.... Hmmm.... I thought I have my oldPrecise installation just the way I want it.  Why not take advantageand put the ex-Toshiba in the optical drive bay?  


I did just that and set the BIOS bootsequence with the Modular Bay HDD at the top of the list and theInternal HDD at the bottom.  Started the machine and it booted to Win7, on the internal HDD.  Probably a BIOS issue.  


I was able to boot Precise from theex-Toshiba HDD, sdb, in the optical bay by interrupting the bootsequence and selecting “Modular Bay HDD”


At this point Gparted shows
sda, NTFS, bootable, is the Dell's Win7 HDD
sdb, EXT4, bootable, is theex-Toshiba's HDD with Precise installed.


Now I have a crude dual boot,requiring interrupting the boot sequence to run Ubuntu.


I next swapped HDD positions.  Puttingthe ex-Toshiba HDD wint Precise in the primary HDD bay and the DellHDD with Win 7 in the optical bay.  
When I start the machine GRUB comes up. Windows loader still shows as /dev/sda1.  


Gparted indicates 
sda, EXT4, Bootable  is the ex-ToshibaHDD with has Precise installed.  
sdb, NTFS, Bootable  is the Dell HDDwith has Win 7.  

GRUB's menu is unchanged.  Win 7 still listed ad being on sda1


However, selecting the GRUB entry forWindows loads and runs Windows.  Selecting the Ubuntu entry loads andruns Precise.


So now I have two mysteries.  
1 – How did GRUB get installed?  
2 – Why is GRUB able to corretly bootPrecise and Win 7 when the its menus show it doesn't know where theOSs are installed?


Is there any potential problem withleaving things this way?  Both HDDs are bootable.  Both OS load andrun fine.  


I should probably update GRUB?


Thank you.

---

### Post by yancek on 2014-07-09
> Is GRUB installed when installingUbuntu as the only OS?

Yes.  Otherwise, it would not boot.

> When HDDs are moved how does GRUB keep things straight?

If you make that type of change you need to update-grub:  sudo update-grub

>  WhenI booted the live USB GRUB came up !

What method did you use to create the Live USB?  Generally, syslinux is used not Grub so you should not have seen Grub unless you forgot to set the flash drive to first boot priority in the BIOS.  Running update-grub might get the entries correct or might not.  Since everything is booting there isn't really any need to change it but I would suggest you make notes of the situation and save the file somewhere in case you have problems in the future.  Also, what shows in the boot menu doesn't really mean anything.  You can what that is by looking at the menuentry line in the grub.cfg file.  There should be an entry immediately after the word:  menuentry in single or double quotes which is what shows on the menu at boot but doesn't affect what boots.

---

### Post by oldfred on 2014-07-09
With respect to yancek's suggestion of documenting boot, I use bootinfoscript or Boot-Repair's BootInfo report which also actually runs bootinfoscript and adds some extra data to help debug install issues.
With multiple drives and/or multiple installs it makes it a lot easier to have the full script to know what is where, sizes and other details.

       boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

      
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sea_dawg on 2014-07-09
Thank you for the reply.

I used YUMI from Pendrivelinux to create the live USB.  Yes, USB was set to first priority in BIOS when GRUB came up with the ex-Toshiba HDD connected via SATA to USB.  I like to have a USB stick with Ubuntu, Puppy and CloneZilla as a fall back in the event the installed OS has problems.

I'm still puzzled how GRUB "knew" about the locations of Win 7 and Precise as I moved HDDS about.   Especially Win 7 because the ex_Toshiba HDD had never had a Win 7 install.   In it's previous live before being a Precise only install it was a Win Vista install.  

At this point it is more curiosity than anything.  sda with Precise is very old.  I will be replacing it with a new HDD and doing a proper dual boot install.  What do you think about leaving sdb with Win 7 and bootable?

---

### Post by oldfred on 2014-07-09
I prefer to keep Windows on a Windows drive and Linux on a Linux drive if you have two or more drives.

But Windows will not boot from an external USB drive.
As long as it sees it as an internal drive it should be ok. 

There must have been a sudo update-grub or a new kernel installed that ran the grub update and found the Windows install.

---

### Post by grahammechanical on 2014-07-09
Do you want my guess? Did you install precise to the USB stick or burn the Ubuntu ISO image to the USB stick? If you installed Ubuntu to the USB then Grub would have been installed somewhere. The installer defaults to installing Grub into sda. So, it is my guess that all the OSes on all the hard drives were detected and put into the Grub menu.

We might think of drives as sda or sdb, etc., but when the Grub configuration file is written hard disks and partitions are not referenced by sda or sdb but by a sequence of numbers and letters which is called a Universally Unique Identifier (UUID). So, it does not matter if we change the ports that we connect hard drives to so that sda and sdb get swapped, the UUID stays the same and Grub is able to find the right OS to load.

A small quote from /boot/grub/grub.cfg, which is what the Grub menu references on my machine

> linux    /boot/vmlinuz-3.15.0-6-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff

Do you see the UUID? So, even if I swap drives around that UUID will tell Grub where the Linux image (vmlinuz-3.15.0-6-generic) is so that it can be loaded.

Regards.

---

### Post by yancek on 2014-07-09
I would concur with the suggestion by oldfred of keeping an up to date copy of the bootinfoscript/boot repair script, particularly useful if you are testing different systems.

---

### Post by PondPuppy on 2014-07-09
+1 to grahammechanical in my book. I believe the OP used YUMI, and that's an install. Incidentally, the YUMI page cautions against using a YUMI-created USB stick as install medium. If you wish to install to the hard drive, you might be better off to burn the ISO to a DVD and use that for the install instead.

---

### Post by sea_dawg on 2014-07-09
Thank you all for you responses and help.  My understanding of GRUB and it's HDD identification is stronger now, though I still have quite a way to go.

To briefly respond to all of you.

I agree Windows on it's own NTFS drive, Ubuntu on it's own EXT 4 drive. 
Once I have the system the way I want it I will run [COLOR=#000000]bootinfoscript or Boot-Repair's BootInfo report and keep the output for future debugging.[/COLOR]
[COLOR=#000000]The explanation of UUID is most helpful in understanding what is going on. [/COLOR]
[COLOR=#000000]Learning that YUMI is an install helps clear the fog.[/COLOR]
[COLOR=#000000]In future I will install Ubuntu to HDD from ISO burned to CD when possible as opposed to install from USB stick.
[/COLOR]
I'll mark the thread as solved.  But I may be back with more questions.

---

