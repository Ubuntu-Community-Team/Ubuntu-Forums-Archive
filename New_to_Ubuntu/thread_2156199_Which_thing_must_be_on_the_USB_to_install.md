---
title: "Which thing must be on the USB to install?"
date: 2013-06-20
forum: New to Ubuntu
---

### Post by caraj on 2013-06-20
I've tried the thing from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)  and the thing from [pendrivelinux.com]("http://www.pendrivelinux.com/"), but is there something I've done wrong?
Does anything have to be done to those files after being inserted onto my USB that I haven't done? Here was my process: after loading them tio the USB  I've just inserted the USB into the laptop and selected "boot from USB".
Anyway, it doesn't work.
The HD is blank, with no OS. The machine is a Dell Latitude D600. RAM 512 MB, Ghz about 2.
What do I do?

---

### Post by monkeybrain2012 on 2013-06-20
What do you mean by "inserting the iso"? 

Anyway if the pen-drive linux thing doesn't work try LILI

[http://www.linuxliveusb.com/](http://www.linuxliveusb.com/)

Edited: Just the disclaimer that the live-usb creator may contain a Trojan, [http://www.pendrivelinux.com/liveusb-install-live-usb-creator/](http://www.pendrivelinux.com/liveusb-install-live-usb-creator/) 
So I would use LILI or unetbootin if I were on Windows.

---

### Post by mastablasta on 2013-06-21
once you download the .iso file make you you do md5sum check first: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

then use lili or unetbootin. you can then do a disk check before booting into the OS to see if all files were moved correctly to USB.

also use Lubuntu or Xubuntu on that mashcine. Ubuntu might struggle.
[http://www.lubuntu.net/](http://www.lubuntu.net/)
[http://xubuntu.org/](http://xubuntu.org/)

also some old maschines just can't boot from USB. if you have a floppy disk you can use PLOP boot manager to boto from the floppy first and then select USB there to continue boot from USB: [http://www.plop.at/en/bootmanager/index.html](http://www.plop.at/en/bootmanager/index.html)

---

