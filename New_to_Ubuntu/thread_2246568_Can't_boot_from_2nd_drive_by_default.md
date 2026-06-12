---
title: "Can't boot from 2nd drive by default"
date: 2014-10-01
forum: New to Ubuntu
---

### Post by c-cubed on 2014-10-01
**My Problem: Can't boot from second drive by default**
 I have an HP Pavillion dv7 1451NR, product number NV204UA#ABA.
 I have two drives installed.
 I have Windows 7 64-bit installed on drive 0 and Ubuntu 32-bit installed on drive 1.
 

 I can successfully boot either operating system by the following procedure:
 
[LIST=1]
[*]Power up 
[*]Press escape-key  to get to BIOS 
[*]Press F9-key  to get to boot menu 
[*]Boot menu shows two drives named     “Internal Hard Drive” 
[*]If I select the first entry named     “Internal Hard Drive” I boot to Windows 7. 
[*]If I select the 2nd entry named     “Internal Hard Drive” I boot to Ubuntu. 
[/LIST]
 

 When I power up if I do NOT press escape, the machine boots to Windows after the timeout.
 **My Problem: I want to boot to Ubuntu by default.**
 

  I've checked the HP bios and I don't believe there is any way to do this by changing the boot priority in BIOS. The BIOS doesn't seem to differentiate between the two hard drives. I only has one entry for “Internal Hard Drive”.
  

  I believe an approach that should work is:
 
[LIST=1]
[*]     Use bcdedit or easybcd to create a BCD record that points to GRUB. 
[*]     Create a GRUB config file that “chain” loads Ubuntu. 
[*]     Use bcdedit to move the GRUB entry as the default. 
[/LIST]
  I've tried various permutations but can't get it to work.
  

  **Question:** Should my idea work?
  **Detailed question:** How do I discover where the initial boot image is for GRUB? I know I need the a copy of sector 0 from the drive and partition that Ubuntu and GRUB are on. From Ubuntu I have tried permutations of “[FONT=Courier New][SIZE=1]dd if=/dev/sdxx of=/NST/grubsdXX.bin bs=512 count=1” [/SIZE][/FONT][FONT=Liberation Serif][SIZE=3]to generate the boot image. Non have worked.[/SIZE][/FONT]
 [FONT=Liberation Serif][SIZE=3]**Detailed question: **What exactly should the BCD record look like? What commands do I use to create it. I've tried various permutations of [/SIZE][/FONT] 
  “[FONT=Liberation Serif][SIZE=3][FONT=Courier New][SIZE=1]bcdedit /create /d “GRUB” /application BOOTSECTOR[/SIZE][/FONT][/SIZE][/FONT]
   [FONT=Liberation Serif][SIZE=3][FONT=Courier New][SIZE=1]bcdedit /set {60e1c218-a9b3-11e0-89b8-00235abb6d44} device partition=C:[/SIZE][/FONT][/SIZE][/FONT]
  [FONT=Courier New][SIZE=1]bcdedit /set {60e1c218-a9b3-11e0-89b8-00235abb6d44} path \nst\grubsdXX.bin[/SIZE][/FONT]
   [FONT=Courier New][SIZE=1]bcdedit /displayorder {60e1c218-a9b3-11e0-89b8-00235abb6d44} /addlast”[/SIZE][/FONT]
  [FONT=Liberation Serif][SIZE=3]I think I'm close, but can't get it to work. My guess is either I'm not getting the right sector 0 image into grubsdXX.bin or I'm not setting the “partition” or path correctly or possibly I need to install GRUB on drive 0.[/SIZE][/FONT]
  

  [FONT=Liberation Serif][SIZE=3]Any help would be appreciated. Thanks in advance.[/SIZE][/FONT]

---

### Post by grahammechanical on 2014-10-01
A couple of points. It is possible to install grub onto drive 0 and that would remove the Windows boot loader from that drive. Which in a way defeats one of the reasons for having Windows and Ubuntu on their own hard drives.

It should also be possible to change or swap over the SATA ports that the hard drives are connected to on the motherboard. That might just change the listing of the hard drives in the BIOS.

Ubuntu and Grub use a combination of alpha-numeric characters to uniquely identify each partition instead of hd0 or hd1 or even sda or sdb. It is called Universally Unique Identifier (UUID). So, it should not mess up the Grub menu that gives you the choice to load either Ubuntu or Windows.

[http://en.wikipedia.org/wiki/Universally_unique_identifier](http://en.wikipedia.org/wiki/Universally_unique_identifier)

I cannot advise on BCD but you will find the Grub configuration file at /boot/grub/grub.cfg. That should give you the information that you need.

Regards.

---

### Post by oldfred on 2014-10-01
Are you sure if you go to hard disk in BIOS it does not have a sub-menu so you can choose each drive? 
If not a sub-menu some BIOS have a separate set of entries for device order which may even be on a different page.

Note that PBR or partition boot sector and MBR or master boot record are the same structure.
I do not necessarily suggest any of these as I prefer grub and most systems can boot with grub.

       Edit BCD to boot grub. copy file to Windows system folder
[http://www.boyans.net/DualBootWindows7andLinuxOrUnix.html](http://www.boyans.net/DualBootWindows7andLinuxOrUnix.html)
You can use the file (from "/boot/grub/" directory)
- boot.img (GRUB2) or - stage1 (GRUB legacy)


 [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by c-cubed on 2014-10-02
Thanks to all who responded. They were good solutions.
1) Yes I could replace Windows loader with Grub. That would work, but I didn't want to do that. I do extensive development in both Windows and Linux and I wanted prestine versions of each.
2) Yes I could switch the drives from one bay to the other. What a pain. Tools and screws. I'm a software kinda guy.
3) And finally yes it would be very very nice if HP would upgrade their BIOS. It doesn't allow selecting a specific drive. In fact
    on many models of HP laptop it doesn't support booting from the second drive at all. Sigh:-({|=

I solved my problem using easybcd and Neogrub. See the attachment for details.

---

### Post by oldfred on 2014-10-02
Glad you got it working.

Just for documentation, your instructions mention menu.lst. That is from grub legacy and default install now uses grub2 which uses grub.cfg and numbers partitions differently.

---

### Post by c-cubed on 2014-10-03
Thanks moderator.
You are correct that my instructions are for grub legacy. Because I was starting in Windows 7. The loader reading the menu was Neogrub which is apparently of grub legacy vintage. Not sure on that.
[B]
One refinement:[/B] I discovered how to avoid having to edit the menu item every time you update the Ubuntu kernel. When it is updated Ubuntu creates a link in the root of the root partition that points to the latest kernel and one that points the latest initrd. Therefore if you replace the reference to a specific kernel (example: /boot/vmlinuz-3.2.0-48-gereic-pae) and initrd (example: /boot/initrd.img-3.2.0-48-generic-pae) with "/vmlinuz" and "/initrd.img". Your menu will always boot the latest installed Ubuntu.:p

---

