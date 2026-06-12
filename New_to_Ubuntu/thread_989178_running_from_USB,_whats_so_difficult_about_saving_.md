---
title: "running from USB, whats so difficult about saving configuration?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by unxzst on 2008-11-21
I'm trying to get used to Ubuntu, so I created a USB startup disk on an 8Gb flash, and also a boot CD via a tutorial i found on pendrivelinux.

My question, what's so different about running from flash? Why can't a flash drive be considered as a regular hard drive?
Another way to look at it, is like having an external hard drive. 

Im asking this because I often get error 17 when trying to install packages. I'm trying to develop with Eclipse ( I may be switching to Netbeans if this latest attempt fails), and I am having problems running it. I've installed the latest sun java, and going to give it another try.

---

### Post by ztrange on 2008-11-21
I can only say that I have tested making a pendrivelinux and succeeded... The difference, I think, is that it, as the live cd, has a compressed version of linux. By compressed I mand that if yopu browse the pendrive conents in a regular pc (not booting with it), you will not see the filesystem just as you see it when usb booting.

You also have to understand the difference between a persistant live-usb and a common live-usb installation. The persistant is the one in which you can save your documents and install software.

In the other hand, I dont know what error 17 says and cannot help you with that, maybe you can provide more details.

---

### Post by Keen101 on 2008-11-21
an 8gb drive should be fine for a regular ubuntu install.

why did you use pendrivelinux?  A normal ubuntu install should have worked fine.

---

### Post by bodhi.zazen on 2008-11-21
> **unxzst said:**
> I'm trying to get used to Ubuntu, so I created a USB startup disk on an 8Gb flash, and also a boot CD via a tutorial i found on pendrivelinux.

My question, what's so different about running from flash? Why can't a flash drive be considered as a regular hard drive?
Another way to look at it, is like having an external hard drive. 

Im asking this because I often get error 17 when trying to install packages. I'm trying to develop with Eclipse ( I may be switching to Netbeans if this latest attempt fails), and I am having problems running it. I've installed the latest sun java, and going to give it another try.

You can install Ubuntu to a flash drive and then the issue is getting the BIOS to boot from it.

Or you can boot the iso image, which is different ...

Ubuntu is not designed to be used this way, although some distros are (Puppy, Slax, Wolvix, etc).

---

