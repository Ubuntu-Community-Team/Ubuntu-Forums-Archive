---
title: "Installing an older version through terminal"
date: 2017-03-04
forum: New to Ubuntu
---

### Post by shawnfail on 2017-03-04
Here's the full story. I was running out of space for my 3DS and decided to buy a new microSD card. I bought a 64GB figuring I would never need to upgrade from that. After I swap it in and it's not working I find out that the 3DS only supports up to 32GB. My friend saw there was a work around by using partitions on the card so I started looking into it. My chromebook was the only thing I have with any SD card slots so I looked into working with that. After going through and installing ubuntu on it and download GPARTED, I can't partition the SD card because GPARTED crashes. From what I've seen its an issue with the version of Ubuntu and the version of GPARTED, and using an older version of Ubuntu fixes it. So now my question is: How, purely through my chromebook, can I install an older version of Ubuntu in hopes that this will fix my issue and allow me to partition my SD card for my 3DS?

---

### Post by mörgæs on 2017-03-04
Hi, welcome to the fora.

Gparted does nothing in itself. It's only an interface to the **parted** command which can be invoked from the command line. 

In stead of focusing on old releases I suggest that you take a look at **parted**.

---

### Post by HermanAB on 2017-03-04
..or go olde skool and use fdisk and mkfs.

---

### Post by malangaman on 2017-03-04
check this out:

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

### Post by shawnfail on 2017-03-04
Thanks. I'll be looking into this when I have some time after work today!

---

