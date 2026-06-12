---
title: "Can not access anything from my cd drive."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Jerrick on 2008-09-05
I jsut installed ubuntu as it was my only bootable cd with me. I wanted to go from ubuntu, to XP. Figured Id just pop in the XP cd (Found it about 20mins ago) and it would load up and I could take it from there.

But thats not working. When I put in the XP disk, nothing happens, so i thought my XP disk was getting old, so i tried my backup Xp disk, and that didnt work, nor do my dvds, audio, or any other cds I have.

Im completely new to ubuntu and google searching this problem made my stomach sink, cause I had no clue what was being talked about and that just confused me even more.

Can anyone walk me through this? IThe sooner I can get back to XP, the better.

Oh, because Xp is bootable, i tried putting that in and turning on my comp, and I get the option to boot from the cd, and I let it go, but instead of bringing up the XP options, Ubuntu loads. That also happens when I try loading my Win98 disk, and Nortons bootdisk.

Hopefully, tomorrow I can get my hands on a floppy drive and find a boot diskette, load 98se and get to xp from there.

Thanks for any help.

---

### Post by Rocket2DMn on 2008-09-05
You need to select to boot from the XP disc.  This either requires you to get the boot menu (which it seems like you had), or to change your BIOS boot sequence to look at the cd drive before the hard drive.  Once you reboot the computer and load from the XP disc, you can go ahead and install over Ubuntu.  Please make sure you have any important information backed up first, since re-installing any OS over an existing drive will wipe out the information on the drive.

---

### Post by gvartser on 2008-09-05
Ubuntu is NOT reversible. ;)

/g

---

### Post by maniheer on 2008-09-05
Did u press enter when it said Boot From CD?

---

### Post by Jerrick on 2008-09-05
> **Rocket2DMn said:**
> You need to select to boot from the XP disc.  This either requires you to get the boot menu (which it seems like you had), or to change your BIOS boot sequence to look at the cd drive before the hard drive.  Once you reboot the computer and load from the XP disc, you can go ahead and install over Ubuntu.  Please make sure you have any important information backed up first, since re-installing any OS over an existing drive will wipe out the information on the drive.

Well, ive gone into the boot order (f12 on a gigabyte ep45 board) and selected to boot from the cd, but it would just go to ubuntu. In the bios ive even go as far as setting all three main boot options to cd-rom. And yes, I did hit enter when it would ask to boot from cd.

This morning showed some improvement with me being able to boot from a cd, so thats good, and once I get home from work, I should be able to have everything up in running in an hour.

Lol, im not saying ubuntu is bad. I quite like it, but I dont intend on using it on this machine.;-)

EDIT: Oh, can anyone help me with installing WINE? Thats all I need and ill be set.

---

### Post by Rocket2DMn on 2008-09-05
Let us know if you are successful with booting from the CD.  If you can't boot from the CD that is a hardware or BIOS problem since it is looked at before you ever get to GRUB or anything on the hard disk.

For wine, you should start a new thread in the wine forum - [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
And check out [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Jerrick on 2008-09-05
Well, I can boot from my windows98 cd, but not my Xp. But 98 doesnt work with my system because of "Insufficient memory" even though I have 4gigs ddr2 ram, plenty of harddrive space, and a quadcore processor. Guess old stuff cant work on everything thats new...

And XP cant boot in DOS mode. haha. Sucky.

Thanks for the link. Im getting it all working out with wine. Once I get this computer setup to how I like it, Ill get one of my other 4 comps running on ubuntu. :D

---

### Post by paul_mcl on 2008-09-05
> When I put in the XP disk, nothing happens
No automount? No problem.

mkdir -p /mnt/xpcd
fdisk -l
(find your device and partition no., for example, /dev/sdb1)
mount -o iocharset=utf8,umask=000 -t vfat /dev/sdb1 /mnt/xpcd
????
PROFIT!

---

### Post by Rocket2DMn on 2008-09-05
If you can boot from the 98 cd but not from the XP cd, it stands to reason that your XP disc is damaged in someway, so you should get your hands on a new one.

---

### Post by halitech on 2008-09-05
> **Jerrick said:**
> I jsut installed ubuntu as it was my only bootable cd with me. I wanted to go from ubuntu, to XP. Figured Id just pop in the XP cd (Found it about 20mins ago) and it would load up and I could take it from there.

But thats not working. When I put in the XP disk, nothing happens, so i thought my XP disk was getting old, so i tried my backup Xp disk, and that didnt work, nor do my dvds, audio, or any other cds I have.

Im completely new to ubuntu and google searching this problem made my stomach sink, cause I had no clue what was being talked about and that just confused me even more.

Can anyone walk me through this? IThe sooner I can get back to XP, the better.

Oh, because Xp is bootable, i tried putting that in and turning on my comp, and I get the option to boot from the cd, and I let it go, but instead of bringing up the XP options, Ubuntu loads. That also happens when I try loading my Win98 disk, and Nortons bootdisk.

Hopefully, tomorrow I can get my hands on a floppy drive and find a boot diskette, load 98se and get to xp from there.

Thanks for any help.

if none of the cds will boot and it won't recognize any cd or dvd you put in it, sounds like you have a hardware problem with your cd rom, you may want to look at replacing it or at least try cleaning the laser with a cd cleaner

> **Jerrick said:**
> Well, ive gone into the boot order (f12 on a gigabyte ep45 board) and selected to boot from the cd, but it would just go to ubuntu. In the bios ive even go as far as setting all three main boot options to cd-rom. And yes, I did hit enter when it would ask to boot from cd.

This morning showed some improvement with me being able to boot from a cd, so thats good, and once I get home from work, I should be able to have everything up in running in an hour.

Lol, im not saying ubuntu is bad. I quite like it, but I dont intend on using it on this machine.;-)

EDIT: Oh, can anyone help me with installing WINE? Thats all I need and ill be set.

> **Rocket2DMn said:**
> Let us know if you are successful with booting from the CD.  If you can't boot from the CD that is a hardware or BIOS problem since it is looked at before you ever get to GRUB or anything on the hard disk.

For wine, you should start a new thread in the wine forum - [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)
And check out [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

> **Jerrick said:**
> Well, I can boot from my windows98 cd, but not my Xp. But 98 doesnt work with my system because of "Insufficient memory" even though I have 4gigs ddr2 ram, plenty of harddrive space, and a quadcore processor. Guess old stuff cant work on everything thats new...

And XP cant boot in DOS mode. haha. Sucky.

Thanks for the link. Im getting it all working out with wine. Once I get this computer setup to how I like it, Ill get one of my other 4 comps running on ubuntu. :D

windows 98 didnt like (depending on who you listen to) more then 512 meg of ram (out of memory bug) or 2 gig (technical answer [http://answers.google.com/answers/threadview/id/333688.html](http://answers.google.com/answers/threadview/id/333688.html) )

> **Rocket2DMn said:**
> If you can boot from the 98 cd but not from the XP cd, it stands to reason that your XP disc is damaged in someway, so you should get your hands on a new one.

would be hard to believe that all but 1 disk is damaged

---

