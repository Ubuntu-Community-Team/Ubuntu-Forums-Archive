---
title: "Installing XUbuntu 12.04 help"
date: 2013-12-05
forum: New to Ubuntu
---

### Post by bfbctom on 2013-12-05
Installing XUbuntu 12.04 on my machine from my USB stick.


Boots up from it fine > Install > Installation type, this is where I am stuck.

Nothing appears in the white box labeled, Device, Type, Mount Point etc. When I click +, or any other button, it comes up with "Sorry, Ubuntu 12.10 has experienced an internal error."


What do I do from here? Do I need a second USB stick to use for the install? I am not sure what the /dev/sda means too.


Can someone please point me in the right direction?


Kind regards,
Tom

---

### Post by ajgreeny on 2013-12-05
If you are trying to install to the USB which already has the live system/installer on it, you will not be successful.

Normally you would install from the USB onto the hard disk of your machine (which may have windows on it already) which is the /dev/sda you mention, but please give us more details of what exactly you've done and what hardware you are attempting to use.

---

### Post by bfbctom on 2013-12-06
> **ajgreeny said:**
> If you are trying to install to the USB which already has the live system/installer on it, you will not be successful.

Normally you would install from the USB onto the hard disk of your machine (which may have windows on it already) which is the /dev/sda you mention, but please give us more details of what exactly you've done and what hardware you are attempting to use.

Hi,

Currently there is no hard drive, hence why this isn't working probably. I won't be using a HD for this install but a USB stick. So I presume I need a second blank USB stick to install the software from the bootable stick to the blank one right? 

I have a MSI Z77A-G65 mobo with a Intel G1610 processor, 4GB RAM.

So if I plug in a blank USB stick, I can use this instead of the hard drive? Does it need to be formatted at all?

Thanks for the help.

---

### Post by codenine75a on 2013-12-06
I see what you are doing.  You are trying to install a direct copy of Ubuntu on a USB drive instead of a live install.  I think you can do it with two usb sticks.  I used to install on to external usb hard drives.  Boot up to your live installation and plug in your "slater" USB stick and install on it.

---

### Post by fantab on 2013-12-06
In Linux the HDD or USB storage are called /dev/sdx.
Where 'x' means the HDD number. Your first storage device will be called /dev/sda. You second device will be /dev/sdb and the third /dev/sdc and so on.

Yes you can install from USB to another USB. Just make sure that the USB you will install to is /dev/sda and the device you are installing from is /dev/sdb... This depends on which USB you plugin first... or in which port.

How big is the USB storage you want to install to?

---

