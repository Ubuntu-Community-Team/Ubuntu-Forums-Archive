---
title: "No sound in 8.04"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by kickstart on 2008-11-18
Hi,

I've just installed 8.04 after some time away from linux, it seems to be working fairly well. One problem however is i have no sound.

If i type lspci | grep -i audio      into terminal i get the following:

> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

So by this i assume that Ubuntu is recognizing that my motherboard has an on board sound card. 

On the ASLA page i can't find anything saying that it supports my card, however, i have had success in running Ubunut (with sound) in 7.04, so i see no reason why i shouldn't be able to get support in 8.04.

Hope someone can help me out!

Cheers

---

### Post by Sealbhach on 2008-11-18
.

---

### Post by Sealbhach on 2008-11-18
I would suggest adding an option to /etc/modprobe.d/alsa-base 

See post here:

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)


.

---

