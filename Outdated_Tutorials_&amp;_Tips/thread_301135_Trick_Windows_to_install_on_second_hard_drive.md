---
title: "Trick Windows to install on second hard drive"
date: 2006-11-16
forum: Outdated Tutorials &amp; Tips
---

### Post by N/A on 2006-11-16
Hello!

This is how i tricked Windows Me to install as a secondary OS on a slave HDD even if it was reluctant to do so.
My System:
I have 2 HDD,
- one has 80GB - Master (IDE-0) File System: ReiserFS
- second has 8GB - Slave (IDE-1) File System: FAT 32

Previously i had Windows XP(first os) on the first Hard disk and Windows Me(installed after XP) on the second one, but Windows XP was sluggush and i formated the drive as ReiserFS (i don't know if is the best choice) for Xubuntu. After installing Xubuntu i had Windows Me in the boot list but the OS wasn't able to start so i had to reinstall it.
You may not have the same problems as i did but if you do i list them all in here:

Specific state: because i previously had windows ME, after instaling Xubuntu, GRUB detected my Windows presence so at boot screen it was already in the list, it just didn't started(is an error of wrong boot thing). If you don't have windows in the boot list then you should add it manualy. Because i don't really know how to do it i suggest you should use the search button. This is what i have in  /boot/grub/menu.lst I suspect this is what you shoult try to have too (is right at the end of the file):


title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows 95/98/Me
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

!! NOTE!!! : test to see if this works for you.


Problem 1: No functional floppy drive -> that means my MS boot floppy won't work -> no ms-dos -> no windows installation.
Fix: 
- download WindowsMe boot disk (is the best boot disk for windows imo) from [here](http://www.allbootdisks.com/index.php?option=com_remository&Itemid=42&func=fileinfo&parent=folder&filecatid=1871)
- have a blank CD to make a WindowsMe boot CD.
- if you have xubuntu use Add/Remove to get CD/DVD Writer Gnome Baker (is in accesories) (on xubuntu the default Xfburn doesen't seem to want to burn .iso)
- chose Burn CD Image, chose the WinMe.iso and burn it, after that you will have a WinMe boot CD.

Problem 2: The  boot CD works but the setup.exe from the Windows Me Installation CD can't write to the primary boot record because is not FAT32 so you get an error and must exit setup. The BIOS boot sequence was CDROM,IDE-0,IDE-1...
FIX:
Enter BIOS and set:
first boot device IDE-0 (this has linux - is the master HDD)
second boot device IDE-1 (this is where windows will go - slave HDD)
third boot device CDROM

*Note: if you can set only 2 boot devices (really old system) then chose IDE-0 and CDROM

Tricking Windows:
Ok this is how you trick windows to install itself(this is possible because GRUB is a boot manager (like PQBOOT):
1 - Put CDROM in the CD drive
2 - Reboot PC
3 - In the boot list you should have Windows, select it and press enter (if you don't you must set GRUB or your boot manager to boot from the second HDD)
4 - You should get a boot record error or something and will ask you to press a key, preass any key and wait for the boot CD to start
5 - After the boot cd starts chose the startup with CDROM support
6 - go to your cdrom (usually D: if you didn't had your second HDD partitioned) and type setup.exe /is to skip the scandisk
7 - to me it happend that after the initial progress bar got to 100% the PC just hanged for a looooooong while and i started moving the mouse and clicking its buttons and after that it continued with the normal setup... i don't know if it was because i clicked but there was no activity on my HDD nor on my CD and for some reason clicking the mouse buttons and moveing the mouse seems to work for me. 
8 - go on with the usual windows dumb free setup.

After windows is installed, reboot. In the boot list you shoud still have windows but this time it will work.

And this is how you install Windows Me on a second (slave) HDD and with not FAT32
If you need to install windows on the same HDD with linux but on different partition there is a different HOWTO on the Internet (Google it!)
if this doesn't help you then do what everybody else is doing: IMPROVISE!

Good Luck!

---

