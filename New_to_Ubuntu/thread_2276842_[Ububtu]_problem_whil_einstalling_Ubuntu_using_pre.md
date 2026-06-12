---
title: "[Ububtu] problem whil einstalling Ubuntu using preseed"
date: 2015-05-05
forum: New to Ubuntu
---

### Post by neel5 on 2015-05-05
Based on the original ISO for Ubuntu 12.04, a custom ISO was produced which merely included extra packages. It's then written to a USB/CD memory with unetbootin. Then isolinux/isolinux.cfg is modified where automatic-ubiquity is added as a kernel parameter along with the preseed file to use. This is with the intention of automatically starting Ubiquity to automate the install when my system boot through USB/CDROM.
This does not work at all. It didnot work with only-ubiquity also.
Pls help where should i add ubiquity--atomatic to launch auto install.

---

### Post by dino99 on 2015-05-05
try pendrivelinux instead of unetbootin  [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by neel5 on 2015-05-05
Dropped an idea of making USB UNetBootin but would like to make custum iso and offer mount ISO though NFS.
Can you advise where to add ubiquity--automatic.

thanks

---

### Post by Vladlenin5000 on 2015-05-05
Perhaps testing your ISOs the good ol'fashion way - burning in a physical media or using it to create a VM - should come first. Assuming you already checked that the second troubleshooting step should be the USB dingle itself. Does it boot with a regular Ubuntu ISO in a USB made the usual way (UNetBootin, Ubuntu's satartup disk creator, etc.)? Assuming it boots a regular Ubuntu ISO but not yours then perhaps it's time to consider tools that don't screw up certain ISOs, the aforementioned plus Multisystem.  Give **SUSE Studio Imagewriter** a chance? Or just use *dd* (be carefull, be extremelly carefull, check the destination drive twice!)... [32-bit]("http://download.opensuse.org/distribution/13.2/repo/oss/suse/i586/imagewriter-1.10.1396965491.a4dcffa-3.1.4.i586.rpm") [64-bit]("http://download.opensuse.org/distribution/13.2/repo/oss/suse/x86_64/imagewriter-1.10.1396965491.a4dcffa-3.1.4.x86_64.rpm")  Obs.: Ubuntu, like all Debian based distros, use DEB packages. RPM packages are therefore alien to Ubuntu. You must use *alien* to install. ;)  Or just use *dd...*

---

### Post by neel5 on 2015-05-06
It seems i should be more mature in linux to understand your advice. Below is my requirement.

* Download Ubuntu ISO 12.04
* UnSquash filesystem add/delete some packages
* Squashfs, Provide custom_preseed file to answer all installation questions and partition
* make new ISO
* Create new VM in ESX, mount ISO and boot.
* Loads ISO If i run ubiquity --automatic (terminal) which starts and completes installation successfully.

what i wish is to avoid loading and then running "ubiquity --automatic" in termainal. As soon as i mount and boot it should shoul start installation and complete headless.

To do so i tried modifying iso file extract-iso/isolinux/isolinux.cfg
edited the following line: set as default first label with timeout 10.

Label Install
  menu label intall
  kernel /casper/vmlinuz
  append file=/cdrom/preseed/custom.seed keyboard-configuration/layoutcode=us boot=casper initrd=/casper/initrd.gz automtaic-buiquity quiet splash --

Tried to replace with "only-ubiquity" it doesnot help.

---

### Post by VMC on 2015-05-06
Here is some examples of unattended installs with some preseed examples: [http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu](http://askubuntu.com/questions/122505/how-do-i-create-a-completely-unattended-install-of-ubuntu)

edit: I could never get preseed to work as intended either, so I interested in this topic. I forgot about it until now.

---

