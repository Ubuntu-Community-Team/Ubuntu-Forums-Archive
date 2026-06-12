---
title: "Installing Ubuntu on a separate hard drive from Windows"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by mathguy54 on 2012-09-28
I have two hard drives. One is for Windows and the files I have  accumulated over time. The other hard drive is an empty hard drive that I  want to use to install and use Ubuntu on. I have the Ubuntu 12.04 ISO  disc and I booted with that disc. How do I install Ubuntu on the second  hard drive (disk1 in Windows (disk0 is Windows and disk1 is empty), sdb  in Ubuntu)?

---

### Post by dgharmon on 2012-09-28
> **mathguy54 said:**
> How do I install Ubuntu on the second  hard drive

Dual-boot Ubuntu on a PC with 2 hard drives

[http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/](http://www.linuxbsdos.com/2011/10/27/dual-boot-ubuntu-11-10-windows-7-on-a-pc-with-2-hard-drives/)

---

### Post by Bashing-om on 2012-09-28
mathguy54; Hi ! Welcome to the forum.

This aint't no big deal (welcome to ubuntu !).

I suggest you look at your disk  -for safty's sake alone- with GParted: Dash=>search term:Gparted, click on the icon that appears. This insures ubuntu and you agree, I do expect ubuntu to see the second disk as "sdb".

choose install ...for a basic, no nonsense straight forward install; let the wizard install the system. Simply at the install screen choose "use entire disk" make sure that sdb is where the wizard will install, answer a few more questions, - Tattoo your chosen password on the back of your brain - ..it is vitally important to remember your password. 
Nothing is written until the final screen that informs you of what the installer is going to do. At this point click the advanced tab and verify where grub is going to be installed (can change it if ya want), default I expect to be sda ..which is fine if you intend to boot from the 1st hard drive. Be advised that grub (Grand Unified Bootloader) will chainload windows bootloader to give you the option of which system to boot.

Finally click "install" to make it happen.
[INDENT]We are here if ya have need, or have any other questions and/or concerns.

Kind regards <==BDQ

[/INDENT]

---

### Post by RogerDavis on 2012-09-28
This is the setup I have, but with a twist.  I have a separate hard drive for Windows 7 and for Ubuntu 12.04.  

BUT I have the drives in switchable trays in which I can totally turn on or off each drive as I choose. (check out  [http://kingwin.com/products/cate/mobile/racks/kf_91_bk.asp](http://kingwin.com/products/cate/mobile/racks/kf_91_bk.asp) )  I just turn the switch on any drive to turn it on or off.  

I rarely remove the tray, but that comes in handy too if I want to do something with the drive and not do disassembly.

The only problem is that you need a 5.25 slot open to the front for each drive you want to do this with.

---

### Post by oldfred on 2012-09-29
The disadvantage of any of the auto install options is that grub usually is installed into sda or the Windows drive. Better to insure that grub2's boot loader is installed to sdb, but only with Something else does that work.

dgharmon's link on page 2 highlights the combo box to choose which drive's MBR to install grub2's boot loader into.

If a new computer you may have UEFI. Older computers are BIOS and usually MBR(msdos) partitioned. Windows will only install to gpt partitioned drives with UEFI, Ubuntu will work on gpt partitioned drives with either BIOS or UEFI. 
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
If gpt(not MBR) partitioning include these two first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

