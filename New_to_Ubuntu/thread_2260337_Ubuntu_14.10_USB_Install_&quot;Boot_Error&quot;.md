---
title: "Ubuntu 14.10 USB Install &quot;Boot Error&quot;"
date: 2015-01-11
forum: New to Ubuntu
---

### Post by Miguel_Mallari on 2015-01-11
Soo, I downloaded ubuntu 14.10 64x bit iso, then put it on my 8GB USB, I closed my laptop then plugged the USB in and opened the laptop, I press F12 to "Boot Menu", then I clicked "USB Flash Drive" (Something like that), then it said "Boot Error"... Please help :1

---

### Post by sudodus on 2015-01-11
Welcome to the Ubuntu Forums :-)

Did you check with md5sum that the download was good? See this link [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

How did you put Ubuntu into your USB pendrive? There are several alternatives, see [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

-o-

Please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

Are you running Windows in the computer? Do you want to keep it and make a dual boot?

Knowing these things makes it easier to help.

---

### Post by nerdtron on 2015-01-11
> I downloaded ubuntu 14.10 64x bit iso, then put it on my 8GB USB,

Just copied and paste the ISO file to the USB? That's not going to work since you really need to "burn" the iso (like burning a CD).

Here's an easy to follow tutorial with lots of screenshots: [http://www.wikihow.com/Make-a-Bootable-Ubuntu-with-USB-Drive-Using-UNetbootin](http://www.wikihow.com/Make-a-Bootable-Ubuntu-with-USB-Drive-Using-UNetbootin)

---

### Post by Miguel_Mallari on 2015-01-11
no I burned it into the usb and made it a bootable usb

---

### Post by Miguel_Mallari on 2015-01-11
I used the [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
I am wanting to try Ubuntu 14.10 on my old laptop, it is a Dell Vostro 1500, 3 GB Ram, Intel(R) Core(TM)2 Duo CPU T250.

---

### Post by sudodus on 2015-01-11
It should be possible to run standard Ubuntu in that computer, but maybe the flavour Xubuntu with a lighter desktop environment might work better.

Remember to check that the download was good: see post #2.

But you may have problems installing 14.10 unless you use [mkusb]("https://help.ubuntu.com/community/mkusb") from linux or [Win32 Disk Imager]("https://wiki.ubuntu.com/Win32DiskImager/iso2usb") from Windows. It might be a better idea to try Ubuntu or Xubuntu version 14.04.1 LTS for two reasons. This version has long time support (Ubuntu until April 2019 and Xubuntu until April 2017), while 14.10 is supported only 9 months (from October), so only until July 2015. And 14.04.1 LTS can be installed (copied, flashed) to a USB pendrive with many of the installing tools, for example [Unetbootin]("http://zleap.net/unetbootln-usb-how_to/"), that works from linux as well as from Windows (different versions with very similar graphical user interfaces).

---

