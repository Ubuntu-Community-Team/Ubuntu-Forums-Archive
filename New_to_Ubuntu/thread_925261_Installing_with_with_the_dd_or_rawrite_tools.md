---
title: "Installing with with the dd or rawrite tools"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by lizhood on 2008-09-20
I need to restore the Edubuntu installation on my PC2Go Classmate laptop. The problem is that all the data, including OS, on the machine is in a tiny partition and I can't use the rest of the 40G hard drive. (I think this happened because I screwed up an application install with the Synaptic tool.) I can't get on to the Internet with this machine now, even though I could when I first got it.

I downloaded the Edubuntu 8.04.1 (Hardy Heron) CMPC Remix Daily Build, using a Windows machine, onto a USB drive. However, I don't know how to create the dd or rawrite command on the USB so that I can move the image onto the Classmate. (The code is dd if=/tmp/hardy-classmate-20080311.img of=/dev/sdd)


Any ideas for me? Thanks.

---

### Post by linuxford on 2009-01-07
I think you need to be root to do this, maybe try:

sudo dd if=/tmp/hardy-classmate-20080311.img of=/dev/sdd

---

