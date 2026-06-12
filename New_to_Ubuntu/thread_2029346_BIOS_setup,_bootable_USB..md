---
title: "BIOS setup, bootable USB."
date: 2012-07-19
forum: New to Ubuntu
---

### Post by KL_72_TR on 2012-07-19
Hello.
I have just created a bootable USB (in Ubuntu 12.04), using UNetbootin. But unfortunately I can't set up BIOS to boot from the USB.
Motherboard: Gigabyte G41MT-D3V
BIOS version: F2
Any idea?
Thank you all.

---

### Post by richpri on 2012-07-19
Can your pc boot from a CD?  If so then that may be your only option.

---

### Post by z3nhakr on 2012-07-19
does your bios have a boot menu? it's f12 on mine (instead of pressing f2 for setup) if so can you see your usb there?

---

### Post by KL_72_TR on 2012-09-03
Hello
It has been a long month in vacation, and for that I beg you to forgive me for not replying.
After many tries I did it to boot from the USB and complete the installation of Ubuntu 12.04.
> **richpri said:**
> Can your pc boot from a CD?  If so then that may be your only option.No. I've removed completely CD drives. I found CD-s difficult to manage data on them. Many burning processes gone bad. Wasted time and money This is the reason why I'm using USB-s.

> **z3nhakr said:**
> does your bios have a boot menu? it's f12 on mine (instead of pressing f2 for setup) if so can you see your usb there?You are right. F12 works for me too. But the problem I found had to do with the USB I was using.
The first USB I was using had troubles. BIOS set up was correct to boot from a USB drive, but sometime BIOS could not detect it, at all!
Some other times the boot process was successful and in to the menu of; Unetbootin: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/), Universal USB Installer: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) and other programs I used, selecting: Install Ubuntu.
The beginning of installations looked OK, but at some point installation stopped complaining about HDD errors, or burning the CD with a lower speed.
Also one time the installation completed, but I had access only to the virtual console.
But every time I selected from the initial menu: Try Ubuntu, everything was OK.
At some point I recalled that I had made a mistake with this USB.
I had formated it without unmounting it first. So, I picked another USB. And this time creating the Live USB, booting and installing Ubuntu went by the book.
The only mistake I did this time was using _WindowsXP_ with LinuxLiveUSBCreator: [http://linuxliveusb.com/](http://linuxliveusb.com/)
So, the next time I will keep an eye on the USB.
Also I found out now that the first USB has problems with everything I put on it.
Everything inside a folder disappears, everything must end with an extension: .txt .exe or the data get corrupted and/or erased, PDF-s are unusable.
Basically now I can use it only for: .jpg .mp3 .mp4. But I try to convert every .mp3 to .ogg ...?
Thank you all and hope not to be kicked for replying so late.

---

