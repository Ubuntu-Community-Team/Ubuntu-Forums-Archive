---
title: "How to change startup menu when booting from USB"
date: 2015-12-14
forum: New to Ubuntu
---

### Post by guhjkl3 on 2015-12-14
So I often run Ubuntu from a USB. I had 14.10 on a USB that I made with pendrive and it when I ran it, it would immediately go to a black screen and with the keyboard I could choose what I wanted to do immediately. I made a new one from Ubuntu and it went back to the picture on the left where it would take a while to load and then ask me if I wanted to try or install Ubuntu and then load the desktop after I always clicked try. My question is: is there a way to change between the 2 displays or select one over the other?



[ATTACH=CONFIG]266153[/ATTACH][ATTACH=CONFIG]266152[/ATTACH]

---

### Post by sudodus on 2015-12-14
When you see two small icons near the bottom of the screen, you should press a key in order to get the display to the right (or a display similar to it).

But 14.10 has passed end of life, and you should download and try 14.04.1 LTS (long time support) or 15.10 (the newest version).

---

### Post by C.S.Cameron on 2015-12-14
The following was my answer to a previous post, the method to increase persistence is optional, modification of the syslinux.cfg gets rid of the Try/Install screens altogether and starts the try option. (Not an exact answer to your question).


Boot Live CD or Live USB.
Plug in flash drive.
Start gparted.

Create 2 GB FAT32 partition, (on the left side of the bar). (size is optional, extra space can be used for file storage and transfer to Windows machines).

Create a 4 GB ext2 partition to the right of this, labeled it "casper-rw". (ext3 and ext4 also work).

Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition).

Close gparted.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, Go to the root folder of your Live USB
    Enter the syslinux directory, (or for UNetbootin the root directory).
    Make the syslinux.cfg file writeable
    Replace the contents of the file syslinux.cfg with:

```
    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

Shutdown, remove CD, reboot.


First time booting go to users and groups and create an account with yourself up as an Administrator, with password if desired.

Note:
The above code will bypass the Try/Install and Language screens.

For 64 bit systems use:


    default persistent
    label persistent
      say Booting a persistent Ubuntu session...
      kernel /casper/vmlinuz.efi
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --

---

