---
title: "Installing Ubuntu on its own HDD but still have dual boot with Windows 7"
date: 2012-07-06
forum: New to Ubuntu
---

### Post by rudibear on 2012-07-06
I would like to install Ubuntu 12.04 on its own hard drive in my PC, but still have dual boot capability.
Is this possible?
If it is, how do I go about it?
I tried using the Windows installer and although I can point it to the drive I want to use, I can only select up to 30GB, where the drive in question is 500GB and I would like to have Ubuntu use the entire drive.

---

### Post by anewguy on 2012-07-06
In the installation process, select the manual partitioning and set up the partitions you want on your ubuntu-only disk.  In this process it will also ask where you want grub to be installed - it will default to where you want to install ubuntu.  Change this to point to the drive with Windows.

---

### Post by rudibear on 2012-07-06
Thank you.

---

### Post by Shadius on 2012-07-06
> **rudibear said:**
> I would like to install Ubuntu 12.04 on its own hard drive in my PC, but still have dual boot capability.
Is this possible?
If it is, how do I go about it?
I tried using the Windows installer and although I can point it to the drive I want to use, I can only select up to 30GB, where the drive in question is 500GB and I would like to have Ubuntu use the entire drive.

Here'a nice guide on installing Ubuntu. [How To Install Ubuntu 12.04]("http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/"). Also, using the Windows installer (WUBI) isn't a "real" installation. It is just installing Ubuntu within Windows.

---

### Post by holycow131415 on 2012-07-06
There is a point in the installation where you chose the drive you want ubuntu to be installed on. youll see 2 drives (and these will be the physical drives) that youll have to chose from. Becare to chose the right one so that you dont overwrite windows.

---

### Post by oldfred on 2012-07-06
With 2 drives you really want to keep them separate and fully bootable on there own. Some suggest disconnecting one and then installing, then only connecting the other for the second install.

If you use manual install you get the combo box which gives the choice on where to install the grub2 boot loader. You will want to choose sdb (usually) not the default sda.

While new version has many changes the installer is almost identical, so these are still valid:

Install to external drive 11.04. Also any second drive.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

