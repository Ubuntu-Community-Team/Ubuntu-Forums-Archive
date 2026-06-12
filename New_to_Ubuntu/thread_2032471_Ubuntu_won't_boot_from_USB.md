---
title: "Ubuntu won't boot from USB"
date: 2012-07-24
forum: New to Ubuntu
---

### Post by itzdarockz on 2012-07-24
I sucessfully extracted ubuntu 12.04 to a formatted FAT32 usb. Than when I tried booting into ubuntu a screen that says the SYSLINUX copyright is shown and stuck like that. I cannot type or do anything in that screen except turn the power off (obviously). Also the usb I am using is seen as FDD instead of USB for some reason. Thanks!

---

### Post by NikTh on 2012-07-24
Hi , 
how did you extract the .iso image to usb ? did you use a program ? 

Thanks

---

### Post by lakona on 2012-07-24
Are you using a Ubuntu machine?

If so, try using the USB startup disk creator.

I believe it's in System-->Startup Disk Creator

---

### Post by itzdarockz on 2012-07-24
> **NikTh said:**
> Hi , 
how did you extract the .iso image to usb ? did you use a program ? 

Thanks

Through unetbootin. Sorry I should've specified.

---

### Post by itzdarockz on 2012-07-24
> **lakona said:**
> Are you using a Ubuntu machine?

If so, try using the USB startup disk creator.

I believe it's in System-->Startup Disk Creator

No, im on windows 7.

---

### Post by Bufeu on 2012-07-24
Have you made it bootable?

---

### Post by NikTh on 2012-07-24
Hi , 
try to boot again , but change usb port . Plug in your usb to another usb port. I assume you have more than one (ports). 

I guess that if you press Esc you will see a message similar to this "Cannot find installation media" 
or something like this. 

Another suggestion might be to burn a LiveCD (if you have CD drive) . 

Thanks

---

### Post by NikTh on 2012-07-24
> **Bufeu said:**
> Have you made it bootable?

Unetbootin makes the Usb bootable automatically . 

Except if OP stopped the process .

---

### Post by aimwin on 2012-07-24
Sometimes you will have issues with usb hardware.
or many other issues.

So if you want less trouble burn Ubuntu Live CD ISO instead.
Slower installation process but much more solid installation.

Ubuntu 12.04 has bugs on installation for certain environment.
I don't know if you use window 7 and unetbootin will produce some other errors or not.

Please try to use Ubuntu 10.04 LTS and see if the problem solved or not.

But best if you can create usb stick from UBUNTU machine
 with System-->Startup Disk Creator  as lakona said.

Good luck

---

### Post by oldfred on 2012-07-24
Floppy drives need a different type of image to boot. My system does not boot from any USB option with a flash drive, but from the choice of which hard drive to boot from. See if you can choose which hard drive to boot from, not USB device.

---

### Post by C.S.Cameron on 2012-07-24
Problem might be corrupted iso download, check MD5SUM.

---

