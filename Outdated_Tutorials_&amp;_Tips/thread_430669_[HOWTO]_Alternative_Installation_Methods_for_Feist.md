---
title: "[HOWTO] Alternative Installation Methods for Feisty"
date: 2007-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by speedisso on 2007-05-02
Besides installing from a bootable CD, Ubuntu can be installed using other methods as well, which might prove handy in some circumstances. For instance, you might find yourself in the situation when you need to install Ubuntu on one or more machines with no CD-ROM drives, but with an active network connection. For that, you will need another machine on the network that will provide the installation files to other computers on the LAN, through the network. However, in order to perform a successful network install, your computers must support booting from the network.

You should follow this guide if:
- you have to install Ubuntu on a machine with no CD-ROM drive but with an active network connection
- this machine provides the 'boot from network' option in its BIOS
- you have access to another network machine that's already running Ubuntu

INSTALL FROM NETWORK SERVER

First of all, you'll need to set-up the server, which is the machine already running Ubuntu. On this machine, you'll install the FTP, HTTP and DHCP servers, which will allow the client machine to connect to the server and fetch the installation files and package repositories. To install these services, open a terminal and type:


$ sudo apt-get install tftpd-hpa apache2 dhcp3-server


Now, on the server machine, mount the installation CD, or the downloaded iso. Keep in mind that for network installations, you'll need to download the alternate ISO:


$ cd /where/you/downloaded/the/iso
$ sudo mkdir /var/lib/tftpboot/ubuntu
$ sudo mount -o loop ubuntu-7.04-alternate-i386.iso /var/lib/tftpboot/ubuntu


Make a symlink to the mounted ISO, from the Apache's root directory:


$ cd /var/www
$ sudo ln -s /var/lib/tftpboot/ubuntu/


If the server has a CD-ROM drive and you already have burned the Ubuntu alternate ISO installation CD, insert it into the server's CD-ROM drive and wait for it to get auto-mounted. It will probably get mounted under the /media/cdrom path, so we'll need to create symlinks for both FTP and HTTP servers:


$ sudo ln -s /media/cdrom /var/lib/tftpboot/ubuntu/
$ sudo ln -s /media/cdrom /var/www/ubuntu


Now, configure the DHCP daemon. Download the dhcp config file:


$ cd /etc/dhcp3
$ sudo mv dhcpd.conf dhcpd.conf.old
$ sudo wget [http://download2.softpedia.com:8081/linux/dhcpd.conf](http://download2.softpedia.com:8081/linux/dhcpd.conf)


Open the dhcpd.conf file in a text editor and edit the following directives to match your network:

subnet and netmask - your network subnet and netmask
range - an IP from this range will be randomly assigned to the client machine
domain-name-server - enter here your DNS servers

Reload the dhcpd config file:


$ sudo /etc/init.d/dhcp3-server restart


At this point, your client machine is ready to boot the alternative installation ISO from the server. Simply reboot the client PC, open the BIOS configuration and under the BOOT menu, choose network as the first boot device. Save and exit. If everything worked out well, you should see the Ubuntu installation screen and boot prompt on the client machine.

INSTALL FROM HARD DISK

For this method, you'll need to already have a working Linux system on the machine on which you want to install the new Feisty system. This method provides a faster and more usable system because the installer is running from a hard drive rather than from a CD.

First of all, you need to use GParted to create a new primary partition and format it to ext3. For example, let's say that the partition is /dev/hda3. You will need to copy the ISO's contents over to the new partition:


$ mkdir /tmp/installcd
$ sudo mount -o loop /path/to/ubuntu-7.04-desktop-i386.iso /tmp/installcd
$ sudo mkdir /mnt/installer
$ sudo mount /dev/hda3 /mnt/installer
$ sudo cp -r /tmp/installcd/* /mnt/installer
$ sudo umount /tmp/installcd


Next, you'll need to edit your current Grub configuration file to boot the new partition. To do this, open the /boot/grub/menu.lst in a text editor and add the following lines:


title disk-installer
root (hd0,2)
kernel /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw
initrd /casper/initrd.gz


NOTE: the root line tells Grub which partition contains the installer. If in your case, the partition you created is /dev/hda1, you'll need to edit that line to root (hd0,0). As you can see, the partition number becomes number -1 as Grub starts counting from 0.

Next, reboot and choose 'disk-instaler' from the grub boot menu.

---

### Post by smdeep on 2007-05-11
Hi
I tried to install from hard disk. It boots but stops at :

[    4.304000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher

My laptop is a Toshiba Satellite A80.
Any idea?

Thanks in advance.

---

### Post by mikeymckay on 2007-06-02
> **smdeep said:**
> Hi
I tried to install from hard disk. It boots but stops at :
[    4.304000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher


I have the exact same problem. Any ideas?

---

### Post by CAsurfer on 2007-06-04
> **smdeep said:**
> Hi
I tried to install from hard disk. It boots but stops at :

[    4.304000] squashfs: version 3.2-r2 (2007/01/15) Phillip Lougher

My laptop is a Toshiba Satellite A80.
Any idea?

Thanks in advance.

I also have exactly the same problem.  Any ideas?

---

### Post by tuxcantfly on 2007-06-04
3 other alternate install methods, neither of which require a CD, and options 1 and 2 don't even require any partitioning, and they all have nice, user-friendly GUIs:

If you're already running Linux, and want a loopomounted install:
[http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918)

If you're already running Windows, and want a loopmounted install:
[http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

If you're already running Windows, and want a real install:
[http://ubuntuforums.org/showthread.php?t=427540](http://ubuntuforums.org/showthread.php?t=427540)

---

### Post by mikeymckay on 2007-06-04
> **tuxcantfly said:**
> 
If you're already running Linux, and want a loopomounted install:
[http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918)


Tried it. The idea was cool, even if I was a bit freaked out by running a big script as sudo. Anyways, I got a memory allocation error when it tried to boot up. I think I must have something fundamentally wrong with this approach.

---

### Post by tuxcantfly on 2007-06-04
> Tried it. The idea was cool, even if I was a bit freaked out by running a big script as sudo. Anyways, I got a memory allocation error when it tried to boot up. I think I must have something fundamentally wrong with this approach.

Memory allocation error? Mind reporting a more specific error to the dedicated thread itself at [http://ubuntuforums.org/showthread.php?t=441918](http://ubuntuforums.org/showthread.php?t=441918) ? Like at which stage was this, before or during the d-i installer, on the first bootup after the d-i installer, or when? Exactly what was the error, word-for-word? Did this error occur only with the Lubi installer, or with other Ubuntu installs on the same computer?

---

### Post by UberKnight on 2007-10-11
> **mikeymckay said:**
> I have the exact same problem. Any ideas?
I'm also experiencing exactly the same problem.  Any solutions yet anyone?

---

