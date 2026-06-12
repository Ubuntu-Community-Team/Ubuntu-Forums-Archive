---
title: "Install ubuntu installer on usb drive"
date: 2008-05-05
forum: Philippine Team
---

### Post by jmazaredo on 2008-05-05
Nag ka problem ako sa pag install nang linux
1)wala ako cdrom
2)wala ako floppy
3)hindi ako marunong mag loop da loop sa hard drive

ang natirang opsyon = may usb drive ako na 1 gig!

kaya nag hanap ako nang solusyon eto ang nangyari

Kinalkal ko ang hdd ko kung meron ako ISO Image nang linux may nakita ako CENTOS, MANDRAKE at Ubuntu syempre 1 gig lang ang thumb drive automatic ubuntu.

Mga kailangan
1)internet
2)usb drive
3)poweriso o kahit anung virtual drive manager na nakakabasa nang iso image o kaya ay winrar
4)mag download nang syslinux (i-google mo baby)


1) mag download nang vmlinuz at initrd [dito]("http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/hd-media/") 

2) i-format ang usb drive nang fat32
3) gumawa nang folder na ang ngalan ay install
3) kopyahin ang vmlinuz at initrd na dinowload sa folder nang install
4) kopyahin ang iso image sa root nang usb drive
5) gawing bootable ang usb drive gamit ang syslinux 
    ( syslinux f: ) o kung anung letter and drive letter nang usb
6) i-mount mo ang iso image nang linux at kopyahin ang isolinux na folder sa root nang usb drive
7) i-rename ang isolinux na folder na kinopya sa syslinux
8) pumasok sa folder na syslinux (yung nirename mo) at hanapin ang isolinux.cfg at irename sa syslinux.cfg

Next up is testing the thumb drive d ko pa nasubukan ang mini type gagawin ko sa susunod

NOTE: GOT PROBLEM! KAILANGAN ATA PAREHAS UNG BOOT IMAGE PTI YUNG ISO 

ang binasa ko na [guide]("http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html")

---

### Post by robinx1578 on 2008-05-05
We have the same problem before. Just check your pc bios if you can can boot on usb then its possible to put ubuntu on your flash drive... Im running ubuntu on my usb hard Drive... 

the first thing you should do is to make sure that your pc can boot on flash drive... Then try downloading the flash drive format utility tools.(USB Disk Storage Format would help)

---

### Post by Nhatz on 2008-05-06
Pwede dudes.... nagawa ko na dati yun.
here's the link. [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610/)
Astig!:guitar:

---

### Post by SHENGTON on 2008-05-07
Here's how to install Ubuntu Hardy Heron using USB flash drive. --> [HERE](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

---

