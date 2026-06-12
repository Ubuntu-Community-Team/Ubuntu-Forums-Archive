---
title: "Using Ubuntu on USB fully"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by ritchie_281 on 2008-07-15
I would like to install Ubuntu onto a USB key so I can take that with me and use it on any computer. First of all, what size USB key would be best to have for having Ubuntu plus some GBs more to store files, programs on etc.
Another thing, can I save files on my USB key, say for example I´m on Ubuntu on my USB key and I make a notepad file and save it on the key, if I visit another computer with that key will it still be there or are all details lost once I remove the usb key?

Does anyone know any sites where it tells you step by step how to install Ubuntu onto a USB Key?

Thanks

---

### Post by bobnutfield on 2008-07-15
This will give you all the information you need:

[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")

However, let me caution you that if you want to use the stick with another computer make sure you install grub to the pendrive and NOT the MBR when installing.  Many make this error when installing to a pendrive and if you do that then you will have to have the pendrive inserted to properly boot your computer.  

Bob

---

### Post by ritchie_281 on 2008-07-15
Well I want it so that ubuntu wont load unless I have the pendrive connected, basically the pendrive being a harddrive with ubuntu installed on.. would I need grub or MBR for that?

---

### Post by bobnutfield on 2008-07-15
When you install to a pendrive, Ubuntu will ask where you want to install the Grub bootloader.  If you choose your MBR (master boot record) it will prevent you from booting that computer unless you have the pendrive inserted.  But you said you wanted it to be portable to another computer, so you MUST install grub to the pendrive and on the alternate computer choose to boot from the USB device.  There are complete instructions and tutorials on the link I provided.

Bob

---

### Post by bumanie on 2008-07-15
Presuming you have 8.04 installed on your computer, I used this guide to ahieve what you are looking for - the usb boots off the usb and is independant of the computer it is used on.  [http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/](http://www.pendrivelinux.com/2008/05/15/usb-ubuntu-804-persistent-install-from-linux/) Not all computers will boot this way (some older motherboards won't), but most do.

---

### Post by ritchie_281 on 2008-07-15
No I have Windows install on my computer, I am looking to do this: [http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-via-the-live-cd/)

Though I read that Puppy Linux would be good as it is quicker and smaller.. anyone know any links as to how I can do that?

---

### Post by bobnutfield on 2008-07-15
I use puppy occassionally, and it is very good and very small.

[http://www.puppylinux.org/]("http://www.puppylinux.org/")

---

### Post by LowSky on 2008-07-15
Puppy is great but If you want a ubuntu based release like Xubuntu, it will work on more hardware than regular Ubuntu. Don't forget to not enable anything like compiz or graphic drivers, keep it simple.

I say use at least a 8GB drive so you have some space for files and what not. At the same time create a seperate partition so that you can access some files without always having to boot up if another OS is already loaded. I love to carry extra programs like OpenOffice (for windows) if my friends need something and have no access to the internet

---

