---
title: "Dual boot Win/Ubu. GRUB problems?"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by Barkester on 2013-10-19
Decided to put a Windows partition on the computer. Just as a sorta X-box really. Games. I've got 3 40g. partitions, 2 are ext4 and one, on a seperate old 40g. drive was liein' around, I've already made into NTFS believing Windows wouldn't see the others and go on with a clean install for the NTFS. I've both a cd and a bootable image on USB for Windows, but niether even boot up.

   Did alot of googling, or rather Yandexing, and came up with 3 options none of which I'm sure about. Having recently spent 2 days attempting the impossible, I'd love a more educated opinion before choosing.

   My assets are :

   A fairly standard issue Intel quad-core desktop (drivers are easy)
   An iso of ubuntu 12.somethin'
   Windows XP SP3 image with drivers
   An 8 gig thumb drive (NTFS with Windows image mounted as bootable) and lots of space.
   A half trig portable with 4 ext4 partitions, one empty.
   An over-priced third-world net connection.

   Most assert windows MUST be #1 except for one post. It stated that the GRUB can be later changed and Ubuntu brought back to life. Might be quite a job tho' as it didn't sound cut and paste. 

   Considering cloning the whole Ubuntu drive to my portable, installing Windows, and then just cloning back. 

   Probly my favorite, go hardware, remove the 80gig drive entirely, install Windows, put the drive back.

   All hit the wall at Window installation tho'. Even if I do remove the drive, the Windows won't boot, so I gotta know how to do something in BIOS besides boot order. This GRUB thing I suppose.

   Ideally, I'd like to keep my 13.04 with all my programs and deletions. Sure looks possible, but, as I said, just went thru' that so, is it possible? I'll use the 12. if need be. Even then its a moot point 'till Windows can boot.

   Are there apps that might make changing the GRUB easier so XP will boot? How badly can I screw up? Is it true that if I did remove the drive, when I put it back, Windows XP would  have problems with the addition? 

   Thanks for any feedback. May you all have many children and never have to go thru' this.

---

### Post by oldfred on 2013-10-19
I am not sure what drives you have?
I prefer to have Windows on one drive and Ubuntu on every other drive.

Windows has to have a primary (sda1 thru sda4) partition formatted NTFS with the boot flag to install. Have BIOS set to boot from that drive as default as that is the drive Windows will install and install its boot loaders. Boot Flash drive or CD to install.

Windows will install its boot loader to MBR, so it that drive is where you have your current grub2 boot loader you will have to reinstall grub2's boot loader to MBR.
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by Barkester on 2013-10-20
Thanks Oldfred. Just flagged my NTFS as bootable. Now I'll reboot and see what happens. Hopefull, it sees the Windows image this time.

   Both the 40g drive and the thumb with Windows are bootable. Think it might be the fact the 40G is listed as sda6. Think I'll havta use a cloning app, run ubuntu from my portable using a clone to delete all and change all to NTFS. Remove the portable, install Windows. Then I'll change the other drives back to ext4 and clone it back again using the clone and then use gparted to make the drives bootable if the setting doesn't move with the clone. I've accepted Windows will go first now. Justa matter of keeping all my old settings.

   Your tip that Windowss requires sda 1-4 is appreciated. Now I understand and by knowing what I can't do. I can now go to options that work. 

   I'll need to search about cloning Ubuntu and find that app again first. Thanks for the help.

---

