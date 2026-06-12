---
title: "Ubuntu, SSD, cache and sleep. Can I use a second hdd to write the image to?"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by i0ls on 2014-02-24
I have set up a nice Ubuntu box to run as our family's daily desktop.
I know for a fact that my wife and kids will leave this thing on forever. Which usually isn't a big deal, but after what I have read and a guide that followed to optimize Ubuntu and my ssd. Sleep and the ssd are not a good thing for its life and health.
So, I will admit that I don't know much about this, but from what I understand Ubuntu writes an image of the system to the hard drive before going to sleep and that's what kills the ssd. Is there some way to use a second or third hard drive for writing that image and possibly cache to as well?
thanks in advance for any help!

---

### Post by sandyd on 2014-02-24
> **i0ls said:**
> I have set up a nice Ubuntu box to run as our family's daily desktop.
I know for a fact that my wife and kids will leave this thing on forever. Which usually isn't a big deal, but after what I have read and a guide that followed to optimize Ubuntu and my ssd. Sleep and the ssd are not a good thing for its life and health.
So, I will admit that I don't know much about this, but from what I understand Ubuntu writes an image of the system to the hard drive before going to sleep and that's what kills the ssd. Is there some way to use a second or third hard drive for writing that image and possibly cache to as well?
thanks in advance for any help!

Sleep - no it doesnt write anything
Hibernate - Yes it does

Basically, it writes the contents of the RAM ( in Hibernation mode) into the swap partition.
So basically - you just create a swap partition on a separate disk and mount that as a swap partition

Let me know if you need any more help :)

---

### Post by Bucky Ball on 2014-02-24
> **sandyd said:**
> 
Basically, it writes the contents of the RAM ( in Hibernation mode) into the swap partition.
So basically - you just create a swap partition on a separate disk and mount that as a swap partition



^^^
This. You can actually move all sorts to a HDD; the Firefox cache, swap, /var, /tmp ... and more, but I figure if you go too far, what is the point of having an SSD for speed? ;)

I personally have the Firefox cache and /swap on a separate old IDE drive (you just change the location of the /swap partition in /etc/fstab). Seems to be all fine. ;)

---

### Post by sandyd on 2014-02-24
> **Bucky Ball said:**
> ^^^
This. You can actually move all sorts to a HDD; the Firefox cache, swap, /var, /tmp ... and more, but I figure if you go too far, what is the point of having an SSD for speed? ;)

I personally have the Firefox cache and /swap on a separate old IDE drive (you just change the location of the /swap partition in /etc/fstab). Seems to be all fine. ;)

[https://wiki.archlinux.org/index.php/profile-sync-daemon](https://wiki.archlinux.org/index.php/profile-sync-daemon)

Much faster setup for firefox cache :)

---

### Post by i0ls on 2014-02-24
thanks for your replies! il have to look into an appropriate size to make /swap and do it up. Thanks so much for the help!

---

### Post by sandyd on 2014-02-24
> **i0ls said:**
> thanks for your replies! il have to look into an appropriate size to make /swap and do it up. Thanks so much for the help!

If you want to hibernate - your swap should be larger than the amount of ram you have - generally, I set it to the size of the ram or 2x incase something is using the swap

---

### Post by i0ls on 2014-02-25
> **sandyd said:**
> If you want to hibernate - your swap should be larger than the amount of ram you have - generally, I set it to the size of the ram or 2x incase something is using the swap

I made a 8.4 gb swap partition on my 2tb secondary hard drive just to test it out. Set swap for /dev/sda2 which is the swap partition and checked with sudo mount -a. No errors. Rebooted and the system absolutely crawled, and for some reason I had no mouse idk.. Restored my trusty backup fstab and all is well again. What the heck did I do?

How is anyone else with an SSD dealing with power management for a box that's left on 24/7? 
The read/write to the 2tb is way faster than the way the system ran (felt like ide, like before eide even). What gives?

---

