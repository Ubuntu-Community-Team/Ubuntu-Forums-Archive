---
title: "How to make a ubuntu live usb hdd"
date: 2005-12-10
forum: Outdated Tutorials &amp; Tips
---

### Post by pomalin on 2005-12-10
This is how I made my ubuntu live usb (USBuntu) and the bootcd to boot on older computer that not have boot from usb. updated 19/12/2005 
I have two partitions in fat32 on a cibox proton 2gigas, so I can share in one partition with other systems.

 
Base on howto by DaBruGo and henk.1955 here. [http://ubuntuforums.org/showthread.php?t=71567&highlight=initrd#top](http://ubuntuforums.org/showthread.php?t=71567&highlight=initrd#top)

Use of mybuntu for building own live cd.
here: [http://stuporglue.com/content/view/29/35/](http://stuporglue.com/content/view/29/35/)

dependencies:

sudo apt-get install cloop-utils mkisofs gcc netpbm syslinux qtparted





(1 ) Format usb hdd in fat32 with windows xp or qtparted, why xp or qtparted? because I don't know why but, the partitions made by gparted don't work with grub-install.

(2 ) Boot your computer with ubuntu desktop.

(3 ) Plug usb hdd while your in your session

(4 ) put the live cd in. 

(5) with gnomebaker make an ubuntu.iso with the live cd.



A/ This part concern the personnalisation of the cd just go to the number part if you don't want to personnalize the live.

(a) take mybuntu here: [http://stuporglue.com/content/view/29/35/](http://stuporglue.com/content/view/29/35/)

(b) extract to your home and put the ubuntu.iso in.

(c) in the folder mybuntu/conf open chrootscript with gedit and correct that :

if [ "$INSTALL_CUSTOM_PACKAGES" == "Yes" ]; then
	apt-get install `cat conf/install_me | grep -v \#`
fi

if [ "$REMOVE_CUSTOM_PACKAGES" == "Yes" ]; then
	apt-get remove `cat conf/remove_me | grep -v \#`
fi
 
in that :

if [ "$INSTALL_CUSTOM_PACKAGES" == "Yes" ]; then
	apt-get install `cat install_me | grep -v \#`
fi

if [ "$REMOVE_CUSTOM_PACKAGES" == "Yes" ]; then
	apt-get remove `cat remove_me | grep -v \#`
fi

(d) open in mybuntu/conf again options.conf  and put Yes or No where you want Yes or No :D

(e) inside install_me put packages that you want to add with the good name for exemple :    language-pack-support-fr  .

(f) inside remove_me put what you want to remove

(g) inside sources.list you can put your sources.list if you say Yes in options.conf of course.

(h) now to make a home with your bookmarks, and configuration just read the readme in mybuntu, it's clear and fast :D

(i) Here we go, for about 40 minutes to build the iso, i got 1 giga swap / 7 gigas free space / ram 512 / athlon-m 2200+ 1.8ghz.

(j) open up a terminal  and cd mybuntu

(k) sudo ./makemybuntu.sh

(l) Be patient, say yes for updates and installations.

(m) Now you got your iso if it fits in a cd burn and test, or with qemu
: qemu -cdrom votre.iso

Now let's get back to numbers


(6 ) Right clic on iso

"open with file roller" ...
"Edit /select all" ...
"Ediion /Extract" ...
"Extract to folder" (here extract to your usb hdd) ...
* all files ...
* Recreate files ...
* erase existing files ...
"Extract"

Pof, all goes on usb hdd.

(6 ) in a terminal

sudo su -- 
mount /dev/sda1 /mnt (use correct parameters!!)
grub-install --root-directory=/mnt /dev/sda
umount /mnt
exit
exit


(8 ) in the folder /boot/grub of the usb hdd create menu.lst (I leave like in the dabrugo how to except for the -fr- part)

# Default to first menu entry
default saved

# Allow 30 seconds before booting default
timeout=30

# Use prettier colors
color cyan/blue white/blue

title UBUNTU Live USB (henk.1955 version)
root (hd0,0)
kernel /install/vmlinuz casper/enable=true casper-udeb/snapshot/backing-file=/cdrom/casper/filesystem.cloop vga=792 ramdisk_size=1048576 root=/dev/rd/0 rw debian-installer/locale=fr kbd-chooser/method=fr --
initrd /install/initrd.gz
savedefault

(9 ) We will now change the initrd to be recognize as a cdrom.

(10)download here [USBuntu.tar.gz]("http://usbuntu.info/resources/USBuntu.tar.gz") and extract the same way as above in your usb hdd.

Ok now you got a bootable live usb hdd ubuntu.

To be able to boot this usb hdd with an older pc that can't boot from usb, you just have to do this steps :

In a folder USBboot (for exemple)

/Copy and paste the install and isolinux folders from the usb hdd

/in a terminal go to USBboot : cd USBboot

/now go to isolinux cd isolinux

/ put this with the RIGHT path at the end :  mkisofs -o USBboot.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table /home/RIGHTpath/USBboot

/Now you got your iso just right clic and burn.

/and after you can boot on the cd just push enter, and the initrd mount the usb hdd has a cdrom, after that the boot process continues and you can remove the cd ;).


That's all. I hope it will work for you for me it work realy well, tested on 4 differents pc's and allways rocks.

Here I have put two iso for booting from usb th USBootout.iso is for computers with internal hdd ide, and USBoot2.iso is for computers with ONE internal hdd in SATA.
When I have time to upload, I will also upload a version of the ubuntu live with the inirtd modified, so you will just have to extract and install grub.

---

### Post by matcram on 2005-12-15
hi

thx for your great and well down howto it worked like a charm for me except for the boot CD. I will try to see what went wrong.

In fact i was a bit disappointed because i tought i could be able to to run my USBubuntu like a desktop one (saving files, config and softs directly to the HDD).

Is it normal because it is based on a live CD that doesn't allow this or do i have to do something special to enable it ?

Thx again for your howto and plz excuse my english since i'm not from US ;-)

---

### Post by pomalin on 2005-12-15
hello, and thank you, for the home and the settingd, yes it's because it's live, but there's a way, here in this forum, but I don't remember where to do a persistent home for the lie.
For the cd, what went wrong?
Here I put two isos you can test, the first is to boot from usb hdd, with internal ide hdd and the second to boot from usb hdd with ONE SATA drive inside.

[http://www.usbuntu.info/page2.html](http://www.usbuntu.info/page2.html)

It's in french, sorry ;) my native language.

---

### Post by matcram on 2005-12-15
Doesn't matter, je suis français ;-) merci pour les iso je testerais demain.

---

### Post by cvmostert on 2006-02-07
Hi there, i also used your howto and it worked for me, thank you... i can boot from usbhdd, i just dont seem to be able to go online with Firefox? 

Gaim works and i can ping google... 

i disabled and enabled the network card and it still does not work... 

has to be something with Firefox?

help will be appreciated
Ciao

---

### Post by hks on 2006-02-15
Hi pomalin

Thanks a lot for all the info and work!

Unfortunately the link you refer to doesn't work:
[QUOTE=pomalin]
Use of mybuntu for building own live cd.
here: [http://stuporglue.com/content/view/29/35/](http://stuporglue.com/content/view/29/35/)
[/QUOTE]

can you please tell us the correct one?

Thanks again.

---

### Post by pomalin on 2006-02-17
Hi, the link is broken and I don't know if there's a new one, I have this script somewhere in my laptop but without permission from the author, I don't distribute it. Really sorry, you will have to follow the wiki to personalize the distro, or wait for dapper, and is persistent live, wich work like a charm.

---

### Post by h0meb0y25 on 2006-04-01
[QUOTE=pomalin]Hi, the link is broken and I don't know if there's a new one, I have this script somewhere in my laptop but without permission from the author, I don't distribute it. Really sorry, you will have to follow the wiki to personalize the distro, or wait for dapper, and is persistent live, wich work like a charm.[/QUOTE]


Hi There,

I have created 2 bootable CD's using the ISO's that u provided and tried to boot from my external USB HDD which has ubuntu installed on it .. but was not successful.

External USB Hdd is connected to the computer and when Boot screen for UBUNTU come using the bootable CD and I press enter.. system just hangs.

If i disconnect the USB hdd, and then again if i press enter i can see live CD working.

can u please help me on this i m a total newbie.

many thnx

---

