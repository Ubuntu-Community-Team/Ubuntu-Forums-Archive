---
title: "ubuntu 10.04 LTS on toshiba z835/830"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by idom on 2012-05-12
Hi 

I just bought toshiba z835 ultrabook and I want to move to ubuntu. 

However when I boot from USB it give following message. 

Unale to find a medidum containg live file system. I booted with the same flash drive on my desktop ( core2 quad ) it is booting properly.

Is there anyway I can check if z835 has some problem with 10.04 LTS.? 
couple of places I found that they have installed 11.10 over z830.

please help. as I would like to stick to LTS if possible and 12.04 seems to still have lots of problem. I don't want to use windows at all since I have been using ubuntu since last 4-5 years.


thanks
idom

---

### Post by jtarin on 2012-05-12
Make sure you have enabled the USB device as first bootable in the bios and try to use your boot selection menu to boot with....normally F11 key
No problems with 12.04 on my box.

---

### Post by j2bv16 on 2012-05-12
> **jtarin said:**
> Make sure you have enabled the USB device as first bootable in the bios and try to use your boot selection menu to boot with....normally F11 key
No problems with 12.04 on my box.

Yeah, 12.04 is a good choise, you should move to the last LTS. Give it a chance

---

### Post by idom on 2012-05-12
> **j2bv16 said:**
> Yeah, 12.04 is a good choise, you should move to the last LTS. Give it a chance

Yeah I have done USB as the first boot up choice it shows ubuntu symbol also. 12.04 many people are complaining about several stuff.

idom

---

### Post by jtarin on 2012-05-12
Possibly your USB is setup incorrectly.What instructions did you follow to place Ubuntu on it?

---

### Post by idom on 2012-05-13
> **jtarin said:**
> Make sure you have enabled the USB device as first bootable in the bios and try to use your boot selection menu to boot with....normally F11 key
No problems with 12.04 on my box.


Hey installed 12.04 LTS eventually as I thought it is always better to move to latest version.

having problem with virtual box trying to install win7 in virtual box inside.

idom

---

### Post by pissedoffdude on 2012-05-13
If there is a usb legacy option in the bios, be sure it is enabled.  Have you tried a different usb port?  The current usb port may be underpowered.  If you're still not able to get it to go and are sure you're booting from usb, you may want to remake it.  How did you create the bootable usb?  You can remake it with unetbootin if you haven't already.

---

### Post by 3rdalbum on 2012-05-13
My first thought is that Ultrabooks use USB 3, and Ubuntu 10.04 predates ultrabooks. This is why the old Linux kernel in Ubuntu 10.04 cannot find the USB stick it's been loaded from; it has no driver for the comparatively new USB chipset. It probably has few or no drivers for anything in your Ultrabook.

That's why 12.04 works on the same hardware.

Glad you got that issue fixed.

---

### Post by idom on 2012-05-13
> **pissedoffdude said:**
> If there is a usb legacy option in the bios, be sure it is enabled.  Have you tried a different usb port?  The current usb port may be underpowered.  If you're still not able to get it to go and are sure you're booting from usb, you may want to remake it.  How did you create the bootable usb?  You can remake it with unetbootin if you haven't already.

Sorry for not giving the full info. 
Sequence of events
1. created a recovery media from toshiba
2. installed 12.04 as a fresh install
3. installed virtualbox 4.1 on the machine
4. now trying to use recovery media 16GB usb flash drive to use as my windows 7 booting however virtual box is not detecting usb it is not giving me option to use usb as a booting device. it just hows floppy/CD/HDD

---

### Post by idom on 2012-05-13
> **idom said:**
> Sorry for not giving the full info. 
Sequence of events
1. created a recovery media from toshiba
2. installed 12.04 as a fresh install
3. installed virtualbox 4.1 on the machine
4. now trying to use recovery media 16GB usb flash drive to use as my windows 7 booting however virtual box is not detecting usb it is not giving me option to use usb as a booting device. it just hows floppy/CD/HDD

as it is no longer 10.04 problem I have moved it to a new thread. this can be ignored as title and problem are no longer related. 

Thank you all for your help. 

Regards 
idom

---

