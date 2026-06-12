---
title: "ATI Accelerated Graphics Driver"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by beetlejuice_masterson on 2008-09-15
Hey All--
I'm running a brand new install of Ubuntu--love it.  Got internet connection and everything right out of the box.  One problem occurred when I tried to set some of the fancy desktop UI enhancements.  I went into
System > Administration > Hardware
And saw that "Ati Accelerated Graphics Driver" was not enabled, status = "not in use".
To remedy I checked the enabled box and it tried to download but I got a 404 file not found!  What's the deal?  Any ideas?

Thanks!!

---

### Post by KazPed on 2008-09-15
i wouldnt advise installing that driver! When i did it, it just made a black screen and i couldnt see anything. even after rebooting etc. then that caused more problems trying to remove it! on regards to your problem i dnt really know, mine downloaded straight away.

p.s im using ATI Radeon 2600Pro

---

### Post by fatality_uk on 2008-09-15
What card are you using? Do you have the multiverse enabled in the software sources?

---

### Post by PocketDog on 2008-09-15
I had the same issue with my ATI. From Terminal type sudo apt-get update. This'll update the local repository locations, then you'll be able to download the driver when prompted

---

### Post by markbuntu on 2008-09-15
It really depends on what card you have wethwer or not that driver will work. It will not work for the 4xxx series cards and the 2600 series agp cards and a few other newer cards, it is too old. For those you need to use these directions, Method 2:


[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The release notes for the latest 8.8 driver are here:


[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_88_linux.html)

---

### Post by beetlejuice_masterson on 2008-09-15
Hey guys, things are working great...I guess I just needed to download new list of updates.  Got some cool fx on my desktop now.  Much appreciated!

---

### Post by N031 on 2008-09-30
> **KazPed said:**
> i wouldnt advise installing that driver! When i did it, it just made a black screen and i couldnt see anything. even after rebooting etc. then that caused more problems trying to remove it! on regards to your problem i dnt really know, mine downloaded straight away.

p.s im using ATI Radeon 2600Pro

I have the same issue as u did help me plz Im new to Ubuntu I installed the driver it said it found for the card and now when i start up it stays black the log in screen for a long time and I dont know how to revert back or remove the driver to its original state it was plz tell me what u did I have a HD 2600 pro like u do!

---

