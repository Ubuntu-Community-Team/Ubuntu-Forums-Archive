---
title: "Any way of installing drivers for non-Linux friendly adapter, salvage situation?"
date: 2019-08-20
forum: New to Ubuntu
---

### Post by skeezyleff on 2019-08-20
So recently I made a somewhat impulsive decision to install Xubuntu on my PC and wipe off Windows as I really wanted to immerse myself and learn, without considering how my hardware wasn't too Linux-friendly. Writing this from my laptop, my PC has an i5-6400 and a GTX 960. The main offender here is my wifi adapter that can be found [here]("https://www.aukey.com/products/ac1200-dual-band-wi-fi-usb-adapter-wf-r6"). 

After installing, I got some message talking about some downloads, things for my language needed to be installed and that's where I noticed that there was no wifi connection, none of the networks popped up. Is there anything that I can do to fix this problem? It doesn't look like this adapter can work on Linux, as my google searches haven't been successful. I found the drivers on the website, but they are .exe files. I have some money to dispose, so would it be possible to buy a new adapter along with an ethernet cable to set things up? That seems like the only plan, the only thing I can do. I'm hoping that it works because I didn't wipe all of my files for nothing, although it isn't a loss since I backed up everything, just don't want to set up Windows again but I guess I'll have to deal with it if it does happen.

Thanks!

---

### Post by Autodave on 2019-08-20
I can't help with what you have, but a quick search on Amazon for "USB wifi Linux" brought up quite a few hits around $15 to $30 US.

---

### Post by crip720 on 2019-08-20
From found two links that might help with drivers.  [https://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-18-04-driver-for-usb-wifi-ac-12000-dual-band-4175628850/](https://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-18-04-driver-for-usb-wifi-ac-12000-dual-band-4175628850/) and [https://ubuntuforums.org/showthread.php?t=2394372](https://ubuntuforums.org/showthread.php?t=2394372).

---

### Post by SeijiSensei on 2019-08-20
This has worked reliably for me for quite some time.

[https://www.newegg.com/edimax-ew-7811un-1-x-usb-1-0-2-0-type-a/p/N82E16833315091](https://www.newegg.com/edimax-ew-7811un-1-x-usb-1-0-2-0-type-a/p/N82E16833315091)

If you want to add Bluetooth to the machine you can use 

[https://www.newegg.com/edimax-ew-7611ulb-usb-1-0-2-0-type-a-port/p/N82E16833315160](https://www.newegg.com/edimax-ew-7611ulb-usb-1-0-2-0-type-a-port/p/N82E16833315160)

Only wireless N speeds though.  If you want an 802.11ac adapter, they are a bit more tricky to find the right drivers.   For this device, see 
[https://askubuntu.com/questions/802205/how-to-install-tp-link-archer-t4u-driver](https://askubuntu.com/questions/802205/how-to-install-tp-link-archer-t4u-driver)

You'll need to install the build-essential and dkms packages first:

```
sudo apt install build-essential dkms
```

And here's an ethernet cable: [https://www.newegg.com/black-startech-6-ft-consumer-electronics/p/N82E16812400937](https://www.newegg.com/black-startech-6-ft-consumer-electronics/p/N82E16812400937)

---

### Post by skeezyleff on 2019-08-20
> **SeijiSensei said:**
> This has worked reliably for me for quite some time.

[https://www.newegg.com/edimax-ew-7811un-1-x-usb-1-0-2-0-type-a/p/N82E16833315091](https://www.newegg.com/edimax-ew-7811un-1-x-usb-1-0-2-0-type-a/p/N82E16833315091)

If you want to add Bluetooth to the machine you can use 

[https://www.newegg.com/edimax-ew-7611ulb-usb-1-0-2-0-type-a-port/p/N82E16833315160](https://www.newegg.com/edimax-ew-7611ulb-usb-1-0-2-0-type-a-port/p/N82E16833315160)

Only wireless N speeds though. If you want an 802.11ac adapter, they are a bit more tricky to find the right drivers. For this device, see 
[https://askubuntu.com/questions/802205/how-to-install-tp-link-archer-t4u-driver](https://askubuntu.com/questions/802205/how-to-install-tp-link-archer-t4u-driver)

You'll need to install the build-essential and dkms packages first:

```
sudo apt install build-essential dkms
```

And here's an ethernet cable: [https://www.newegg.com/black-startech-6-ft-consumer-electronics/p/N82E16812400937](https://www.newegg.com/black-startech-6-ft-consumer-electronics/p/N82E16812400937)

Thanks for all of the links! I will check them out.

---

