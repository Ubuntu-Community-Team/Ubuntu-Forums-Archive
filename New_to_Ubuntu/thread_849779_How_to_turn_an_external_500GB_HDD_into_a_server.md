---
title: "How to turn an external 500GB HDD into a server"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by deadlySniper on 2008-07-04
I am wondering on how to accomplish this. I have been attempting this for a while. I have Windows Server 2003 but I am wanting to use some form of linux that is great with severs. I have tried to us WOS (Portable server) but was too much work and had problems with it. Is there any guide or something I can use to do this?

---

### Post by lazyart on 2008-07-04
Connect your drive and boot up with a LiveCD.  Choose Install from the main menu.  You don't want to go into the Ubuntu session.

Select the 500 gb disk to install to.  After you've done your partitioning and such it will show you what changes you are about to make to the disk.  HIT THE ADVANCED BUTTON.  There it will ask you where to install the boot loader.  If you put it on your internal drive then you will get grub everytime you boot up asking if you should start Windows or Ubuntu on the external hd.

If instead you choose to put the boot loader on the external drive, then to get to ubuntu you would change the boot sequence on the computer to boot from USB HDD.  Grub there will only see Ubuntu as an option and take you on in.  I would suggest the putting grub on the external drive.  For fun you can connect the drive to any machine and boot to it.

Just make sure you partition and install on the correct drive.  Please, make sure.  The internal drive should show up as sda1, while the external will be numbered higher (depending on how many partitions your internal disk has, as well has how many internal disks and optical drives you have).

---

