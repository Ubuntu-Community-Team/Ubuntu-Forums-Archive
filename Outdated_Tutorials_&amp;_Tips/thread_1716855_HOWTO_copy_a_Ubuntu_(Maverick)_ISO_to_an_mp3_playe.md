---
title: "HOWTO copy a Ubuntu (Maverick) ISO to an mp3 player in LINUX."
date: 2011-03-29
forum: Outdated Tutorials &amp; Tips
---

### Post by bincue on 2011-03-29
:!: **WARNING, the following instructions will destroy any existing data on your mp3 player (if done correctly :)).** **NOTE: The size of the ISO is limited to the total amount of space on  your mp3 player. If it is 1GB device then you may use a CD iso. If it is  a 5GB device, then you may use a DVD iso.**

**1.** Plug your mp3 player into an open USB port via data cable and learn how your mp3 player is recognized by the system, 

enter the command:```
sudo ls -l /dev/disk/by-id/*usb*
```This should produce output along the lines of:```
lrwxrwxrwx 1 root root  9 2010-03-15 22:54 /dev/disk/by-id/JET_2.0_047990434080-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 2010-03-15 22:54 /dev/disk/by-id/JET_2.0_047990434080-0:0-part1 -> ../../sdc1
```**2.** Unmount the mp3 player ```
umount /dev/sdc
``` using Gnome Disk Utility ```
sudo palimpsest
```Format the specific Peripheral Device -EMPTY, then use this command to write (as root) the image iso to your mp3 player.\\  
Continue...
:!: Replace /dev/sdX with the actual device learned from the command above. In this example /dev/sdc NOT /dev/sdc1 \\ 
:!: Replace the name of the iso image below by the actual name of the iso image you downloaded.```
sudo dd if=/path/to/iso/[ubuntu-10.10-desktop-i386.iso]("http://releases.ubuntu.com/maverick/ubuntu-10.10-desktop-i386.iso") of=/dev/sdX bs=4M;sync
```Example: /path/to/iso/  may be /home/username/Downloads/

You will see the results like the example below.```
171+1 records in
171+1 records out
720887808 bytes (721 MB) copied, 1262.99 s, 571 kB/s
```All being well, you should now have a bootable UBUNTU 10.10 Maverick Meerkat. **Note: For Security reasons, the mp3 player will be a READ ONLY DEVICE using this method.**

_Setting a pc boot sequence First Device=USB HDD will suffice_

Good luck.

My experience:
Tried this method with two different mp3 player manufactures and with several distros, not only Ubuntu, Fedora, Mint, Peppermint, Xubuntu, Zorin, ChromeOS, and many more. Any LIVE Edition allows you to try before you install as well.

Get creative and make your own ISOs with some of your favorite pkgs in a folder. The only limit is the size of the mp3 player storage space.

*-Inspired by Crunchbang ISO to USB... ran out of USB thumbs... found some unused mp3 players, It worked!*

---

