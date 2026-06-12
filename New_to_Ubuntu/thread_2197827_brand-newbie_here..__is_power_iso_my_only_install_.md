---
title: "brand-newbie here..  is power iso my only install alternative?"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by mauijim66 on 2014-01-05
i was planning on putting linux on the two new barebones systems i just built.  i had planned on downloading a copy of it with my laptop, saving the copy to a flash drive, and somehow installing it (haha i guess im hoping it will sort of 'run' itself)..
so the first thing i notice is that the downloaded file is an iso file.  no worries, as i have power iso on my laptop already.  then i see that my version of pwr iso will only convert files of up to 350 mb.  i have to pay 29$ for a better version of power iso to be able to convert the download files.
is this the only way?  can i use a flash drive?  any other tips?  thanks in advance for your time and patience..

---

### Post by hoopia on 2014-01-05
You will have to convert the ISO into a bootable USB. This can be done with UNETBootin:

[http://sourceforge.net/projects/unetbootin/](http://sourceforge.net/projects/unetbootin/)

Feed it the ISO file, and plug in your USB drive.

---

### Post by sotiris2 on 2014-01-05
Use [this](http://www.linuxliveusb.com/en/download) to make a live usb from windows, or [this](http://infrarecorder.org/) to burn an iso to cd. Then boot your system from whichever medium you prefer. Just a note if you pick to burn a cd (i would pick usb for faster) burn it on the SLOWEST possible speed.

---

### Post by flyfisherbryan on 2014-01-05
I strongly suggest a bootable usb if that is possible.  After you see it work you can pemanently install it.  Once you have the iso you can use this:

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

### Post by Impavidus on 2014-01-06
Never heard of power iso.

You can either burn the iso to a dvd (see [https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD), but you'll need a dvd nowadays) or burn it to an usb flash drive ([https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick), at least 1GB. I'm sure you have one spare). Most people prefer the usb. Remember to "burn" it, not copy the file. An iso is an image of an entire file system, including the code needed to boot the system, which must end up in the boot area of the live medium.

---

### Post by Bucky Ball on 2014-01-06
> **Impavidus said:**
> Never heard of power iso.

A Windows app.

Create a bootable USB dongle using one of the methods described here> 
Reboot to your BIOS (or some machines F12 gives a boot device  list)> 
Change the boot order to boot from the USB>
Choose 'Try Ubuntu'>
If happy, install Ubuntu using the desktop icon.

---

