---
title: "Linux kernel 3.0 rc5 is here"
date: 2011-07-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Harry33 on 2011-07-01
A new rc5 version of 3.0 kernel is building in Launchpad.
Download from here, soon:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-3.4](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-3.4)

---

### Post by sparker256 on 2011-07-01
> **Harry33 said:**
> A new rc5 version of 3.0 kernel is building in Launchpad.
Download from here, soon:
[https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-3.4](https://launchpad.net/ubuntu/oneiric/+source/linux/3.0-3.4)
Been running the 64 bit version from  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc5-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc5-oneiric/) for a few days with no issues that I have found. It fixed the guest cifs mounting issue that I was having.

Bill

---

### Post by VinDSL on 2011-07-01
> **sparker256 said:**
> Been running the 64 bit version from  [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc5-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0-rc5-oneiric/) for a few days with no issues that I have found.[...]
Same here.

I've been running the 32-bit version, since 28-Jun, and it's been working fine too.  ;)

---

### Post by Harry33 on 2011-07-01
The Ubuntu-patched version from Oneiric repos works well too.

---

### Post by dino99 on 2011-07-04
hm, its summer time, packages not into repo yet

Edit: have reached the repo now :)

---

### Post by jfernyhough on 2011-07-04
I downloaded from LP and stuck it on both 311c and 1749. Works fine on my 1749 but as normal for an Ubuntu build it won't detect my touchpad correctly on my 311c so I have no edge scrolling. The mainline builds seem to work fine, though I've also lost two-button-as-middle click.

Annoying, but then I mostly use a mouse anyway. :D

---

### Post by VinDSL on 2011-07-05
I awoke in a whimsical mood today - threw caution to the wind - and installed the 4-Jul 3.0.0-999 mainline kernel.

I also performed a system update, which was quite large.

That was 9 hours ago...

RAM usage is about the same, but there's been a tremendous drop in CPU stress - which was been running at almost 100%, most of the time.

Bottom line:  This machine is running GREAT!  Can't wait to start testing A2! ;)


Check out the CPU stats.  Chromium, Banshee, and Empathy running...

[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-4-jul-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-4-jul-2011.png")[/INDENT]

---

### Post by lucazade on 2011-07-05
Tried new 3.0.3 on a couple of machines and seems to work well.
No major issues at the moment.

@VinDSL
happy whimsical day, I'm still figuring out if i'm already awake.

---

### Post by Dipper on 2011-07-05
Still no backlight with Acer Aspire 5734Z with new kernel update. Very discouraging.

---

### Post by scradock on 2011-07-05
> **Dipper said:**
> Still no backlight with Acer Aspire 5734Z with new kernel update. Very discouraging.
WARNING: The Ubuntu USB startup disk utility reformats ALL connected drives, even the ones not selected!
Do you have any further details of the assertion in your WARNING?

It sounds a trifle alarming, and not something I would expect the good folks at Canonical would have missed........

---

### Post by dino99 on 2011-07-05
rc6 is out

with fixes i'm waiting:

     USB: don't let the hub driver prevent system sleep
      USB: don't let errors prevent system sleep

hope that fix the shutdown issue this time :)

---

