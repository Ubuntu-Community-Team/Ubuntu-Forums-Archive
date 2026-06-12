---
title: "Dual boot usb"
date: 2013-10-06
forum: New to Ubuntu
---

### Post by kmb9205 on 2013-10-06
hi everyone, I am new to linux and have installed Ubuntu 12.04 LTS. I have a few old computers laying around and wanted to experiment a bit. I also have some friends who want me to install a dual boot system on their computers so that they can play also. I installed my own distro using a pendrive. I then found kubuntu and installed it on another pendrive. My friends would like kubuntu and I was thinking the same thing for a laptop of mine. Is there a way of moving both Ubuntu and Kubuntu onto a single (large enough) USB? I would like it to be selectable to either Ubuntu or Kubuntu at booting. I know that this has been discussed more than a few times but the info that i am finding all around the web is conflicting and or dated. I have gParted as well as both .iso 

Any help is again appreciated.

---

### Post by heir4c on 2013-10-06
Multisystem is perfect for that. I have a 32GB usb with 21 distro's on:
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

[IMG]http://i.imgur.com/HtclIvi.png[/IMG]

---

### Post by oldfred on 2013-10-06
There are several scripts that automate the process. Multisystem is one. I manually did it before scripts became available and just installed grub2, created a grub.cfg with loopmount boot stanza (copied from examples) and copied ISOs onto flash drive.

 These are scripts to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk w/grub2
[https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk](https://help.ubuntu.com/community/InstallAndBootMultipleLinuxFromPendriveFlashDriveUSBDisk)
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://sourceforge.net/projects/multibootusb/files/](http://sourceforge.net/projects/multibootusb/files/)
[https://sourceforge.net/projects/multibootusb/files/](https://sourceforge.net/projects/multibootusb/files/)
MultiSystem Another LiveUSB Multiboot French(translate) w/grub2 
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
[http://ubuntuforums.org/showthread.php?t=2175738](http://ubuntuforums.org/showthread.php?t=2175738)
Another: multiboot055.sh
[http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/](http://blog.p-mt.net/blog/2009/12/27/multiboot-usb-stick/)
See yumi for multi-boot versions
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)


 Multiple-Boot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
Examples:
Label partition - if label is grub2 & mount:
sudo grub-install --root-directory=/media/grub2 /dev/sdb
Newer versions automount with $USER name also, this one labeled MC4GB
sudo grub-install --root-directory=/media/fred/MC4GB /dev/sdb
Install grub2 2.00 boot loader to gpt partitioned flash drive from Raring (it used media/fred as mount)
mount and label is PreciseInstaller and flash is sde. Note space before /dev/sde
sudo grub-install --root-directory=/media/fred/PreciseInstaller /dev/sde
This will create a grub.cfg or you can just copy your own grub.cfg into /boot/grub
sudo grub-mkconfig -o /media/fred/PreciseInstaller/boot/grub/grub.cfg
Only if Linux formatted, easier with wide open permissions. 777 otherwise not normally suggested.
sudo chmod 777 -R /media/fred/PreciseInstaller/boot

   More Details:
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)
Install grub2 to USB -general info, note that path for 12.10 and later to flash drive includes your $USER name
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)

   [https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2](https://wiki.archlinux.org/index.php/GRUB2#Booting_an_ISO_Directly_From_GRUB2)

You can do the same from a hard drive. Makes installs a lot faster.

 This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by kmb9205 on 2013-10-06
Thanks much heir4c and oldfred

---

### Post by heir4c on 2013-10-07
We are on this world to help one another.
One thing: Not every ISO can be used. There is a list with many distro's. On the right of my screenshot you see a button with a globe, click on that to see the list. If you doubleclick on the distro then you go automatic to the site of that distro and download from there. (Sometimes it will work even it is not in that list, when you download a iso by yourself, but then you have luck :) and sometimes the new versions don't work even it is in the list. but in 95% it will work.)

---

### Post by kmb9205 on 2013-10-07
thanks again

---

### Post by oldfred on 2013-10-07
One advantage of the scripts as heir4c suggests is that they have the correct boot stanza for the ISO they list. 

Sometimes I have had to "cheat" and look at one of their boot stanzas to figure out how to boot something. And even some Ubuntu ISO like server & alternative do not work.
I tend to prefer the one's that use grub2, but different scripts use different boot loaders and all seem to work at least for some users.

---

### Post by heir4c on 2013-10-07
Yes, it is not always work, but for install a "normal" iso it is useful and easy. 
One thing is required is a PC/laptop who can boot from usb. 
What I do is, I download the ISO and move it from in Nautilus to the open space in the program on the bottom of the screen. (you must place it right, you will see a big cursor turn up in the field, than you can release the mouse button)  It starts automatic and ask to enter your password (it need rootrights)

---

