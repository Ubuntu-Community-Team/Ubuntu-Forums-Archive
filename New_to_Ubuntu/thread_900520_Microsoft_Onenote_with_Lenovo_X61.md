---
title: "Microsoft Onenote with Lenovo X61"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by silenthunter747 on 2008-08-25
So I've been using Ubuntu on my laptop because it runs much quicker than Vista, and it's pretty useful in my System Programming class. However, I still have to boot into Vista to use Microsoft Office (Onenote specifically).

What's the best solution to get Onenote working with all the tablet features on Ubuntu? I've tried running Vista in a VMware server but that was no good. I have an old XP license; would that run Onenote well in a virtual environment? I've tried using Wine with little success.

Lenovo X61
Processor: Core 2 Duo @ 1.6GHz
Ram: 1GB

---

### Post by cookdn on 2008-08-27
OneNote would work in a virtualised environment (VirtualBox, VMWare etc) on top of Windows however you are not going to get the hardware features of your X61 tablet working with OneNote that way; I guess that is what you are really after.

This is probably one of those situations where you have no choice but to dual boot Ubuntu with Windows; booting into Windows to use OneNote and then into Ubuntu for everything else. Accessing files in your windows partition from Ubuntu won't be a problem and you can do the reverse in Windows using something like Ext2 IFS ([http://www.fs-driver.org/](http://www.fs-driver.org/)).

Hope this helps to answer your question.
David

---

### Post by silenthunter747 on 2008-08-27
Well the pen is already recognized and I can use it on the screen, but would those features not tranfer into the virtual environment?

Thanks for that link; I didn't know that windows could read Ubuntu paritions.

---

