---
title: "Is It Necessary to Install Drivers From My Driver DVD?"
date: 2013-04-14
forum: New to Ubuntu
---

### Post by virus7 on 2013-04-14
Hello there, I am going to ask a very silly question here just like windows does Linux need to install its driver from my addition driver software DVD (which was provided by my Laptop Company) ? And If I really want to install a driver from there how can I do so?

Thank you very much.

---

### Post by r-senior on 2013-04-14
Device drivers are part of the core of Linux -- the Linux kernel. The kernel probes (looks at) your hardware and configures appropriate device drivers. When you receive kernel upgrades through normal updates, you get updated Linux drivers as they are released.

Most of the time this is what you want. You don't need to follow the Windows practice of keeping drivers up to date. It is done for you.

Very occasionally, you may have hardware that doesn't work properly with the default drivers. The manufacturer or a developer might provide Linux drivers but installing them can be an awkward process. Most of the time driver CDs just have Windows and Mac OS drivers and associated utilities so they are no use to you. I've not used a driver CD for years -- except to put my coffee cup on.

---

### Post by virus7 on 2013-04-14
thanks a lot.. surely its going to enhance my knowledge a lot. one quick question just arised in my mind.. so it means my linux must need to be connected with Internet connection? what if i dont have a connection is it going to work even on that situation too ??

---

### Post by Impavidus on 2013-04-14
Without internet connection you cannot automatically download and install updates. It is possible to download updates or new software on a different computer, take them home on a usb drive and install them from there (I've done so a few times when I was still using a dial-up connection), but it's rather awkward.

---

### Post by 3rdalbum on 2013-04-14
> **virus7 said:**
> thanks a lot.. surely its going to enhance my knowledge a lot. one quick question just arised in my mind.. so it means my linux must need to be connected with Internet connection? what if i dont have a connection is it going to work even on that situation too ??

You'll be a lot, lot happier using Linux with an internet connection. It's a royal pain to install software on Linux without the internet.

Most drivers come inside the kernel already and will just work without you having to do anything and without an internet connection.

---

### Post by grahammechanical on 2013-04-14
If we install Ubuntu and all the hardware works as it should then we have all the hardware drivers we need. It is when the hardware does not work as it should that we need either a driver from the manufacturer (wireless adapters & video adapters) or we wait until the Linux developers bring Linux up to date with the latest hardware. We have the Additional Drivers utility to make it easy to get proprietary wireless and video drivers but we need Internet access. Or we need to get those drivers on a CD or USB stick and set the CD as one of the locations (repositories/software sources) for getting software.

Regards.

---

### Post by virus7 on 2013-04-16
Thanks to everyon, I have learned a lot of things from you...

---

