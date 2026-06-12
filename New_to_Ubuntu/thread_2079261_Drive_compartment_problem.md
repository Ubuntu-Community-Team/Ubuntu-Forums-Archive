---
title: "Drive compartment problem"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Martynwills on 2012-11-01
When I installed Ubuntu I don't remember getting clear choices about compartmentalising it. I set it up with what I thought was a windows compartment and an ubuntu.

I have just tried to upgrade to Pangolin and it says there isn't enough room.

I opened disk utility and it seems to show 152 Gb sitting free on the hard drive, but no clear route for me to assign this to my ubuntu part of my system. There is an option to create a new partition, but when I open that i can't make sense of the options.

Can anyone help or suggest what I should try?

Im running ubuntu 11.10 if that's any help.

Cheers

---

### Post by critin on 2012-11-01
Take a screen shot of your disk in gparted and upload & post according to instructions in the forum message box.

---

### Post by Martynwills on 2012-11-01
[IMG]http://ubuntuforums.org/picture.php?albumid=2511&pictureid=8533[/IMG]

---

### Post by Bashing-om on 2012-11-01
Hi !Martynwills;

 Heads up..looking at the GParted posting. I see only ntfs partitions. This indicates that your install is inside of windows, -wubbi-.

In my optinion, if your desire is a side-by-side install of ubuntu -> from within windows, delete the ubuntu file...re-install ubuntu onto the unallocated 141.99 Gigabyte space.

Here are guides to assist you :
[https://help.ubuntu.com/community/Wubi#Un-install_from_Vista_or_Win7](https://help.ubuntu.com/community/Wubi#Un-install_from_Vista_or_Win7)
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)


Post back with additional queries and questions.[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by NM5TF on 2012-11-01
> **Martynwills said:**
> [IMG]http://ubuntuforums.org/picture.php?albumid=2511&pictureid=8533[/IMG]

are you running a dual boot system with Windows & Ubuntu 11.10???

from the screenshot above all I see are NTFS partitions which are
usually associated with a Windows OS....where is your Linux 11.10
partition???  it should be either ext3 or ext4 filesystem...

you also have 141.99 GB of unallocated space that can be used to 
install Ubuntu 12.04....you will have to create a new partition
using GParted....

I do not see any Linux swap partitions either....you must have many
GB's of RAM I assume....

(edit) I see now what you have... you installed 11.10 from within
Windows....the reason only NTFS partitions are visible....

like the post above said...purge the 11.10 install & use the unallocated
space to install 12.04LTS....

---

### Post by Cheesemill on 2012-11-01
A default Wubi setup is limited to 30GB for your Ubuntu installation. It is, however, possible to resize your Wubi disk to more than 30GB.

[https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk](https://help.ubuntu.com/community/ResizeandDuplicateWubiDisk)

---

### Post by Mark Phelps on 2012-11-02
Since it looks like you have a Wubi installation (due to the lack of a Linux filesystem), my advice is to NOT upgrade it, but instead, to remove it and replace it.

Wubi installs are intended for short-term use, and while they CAN be upgraded, they have an unfortunate history of not surviving that well -- resulting in a trashed install that then has to be removed.

Since you only have three partitions and could install to another partition, if you want to use Ubuntu in the long-term, you should consider removing your Wubi install.

---

