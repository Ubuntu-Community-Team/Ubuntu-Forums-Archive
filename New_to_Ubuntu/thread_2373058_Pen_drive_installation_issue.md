---
title: "Pen drive installation issue"
date: 2017-10-02
forum: New to Ubuntu
---

### Post by apmbrady on 2017-10-02
I was trying to install ubuntu onto a USB to allow for me to take ubuntu with me. It took a little bit to get it installed (not sure if I did that correctly) BUT I am able to boot into ubuntu with the USB attached. I can also boot into windows 7 (main hd on the laptop) while the USB is installed. 

When I boot up my computer without the USB installed it goes right into grub recovery. No commands work (with exception of ls).... help

---

### Post by yancek on 2017-10-02
If this is an MBR install (which would be the default with windows 7) you probably accepted the default for bootloader installation when you installed Ubuntu to the  USB.  It would install boot code to the MBR of the first drive (your internal drive) and that explains the behavior you are seeing.  If you want the internal drive with only windows 7 (?) to boot itself you need to reinstall windows boot code to the MBR of that drive with your windows installation disk using the Repair option then install Grub boot code to the MBR of the flash drive.

Best to post more details so we know exactly what you have.  You can download and run the boot repair software from the site below and select the Create BootInfo Summary option and post the link you get there.

    [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by apmbrady on 2017-10-03
I was able to get this to work. 

I downloaded easybcd ([http://neosmart.net/EasyBCD/](http://neosmart.net/EasyBCD/))

And restored then boot loader for windows 7. I reinstalled on pendrive and it seems to be working. Thank you!

---

### Post by C.S.Cameron on 2017-10-03
I've used easybcd for years booting Win 7 and Win XP without problems.

---

