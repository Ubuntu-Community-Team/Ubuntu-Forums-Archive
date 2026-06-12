---
title: "Trying to Install Ubuntu on MacBook using USB Jump Drive"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by David_Sigmon on 2014-05-01
I am a newbie, so I posted here instead of the Install section. I have a mid-2009 MacBook. I am trying to follow the instructions in a few Community Help Wiki documents: "Mactel Support Team / Apple Intel Installation" and "How to install Ubuntu on MacBook using USB Stick".

I successfully downloaded ubuntu 14.04 desktop amd64.iso, and converted it to a .img.dmg.

Here is my Terminal script for the next steps:
"[FONT=Menlo]diskutil list[/FONT][FONT=Menlo]/dev/disk0[/FONT]
[FONT=Menlo]   #:                       TYPE NAME                    SIZE       IDENTIFIER[/FONT]
[FONT=Menlo]   0:      GUID_partition_scheme                        *160.0 GB   disk0[/FONT]
[FONT=Menlo]   1:                        EFI EFI                     209.7 MB   disk0s1[/FONT]
[FONT=Menlo]   2:                  Apple_HFS Untitled                94.2 GB    disk0s2[/FONT]
[FONT=Menlo]   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3[/FONT]
[FONT=Menlo]   4:                  Apple_HFS Untitled 2              64.9 GB    disk0s4[/FONT]
[FONT=Menlo]/dev/disk1[/FONT]
[FONT=Menlo]   #:                       TYPE NAME                    SIZE       IDENTIFIER[/FONT]
[FONT=Menlo]   0:     FDisk_partition_scheme                        *2.1 GB     disk1[/FONT]
[FONT=Menlo]   1:               Windows_NTFS Untitled                2.1 GB     disk1s1[/FONT]
[FONT=Menlo]David-Sigmons-MacBook:~ davidsigmon$ diskutil unmountDisk /dev/disk1[/FONT]
[FONT=Menlo]Unmount of all volumes on disk1 was successful[/FONT]
[FONT=Menlo]David-Sigmons-MacBook:~ davidsigmon$ sudo dd if=/Users/davidsigmon/Documents/ubuntu.img.dmg of=/dev/rdisk1 bs=1m[/FONT]
[FONT=Menlo]Password:[/FONT]
[FONT=Menlo]964+0 records in[/FONT]
[FONT=Menlo]964+0 records out[/FONT]
[FONT=Menlo]1010827264 bytes transferred in 193.092326 secs (5234943 bytes/sec)[/FONT]
[FONT=Menlo]David-Sigmons-MacBook:~ davidsigmon$"

It looks successful, but I immediately get a pop-up warning: "The disk you inserted was not readable by this computer." and options "Initialize", "Ignore", and "Eject".

I have tried erasing the USB drive using the disk utility, and formatting it with FAT, and a separate time as an Apple_HFS. Each time, the computer can access it fine, until after I run the sudo function. 

I have also tried ejecting it after the successful(?) sudo, putting it back in and restarting the computer, and none of my reFit options seem to refer to the USB drive or disk1 as it is known by. If I choose the efi boot64 or grub, it says the disk cannot be found, then I get the screen where it asks if I want to Try Ubuntu, and I select it and then nothing happens for 30 minutes, so I use the power button to turn the laptop off.

Any help would be very appreciated. Thanks in advance.[/FONT]

---

### Post by llamabr on 2014-05-01
Dunno.  There's a ubuntu on mac thread on this forum. If you don't get any advice on this thread,  [Click here]("http://ubuntuforums.org/forumdisplay.php?f=328").

For me, I run debian on my old ppc ibook, but I've never tried a usb install.

---

### Post by David_Sigmon on 2014-05-01
While I am waiting for a reply, I tried converting the original .iso file again, so the resulting file would be named "ubuntu.dmg" instead of "ubuntu.img.dmg". However, that did not improve anything, as the computer still tells me it cannot read the USB drive after completing the sudo function.

---

### Post by David_Sigmon on 2014-05-01
> **llamabr said:**
> Dunno.  There's a ubuntu on mac thread on this forum. If you don't get any advice on this thread,  [Click here]("http://ubuntuforums.org/forumdisplay.php?f=328").

For me, I run debian on my old ppc ibook, but I've never tried a usb install.
Thanks, llamabr. I am going with the usb install, as the file won't fit on my cd-roms that only hold 800mb.

---

