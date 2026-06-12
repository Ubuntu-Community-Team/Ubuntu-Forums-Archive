---
title: "dual boot from different hard drives"
date: 2012-06-13
forum: New to Ubuntu
---

### Post by dlpeka on 2012-06-13
I have 4 hard drives in my computer; Windows 7 resides on "C" and Ubuntu resides on "H".  If I completely install Ubuntu (I've installed it -- just haven't rebooted yet to finalize it), will it mess up my Windows or files, etc. created in Windows?
C = Windows 7
H = Ubuntu
I'm imagining it will _not_ interfere with Windows 7 if I finalize installation of Ubuntu on a different hard drive.  But wanted to be sure!
Goal is to have the option of which system to boot (dual-boot).

---

### Post by black veils on 2012-06-13
if you partitioned correctly etc, it should be ok. either way, its done now, whether you restart or not, you have already made changes. you should let it do the reboot.

if you have problems after that, then you can post again.

---

### Post by dlpeka on 2012-06-13
I didn't "partition" any of the drives.  Windows 7 was already on my computer on the "C" drive.  I have two other drives with documents, etc., created in Windows 7.  When I decided to try Ubuntu, I installed a new and separate internal hard drive, and wish to run Ubuntu from that drive.  With it on a completely separate drive, even though it's using the same Motherboard, will it interfere with Windows 7, or will I simply be prompted to select which OS I want to boot under at startup?  Sorry if this sounds basic, but that's what I am - a Basic Newbie to Ubuntu!

---

### Post by drs305 on 2012-06-13
One of the last steps of the installation should have been where you want to put the Ubuntu bootloader (GRUB).

Select sdb (don't select an entry with a partition number such as sdb1 or sdb5). sdb should be your second drive. If it isn't sdb, select whatever the Ubuntu drive is.

This will keep the Windows bootload on sda (assuming sda is your Windows drive) and put GRUB on sdb. On rebooting, change the BIOS boot order to boot your Ubuntu drive first.

On the initial boot, you should see both Ubuntu and Windows. If you don't and it boots directly into Ubuntu, open a terminal and run:
```
sudo update-grub
```
That command should locate Windows and add it to the Ubuntu boot menu.

The advantage of installing GRUB only to sdb is that if you ever have problems with booting Ubuntu, you can change your BIOS back to booting sda first. This will return the Windows control of the boot without having to make any other changes.

---

### Post by oldfred on 2012-06-14
Do not use any of the automatic installs. Grub defaults to sda which usually is the Windows drive. It would then overwrite the Windows boot loader. You would still be able to boot, but better to keep the Windows boot loader on the Windows drive and the Ubuntu/grub2 boot loader on the Ubuntu drive as drs305 says. See last link to the screen to choose sdb to install grub2's boot loader into the MBR.

Install examples with screen shots, only minor changes in installer from any version:

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

