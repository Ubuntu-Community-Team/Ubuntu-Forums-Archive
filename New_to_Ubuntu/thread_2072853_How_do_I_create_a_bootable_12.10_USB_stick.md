---
title: "How do I create a bootable 12.10 USB stick"
date: 2012-10-18
forum: New to Ubuntu
---

### Post by oyoyoy on 2012-10-18
How do I go about creating a bootable USB stick when the Pen Drive USB installer give me no option to chose the Ubuntu 12.10 desktop?

[IMG]http://imageshack.us/a/img10/3784/no1210.jpg[/IMG]

I am using the latest version of the USB installer (available on their website) and I'm trying to use the recently downloaded ubuntu-12.10-desktop-amd64.iso from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) The installer does not auto detect my iso contrary to what is advertised.

Oy

---

### Post by arochester on 2012-10-18
Use the app: Unetbootin

It's available for Linux from repository. It's also available for Windows.

---

### Post by jerrrys on 2012-10-18
An earlier thread

[http://ubuntuforums.org/showthread.php?p=12302322#post12302322](http://ubuntuforums.org/showthread.php?p=12302322#post12302322)

more here

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=create+bootable+usb&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=create+bootable+usb&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by wojox on 2012-10-18
Select 12.10 Daily Build and set the path to the iso.

---

### Post by philinux on 2012-10-18
> **wojox said:**
> select 12.10 daily build and set the path to the iso.

+1. I guess they're a bit behind with the naming.

---

### Post by oyoyoy on 2012-10-18
Thanks a bunch for the help. I got the tip to use Unetbootin elsewhere on these forums and that worked a charm*. No idea if using the 12.10 daily option would indeed work. The fact that the installer explicitly warns you to set the correct build made me stay away from it.

As far as I'm concerned this issue is solved.

*The install went fine and Ubuntu started with no problem on a reboot. However, after visiting win7 on the same machine (it's a dual boot) and having it do it's disc-checks I am no longer able to boot into Ubuntu. After selecting Ubuntu in the grub I'm stuck on a black (grey) screen going nowhere. I somehow doubt it's got anything to do with the USB installer used, but figured it was worth mentioning. I best make another thread asking how to fix it...

Oy

---

### Post by C.S.Cameron on 2012-10-18
I prefer Startup Disk Creator from the Ubuntu Live CD.
If you don't want to burn a disk to make a USB you can make one using VBox.

---

