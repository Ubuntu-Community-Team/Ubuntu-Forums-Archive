---
title: "ubuntu 8.04 boot loader problem..pls help!!!"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by thunder901 on 2008-05-02
hey folks,
i recently tried installing ubuntu 8.04 into my usb harddrive but facing problem. its a 160gig which i partitioned 150gb ntfs for personal use, n 10gb unallocated in (disk management)windows vista. during installation process in the partitioner window, i use manual n create a new partition with the unallocated space with ext3 file system / root shown as /dev/sda2 and another partition sparing out 1gb for swap. in the install bootloader option, i get 3 options, 
(hd0) (this means the first hdd, but i disconnected my internal        hdd, so will my usb hdd be recognised as first hdd?)
/dev/sda - 160gb western digital
/dev/sda1 (which is my first partition)
/dev/sda2 (ubuntu partition)
previously i selected /dev/sda2, thinking the boot loader must be located in the same partition. it installs successfully, but whn i restart the computer, nothing happens. what went wrong here? am i supposed to select /dev/sda or (hdd0) or should i just format my usb hdd n do the whole process again. also i'm a bit confused abt the bootloader. does it/can it be installed in the same partition whr  os is installed or hdd device as such needs to be selected for boot loader install. what i'm tryin to accomplish here is whn i connect the usb hdd to a pc, n turn it on, it shud boot into ubuntu. please, help!!

---

### Post by benerivo on 2008-05-02
Sounds like you want to keep the internal drive clean and separate from the ubuntu installation as a a precaution/preference. The bootloader needs to go in the drive that the pc first tries to boot from, so you will need to set the pc's BIOS to first try to boot from the usb drive before the internal whenever you want to boot in to ubuntu. For the installation part, I think you can install the bootloader in your usb drive, but i would do it with your internal drive attached (ie. how it will be set up whenever you turn your pc on in the future). Select the usb drive as the target for the bootloader (might be called /dev/sdb if internal drive is attached), and forget about partitions, as there is a small space left at the start of all drives (ie. even before sdb1) which it will write it to.

---

### Post by thunder901 on 2008-05-03
installed the bootloader through the terminal grub and installed it on (hd0). at that time i disconnected my internal drive. so my usb had to be (hd0). now whn i reboot it says 
Grub Loading stage1.5 

Grub loading, please wait... 
Error 17

i have no idea how to go about the problem. if someone can please help me resolve this issue.

---

