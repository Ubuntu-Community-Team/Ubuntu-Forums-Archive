---
title: "multibootusb and persistence"
date: 2012-09-01
forum: New to Ubuntu
---

### Post by active1 on 2012-09-01
hi, i want to use MultiBootUSB to create a bootable lubuntu flash usb
and i want it to be persistence
how can i do that in MultibootUSB ?? or is there any other application that can create the persistent separtely ?
i know that there is other applications to create persistent bootable usb (like UNetbootin, Universal USB Installer, LiLi, etc..) but i want to use MultibootUSB because it is the only one that makes the system boots very fast compared to the others.

i need some help :(

---

### Post by active1 on 2012-09-01
update
i added "persistent" to the syslinux.cfg file (at the end of append line)
and i created a casper-rw raw file (1000 MB) in the multibootusb directory, but when i boot, the system is not persistence too :(

i noticed this while booting:
```
/init: line 7: can't open /dev/sr0:no medium found

```

what should i do ???

---

### Post by oldfred on 2012-09-01
I have not used the Multi-boot, but have suggested it. It really is for installing more than one ISO. But you can only have persistence for one of the installs.

Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)

If flash drive is large and you want full updating, you can do a full install and still use grub2 to boot other ISOs.

Has some details on the setting of persistence.
Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by C.S.Cameron on 2012-09-01
> **active1 said:**
> update
i added "persistent" to the syslinux.cfg file (at the end of append line)
and i created a casper-rw raw file (1000 MB) in the multibootusb directory, but when i boot, the system is not persistence too :(

i noticed this while booting:
```
/init: line 7: can't open /dev/sr0:no medium found

```

what should i do ???

How did you create the casper-rw file? I copy mine from a never used usb-creator install.

As Oldfred says you can also create a ext2, 3 or 4 partition named casper-rw, (and home-rw).

Things can go a little wonky if you use the persistence file, or partition, for more than one distribution on a multiboot.

I have only managed to get this method working with 'buntus.
There are other methods for getting persistence working for other Linux, I recall discussing Puppy elsewhere in the MultiBootUSB thread.

See also:

[http://ubuntuforums.org/showthread.php?t=1518273&page=5](http://ubuntuforums.org/showthread.php?t=1518273&page=5)  #41

---

### Post by O2Blevel on 2012-09-01
> **active1 said:**
> update
i added "persistent" to the syslinux.cfg file (at the end of append line)
and i created a casper-rw raw file (1000 MB) in the multibootusb directory, but when i boot, the system is not persistence too :(

i noticed this while booting:
```
/init: line 7: can't open /dev/sr0:no medium found

```

what should i do ???

You should add "persistent" to the appropriate cfg file in the menu folder not to syslinux.cfg

Edit: Sorry, I'm in a daze today, ignore my post, it's for YUMI not multiboot.

---

### Post by C.S.Cameron on 2012-09-01
> **O2Blevel said:**
> You should add "persistent" to the appropriate cfg file in the menu folder not to syslinux.cfg

Yes edit grub.cfg in the grub folder. 
The casper-rw file should be located in the root of the USB.

---

### Post by active1 on 2012-09-02
thank you all for replying

> How did you create the casper-rw file? I copy mine from a never used usb-creator install.
i created it with PDL-Casper-RW-Creator

> **C.S.Cameron said:**
> Yes edit grub.cfg in the grub folder. 
The casper-rw file should be located in the root of the USB.

but where is the root folder (of the usb) ? :p
there is a folder named "grub" inside the "boot" folder, and there is one cfg file in that grub folder, it is loopback.cfg 
i edited it this way:

```
menuentry "Try Lubuntu without installing" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/lubuntu.seed boot=casper iso-scan/filename=${iso_path} quiet splash -- persistent
    initrd    /casper/initrd.lz
}
menuentry "Install Lubuntu" {
    linux    /casper/vmlinuz  file=/cdrom/preseed/lubuntu.seed boot=casper only-ubiquity iso-scan/filename=${iso_path} quiet splash -- persistent
    initrd    /casper/initrd.lz
}
menuentry "Check disc for defects" {
    linux    /casper/vmlinuz  boot=casper integrity-check iso-scan/filename=${iso_path} quiet splash --
    initrd    /casper/initrd.lz
}
menuentry "Test memory" {
    linux16    /install/mt86plus
}
```

and i added the casper-rw raw file in that grub folder too, but nothing changed :\

any idea ? maybe i should add the directory of the casper-rw file with a command in the loopback.cfg file ?

---

### Post by active1 on 2012-09-03
those are the folders and files inside USB/multibootusb :
```
.   chain.c32  Lubuntu-12-04  menu.c32        vesamenu.c32
..  grub.exe   memdisk          syslinux.cfg

```and inside USB/multibootusb/Lubuntu-12-04 :
```
.         boot    .disk    isolinux      pool              wubi.exe
..         [BOOT]  dists    md5sum.txt  preseed
autorun.inf  casper  install  pics      README.diskdefines
```where should i put the casper-rw file ? :p

---

### Post by C.S.Cameron on 2012-09-03
> **active1 said:**
> 
but where is the root folder (of the usb) ? :p
 ?

If your flash drive is sdc1 then put casper-rw in sdc1.
If you are using a casper-rw partition, make it sdc2


If using Windows and flash drive is E:\ put casper-rw there.

Don't put it in any folder on the drive, it should sit beside the highest level folder.

---

