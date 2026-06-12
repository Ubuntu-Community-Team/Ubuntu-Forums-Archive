---
title: "Grub Error"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Covalent Bond on 2012-04-27
I have 2 hard drives with Windows 7 on one and Ubuntu 11.04; I did a fresh install of 12.04 and all went well, but when I went to restart I got a message that said:  Error-no such device   <Grub Rescue>.  I do not know what went wrong or how to fix it.  When I installed I chose the option to erase 11.04 and install 12.04 as that is what I wanted to do.  There was a another option which was Other, but I had no idea of what to do with that.  I want the same set up I had with 11.04, namely 12.04 on the second HD with Windows on the Primary HD, the one used by my partner.

TX, 
CB

---

### Post by powder on 2012-04-27
The installer might have installed GRUB to the other hard drive.  Go into the BIOS and change your boot priority to boot to the other disk first.

If that doesn't work, go back into the BIOS and revert the changes.  Then use one of the methods at the link below to reinstall GRUB.

[https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2)

---

### Post by Covalent Bond on 2012-04-27
Thanks for the reply, but I opted to go back to 11.04 (Thats what I was in the process of doing when I first wrote), and that has worked.  Maybe later, I will try to reinstall.

CB

---

### Post by oldfred on 2012-04-27
Grub2 will default to sda with the automatic install options. You have to use Something Else or manual install to get the combo box on which drive's MBR to install grub2's boot loader into.

After an install:
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc
and to change it/reinstall it:
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Some explanation of manual installs. Older versions but only minor changes in screens to new version.

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

