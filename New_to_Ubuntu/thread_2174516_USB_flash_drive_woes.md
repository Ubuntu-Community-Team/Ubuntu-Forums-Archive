---
title: "USB flash drive woes"
date: 2013-09-14
forum: New to Ubuntu
---

### Post by WacoJohn on 2013-09-14
I can access it in File Manager ... Media Folder then another folder within ... open that and there are the contents of the drive.  I seem to be able to read from it .. but that is it.  Can't copy to/from it.  I am ASSUMING it is mounted ... or I would not even be able to do that much .. but maybe not.

```
wacojohn@ubuntuCOMPAQ:~$ lsusb
Bus 001 Device 002: ID 13b1:002e Linksys 
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
```

The drive is inserted into one of two 2.0 ports on a USB card.

Don't know if this helps:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=d5e87bd1-2ab0-4c40-b11d-79eee6fd7ce8 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=38ba3ba2-f866-4616-b09c-52668007a0f9 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

Huh??
```
# / was on /dev/sda1 during installation
UUID=d5e87bd1-2ab0-4c40-b11d-79eee6fd7ce8 /               ext4    errors=remount-ro 0       1
```

There are also two other devices in MEDIA folder ... same problem but they are POGOPLUG hard drives.

Help is appreciated in advance.

---

### Post by Android_63 on 2013-09-14
Does the same thing happen on other flash drives, or just that one?

---

### Post by WacoJohn on 2013-09-15
> **Android_63 said:**
> Does the same thing happen on other flash drives, or just that one?

I am not sure what is going on.  Might be I am not familiar with this particular File Manager.  It seems I can do anything I want now .. as long as I paste into the correct pane of the FM.  To be honest .. maybe I am losing my mind.  I can now to things I could not do before ... with either flash drive or pogoplug drive .... _I think_.  It is astounding how many tests there are to be certain these devices manage files entirely ... can you delete, can you move, can you copy, can you open .... but at the moment, it seems it all does actually work.

Thank you immensely for your interest.  If I have further problems, I will append to this thread.  Thank you again.

---

### Post by CeejRab on 2013-09-15
Hello WacoJohn,

Try pressing the windows button on your keyboard to open the dash and type "disk utility". Open the program and select the drive that is causing you issues. If it gives the option to mount it, do so and see if this fixes your problem. If the option to unmount it is there, this means it is currently mounted and further action must be taken. I would recommend unmounting, then formatting it as FAT and then remounting it. Then all should work fine after an unplug and computer reboot. 

All the best,

-Christian

---

### Post by CeejRab on 2013-09-15
Good to hear things are working, however freaky it might be that its spontaneously cooperating! 

Hope it continues to work for you. If not, there's plenty of happy Linux lovers here ready to help!

All the best,

-Christian

---

