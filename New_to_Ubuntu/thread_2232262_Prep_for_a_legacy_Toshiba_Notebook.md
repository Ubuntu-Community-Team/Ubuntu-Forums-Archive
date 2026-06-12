---
title: "Prep for a legacy Toshiba Notebook"
date: 2014-06-30
forum: New to Ubuntu
---

### Post by Phil_Pene on 2014-06-30
Want to put Ubuntu on an old Toshiba laptop that has precisely  2GB memory, Microsoft Vista but does not recognize a USB drive on boot
Additionally, I would want the USB and the CD for a windows machine created on an Apple 64bit desktop... can this be done?  Can a yummi USB be created on this Apple?
Is there anything that would allow me to modify the BIOS to recognize the USB bootup?

Much appreciation for any guidance

---

### Post by yancek on 2014-06-30
Older computers were not capable of booting from a usb.  You might post additional information on your Toshiba laptop, the type or model and someone might be familiar with it.  If you want to create a bootable usb of a Linux system on an Apple computer, you can use unetbootin.  Just google it and you will notice on their home page a version for Apple.

---

### Post by Vladlenin5000 on 2014-06-30
Is your Toshiba from circa 2007? If so it most certainly it can boot from USB. Is such option offered and it doesn't boot from the drive or not available at all?
 You may want to take a look at this old thread  - [http://www.techspot.com/community/topics/cannot-boot-from-dvd-on-toshiba-satellite-laptop.88460/](http://www.techspot.com/community/topics/cannot-boot-from-dvd-on-toshiba-satellite-laptop.88460/) -. Unrelated but the suggestions about how to change boot order might help you.

---

### Post by oldfred on 2014-06-30
My Toshiba laptop is from the end of 2006. It has 1.5GB of RAM and says Vista Ready but was purchased just before Vista was released. It boots from USB flash drive.
TOSHIBA Satellite A105 with Intel(R) Core(TM)2 CPU         T5500  @ 1.66GHz
I run Ubuntu 64 bit 12.04 on it, but have to install flashback/fallback or gnome-panel as it just does not have enough to run Unity. And with 1.5GB of RAM cannot open more than one large app and a couple of smaller ones before it goes to cache and gets real slow.

You do have to make sure flash drive is correctly configured as a boot able device as BIOS skips it if not bootable.

---

### Post by slooksterpsv on 2014-07-01
I'm not sure about a yummi, but there are a few options. You are able to create a bootable USB on Mac, also you can create a CD on Mac as well. As long as it's ISO, it should burn as an ISO. You can do that in disk utility. I'd look into unetbootin for USB booting.

If all else fails there is another way using dd, I won't go into it as sometimes you have to play with it, use the tools as mentioned above and let us know if it works. I believe most computers from 2001+ were capable of booting from USB.

---

