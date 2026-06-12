---
title: "[SOLVED] SD Card Help Please"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by pjtb on 2008-11-23
I was playing with the SD card configuration and have managed to lose access to my SD card. I entered '/home' in 'mount with' (or something like that) when adjusting the configuration but cannot access these any longer.

I have reformatted in windows to FAT32 and this works fine. However, when inserted into my Acer Aspire One it does not show up at boot. Using 'Places-Computer' in the menus it shows up as '16.1 GB Media', right click on it and mount gives the following error

'Cannot mount volume'
Details are - 'mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually/)'

I assume I need to edit something but I don't know what to edit. Any help appreciated.

---

### Post by eldragon on 2008-11-23
im not sure is this will help, buy could you post the contents of /etc/fstab in here?

---

### Post by pjtb on 2008-11-23
Thanks for the reply eldragon, contents of fstab is


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=457b2d5b-ae02-454b-82b5-b4791032b6cd /               ext2    noatime,errors=remount-ro 0       1
# /dev/sda5
UUID=74ee7f5c-8973-48a6-8e0a-ebe9e8084ff0 none            swap    sw              0       0
#/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
tmpfs      /var/log        tmpfs        defaults           0    0
tmpfs      /tmp            tmpfs        defaults           0    0
tmpfs      /var/tmp        tmpfs        defaults           0    0 /dev/sda1              /             ext2      defaults,noatime,nodiratime,errors=remount-ro    0    1


Sorry don't know how to add quote box - hope this helps.

Regards

---

### Post by eldragon on 2008-11-23
fstab seems ok.

after inserting the sd card in its slot, open a terminal an dype
```

$ dmesg | tail

```

to encircle in a box pieces of code, you can select text and click the # number in the reply message box.(next to the <>)


you could also add the output of
```

$ lsmod | grep sdhci

```

---

### Post by pjtb on 2008-11-23
Thanks - after typing 'dmesg | tail' in terminal, the output was:
(the cannot mount error also reappeared!)
```
[   41.519713] Bluetooth: RFCOMM ver 1.8
[   44.079638] pciehp: Unknown parameter `pciehp_slot_with_bus'
[   45.128197] [drm] Initialized drm 1.1.0 20060810
[   45.133678] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
[   45.133697] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.133834] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   45.152810] mtrr: no more MTRRs available
[   85.127031] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   86.869052] NET: Registered protocol family 17
[  106.239877] ath0: no IPv6 routers present

```

The output of  'lsmod | grep sdhci' was:

```
sdhci                  19076  0 
mmc_core               51460  2 mmc_block,sdhci
```

I really appreciate your help with this!

---

### Post by eldragon on 2008-11-23
there is no record of the sdcard being detected in dmesg.

did you type the command right after inserting the card?

insert the card.
wait 2 seconds
type dmesg | tail

---

### Post by pjtb on 2008-11-23
Yes sorry the SD card was still in the slot from before when card inserted the cannot mount message came again but followed your instructions and got

```
[   45.133697] PCI: Setting latency timer of device 0000:00:02.0 to 64
[   45.133834] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   45.152810] mtrr: no more MTRRs available
[   85.127031] ADDRCONF(NETDEV_CHANGE): ath0: link becomes ready
[   86.869052] NET: Registered protocol family 17
[  106.239877] ath0: no IPv6 routers present
[ 3411.790195] mmc0: card b368 removed
[ 3416.995126] mmc0: new SDHC card at address b368
[ 3416.995720] mmcblk0: mmc0:b368 SDC   15694336KiB 
[ 3416.995846]  mmcblk0: p1

```

---

### Post by eldragon on 2008-11-23
now create a dir in your home
```

mkdir ~/sdcard

```

and try to mount it with 
```

sudo mount /dev/mmcblk0p1 ~/sdcard

```

if it should mount ok.. if this is the case, you might probably have been fiddling with some gnome settings.

you could (for testing purposes) create a new account, logout of yours and log in with the new one. and insert the card.

right now im looking at gconf settings concerning removable media, but cant find anything useful :(

if the new account can mount the sdcard. id advise you to start renaming certain config files in your home and see which one does the trick.

---

### Post by pjtb on 2008-11-24
> **eldragon said:**
> now create a dir in your home
```

mkdir ~/sdcard

```

and try to mount it with 
```

sudo mount /dev/mmcblk0p1 ~/sdcard

```

if it should mount ok.. if this is the case, you might probably have been fiddling with some gnome settings.

you could (for testing purposes) create a new account, logout of yours and log in with the new one. and insert the card.

right now im looking at gconf settings concerning removable media, but cant find anything useful :(

if the new account can mount the sdcard. id advise you to start renaming certain config files in your home and see which one does the trick.

Brilliant - Thanks all is now fixed and I will mark as solved!

I managed to mount the card with your instructions - so I used 'gconf-editor' and navigated to '/system/storage/drives/_org_freedesktop_Hal_devices_storage_serial_0x000002c3/mount_point' and deleted the '/Home' that I entered via another means.

Reboot and Hey Presto the device mounted. (I imagine you can cause serious issues with you system by adjusting settings using gconf-editor though)

Thanks again for your help - much appreciated!

---

### Post by eldragon on 2008-11-24
> **pjtb said:**
> Brilliant - Thanks all is now fixed and I will mark as solved!

I managed to mount the card with your instructions - so I used 'gconf-editor' and navigated to '/system/storage/drives/_org_freedesktop_Hal_devices_storage_serial_0x000002c3/mount_point' and deleted the '/Home' that I entered via another means.

Reboot and Hey Presto the device mounted. (I imagine you can cause serious issues with you system by adjusting settings using gconf-editor though)

Thanks again for your help - much appreciated!

well, gconf-editor only changes settings for the user running it, so even if you can break stuff, its quite simple to revert everything back to defaults. (rename ~/.gconf ) which is what i was going to suggest next..

glad it worked.

---

### Post by Locke_99GS on 2008-11-24
Peculiar - I have the exact same issue, though I have a pretty fresh Intrepid install, and I haven't tweaked *anything* other than the goofy new FUSA. Without an SD card handy, I can't check or try the advise given at the moment. I will come back to this thread later, when I do have a card handy, though. (subscribe)

---

