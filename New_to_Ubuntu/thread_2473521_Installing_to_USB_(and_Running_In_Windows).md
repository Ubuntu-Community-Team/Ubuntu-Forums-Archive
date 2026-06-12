---
title: "Installing to USB (and Running In Windows?)"
date: 2022-04-06
forum: New to Ubuntu
---

### Post by odiousmelodious on 2022-04-06
Greetings,

I am familiar with ubuntu through school, but very new to actually using it on my own computers.

I am currently (but wishing I wasn't) a Windows user, and trying to find a way o transfer over to a linux system completely, although that will take time to accomplish.

To get started, I know it is possible to install and operate ubuntu from a USB drive, but I dont know the details of how to do it and have included two starter questions below.

1.) Do I need a completely fresh usb drive with nothing else on it?  Or can I put Ubuntu in a folder alongside other folders on the thumbdrive?

2.) Assuming it gets installed correctly, when you go to run ubuntu - can you run it inside windows, or do you have to redirect windows at startup/boot? 

Any helpful pointers much appreciated!

Thank you!

wm

---

### Post by oldfred on 2022-04-06
There is just boot of live installer, which can have persistence to allow saving some files/settings, but is not updateable.

There is a full install where you need two flash drives, a small one as installer (which does get erased) and another one to install into. If flash drive large enough you can have other partitions on it. Some choices may erase partitions, so often best to only use the Something Else install option.

And if newer UEFI system, you need to have an ESP on flash drive, otherwise  Ubuntu's Ubiquity installer puts the boot files on the internal drive's ESP. That works only if always using flash drive on same system.

Flash drives are slow particularly for writes. While putting full installs on most of my larger flash drives just for emergency boot with then larger data partitions, I now find an external USB SSD to be almost as fast as an internal SSD and faster than the installs to my internal HDD.
Flash drives also have limited life. Some better than others. Best to have good backups right from beginning.

Dual boot requires you to reboot system, and have Windows totally shutdown and fast start up/hibernation off.
Many suggest virtual installs. But they also suggest using Ubuntu and having Windows as virtual install as long as not gaming. Virtual installs are a bit slower. But if lots of RAM you can divide it up so systems run well.
Windows has WSL which used to be command line only, but WSL2 allows some gui. Do not know about it. But somewhat like a limited virtual install.

---

### Post by grahammechanical on 2022-04-06
The Ubuntu installer, which we call an ISO image, is 3.4 GB in size and requires a minimum of 4 GB of space on a USB memory stick. The Ubuntu installer (Ubuntu version 22.04) will offer you a full install or a minimal install. The full Ubuntu installation requires a minimum of 25 GB and the minimal Ubuntu installation requires 8.6 GB of space. The  process of creating a Ubuntu installer USB will erase all data that is already on the USB memory stick.

It is possible to dual boot Ubuntu and Windows whether they are both installed on the same drive or on separate drives. The Ubuntu installer will create a bootloader called Grub (GRand Unified Bootloader) that will offer a menu giving the option to boot either Windows or Ubuntu. The Windows boot loader will not recognize the existence of Ubuntu and so will only boot Windows.

You ask about running Ubuntu from inside Windows. Are you thinking about what are called Virtual Machines (VM)? You may find someone this forum who know how to do that but I think that question is more appropriate for a Microsoft forum.

Regards

---

### Post by mastablasta on 2022-04-07
> 

2.) Assuming it gets installed correctly, when you go to run ubuntu - can you run it inside windows, or do you have to redirect windows at startup/boot? 



it's an operating system like windows. can you run Android inside windows? or macOS inside windows? no. 

you can run some of the OS in virtual machines (such as virtual box) or emulators (such as DOSBox).
 
how to:
[https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview](https://ubuntu.com/tutorials/how-to-run-ubuntu-desktop-on-a-virtual-machine-using-virtualbox#1-overview)

But keep in find this is not the same as bare metal install and performance is also not the same but can be differently hit by virtualisation.

---

### Post by ActionParsnip on 2022-04-07
As far as I know, Ubuntu will need the whole usb and can't just be put in a folder. Considering how very cheap USB storage is you can grab a 32gb stick and be fine

---

### Post by C.S.Cameron on 2022-04-07
Persistent Install vs Full install
------------------------------------------------

Ubuntu can be installed to a USB in different ways. A **Live install** does not save between sessions. A **Persistent install** extracts the OS from a compressed file and saves data to an overlay file or partition each session, and a **Full install** installs the complete OS to the USB just like an install to internal disk.

**Comparison between Persistent and Full install USB**

**Advantages of a persistent install:**

1) You can use the persistent pendrive to install Ubuntu to another computer.

2) A persistent install takes up less space on the pendrive.

3) You can reset the pendrive by overwriting the old casper-rw file with a new one.

4) The install to pendrive takes less time.

5) Slightly less wear on the drive.

**Advantages of a Full install:**

1) You can update and upgrade.

2) If you have problems or wish to modify, the solution is the same as with an internal install, (You can ask for help in the forums).

3) No ugly startup / install screen.

4) Better security, you can use full encryption 

5) You can use proprietary drivers.

6)  Swapfiles and partitions work and Hibernation can be enabled.

7) Many persistent installs are limited to a 4GB casper-rw and a 4GB home-rw persistence file, to get more persistence requires persistence partitions. Once casper-rw is full, the drive will not boot.

8) More efficient usage of disk space. Does not require reserved space for persistence.

9) Faster boot, no automatic disk checking or Try Ubuntu/Install Ubuntu screen.

10) You can run VBox and use virtual machines.

11) Generally faster boot than Live or Persistent USB's.

12) More stable, better for day to day use. I have run Ubuntu off a flash drive for 5 years making only LTS upgrades.

Note that once booted, both methods run at about the same speed. If the computer has lots of RAM Ubuntu should run mainly in RAM and there will not be a big difference between running off internal HDD and USB3 flash drive f.**Full Install Method**

A quick and easy method to flash a Full install to USB can be found here: [https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi](https://askubuntu.com/questions/1300454/easy-full-install-usb-that-boots-both-bios-and-uefi)

A more traditional methods for creating a Full install USB from scratch can be found here: [https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-st](https://askubuntu.com/questions/1217832/how-to-create-a-full-install-of-ubuntu-20-04-to-usb-device-step-by-st)


**Persistent install method**

The following tools can  be used to make a Persistent install USB: **mkusb** - [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb), **Rufus** - [https://rufus.ie/en/](https://rufus.ie/en/), **Universal USB Installer** - [https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](https://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/), **Ventoy** - [https://www.ventoy.net/en/index.html](https://www.ventoy.net/en/index.html), ** YUMI** - [https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/). and others.

**mkusb** is my favorite tool for making Persistent USB's [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb). It creates boot partitions that allow it to boot in BIOS or UEFI mode. It puts the OS on a read only ISO9660 partition that is difficult to corrupt. Persistence goes on an ext4 partition who's size is only limited by USB size and it will make a NTFS data partition so you can save data from a Windows or a Linux computer

---

