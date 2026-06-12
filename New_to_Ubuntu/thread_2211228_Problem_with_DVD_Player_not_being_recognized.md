---
title: "Problem with DVD Player not being recognized"
date: 2014-03-14
forum: New to Ubuntu
---

### Post by conwaycc on 2014-03-14
I was having problems getting the CD drive to work but after playing with the "Disks" graphical edit mount options and changing to manual then back again and inserting a data disk and audio CD the CD is working but says read only and it is a CD RW drive.  Haven't tried the burning part on that drive yet.  

The next problem is with the DVD ROM.  It will not play a DVD or read a CD when inserted in the drive but I can eject from the GUI interface so it is sending the correct signal to the correct device being the DVD ROM.  

ubuntu 13.10 32-bit
Dell Dimensions GEN 3 w/1 GB ram

Here is what is in my /etc/fstab:
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=5a493a7b-11f8-49dd-901f-35d0068dd4e0 /boot           ext2    defaults        0       2
/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

In the "Disks" application:

Both drives are set with Automount: ON

Model:  JLMS DVD-ROM XJ-HD166 (DD05)
Device: /dev/sr0 (Read-Only)
Media & Size: -
Size & Contents:  -

nosuid,nodev,nofail,noauto,x-gvfs-show
Mount Point:  /mnt/ata-JLMS_DVD-ROM_XJ-HD166
Identify As:  /dev/disk/by-id/ata-JMS_DVD-ROM_XJ-HD166
Filesystem Type:  auto

Do I need to change the Mount Point which is the default /mnt/ata-JLMS_DVD-ROM_XJ-HD166 to /dev/sr0?

Hopefully I provided enough info about the problem.  First post and just installed ubuntu 3 days ago since XP support is ending April 8.  So far everything else is working great and I really like it.

---

### Post by conwaycc on 2014-03-15
Okay, I got it to work and can now see the DVD in the "Videos" application.  But now I am getting the following error after it plays the DVD for about 10-15 seconds - "data flow error"

Anyone know how to fix this?

---

### Post by deadflowr on 2014-03-15
Did you try following this
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by conwaycc on 2014-03-15
I ran the following:
sudo apt-get install ubuntu-restricted-extras and it displayed the following but will not do anything when I press enter or "O".

TrueType core fonts for the Web EULA                                         
 &#9474;                                                                              
 &#9474; END-USER LICENSE AGREEMENT FOR MICROSOFT SOFTWARE                            
 &#9474;                                                                              
 &#9474; IMPORTANT-READ CAREFULLY: This Microsoft End-User License Agreement          
 &#9474; ("EULA") is a legal agreement between you (either an individual or a         
 &#9474; single entity) and Microsoft Corporation for the Microsoft software          
 &#9474; accompanying this EULA, which includes computer software and may include     
 &#9474; associated media, printed materials, and "on-line" or electronic             
 &#9474; documentation ("SOFTWARE PRODUCT" or "SOFTWARE"). By exercising your         
 &#9474; rights to make and use copies of the SOFTWARE PRODUCT, you agree to be       
 &#9474; bound by the terms of this EULA. If you do not agree to the terms of         
 &#9474; this EULA, you may not use the SOFTWARE PRODUCT.                             
 &#9474;                                                                              
 &#9474;                                                                              
 &#9474;                                  <Ok>

---

### Post by conwaycc on 2014-03-15
Well that didn't work - it hosed up when I closed the terminal window and I had to kill the process.  Then ubuntu software center tried to repair and that failed too.

---

### Post by deadflowr on 2014-03-15
What process did you kill?

Anyway, when you get the eula, use the tab key and the arrows to choose.
(I always go with yes, for the sake of not wanting it to abort. even though I don't know if it would)

---

### Post by conwaycc on 2014-03-15
I tried it again and when you get to the license screen the only way to get past it was to press the TAB key.  Go figure.  I am new so bear with me but now it is installed.

All done, no errors.
All fonts downloaded and installed.

Also installed the libdvdccs

I am still getting the "Internal Data Flow Error".  This did not fix the problem.

---

### Post by conwaycc on 2014-03-15
The "Videos" application is problematic even after all of the updates.  Reinstalled the VLC media player and NOW everything works.  I will just use that player go forward.  Thank you so much for you help!!!!! Installing those packages and the VLC media player was the key!

---

