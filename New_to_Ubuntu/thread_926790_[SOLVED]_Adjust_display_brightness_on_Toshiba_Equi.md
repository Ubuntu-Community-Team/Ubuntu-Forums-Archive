---
title: "[SOLVED] Adjust display brightness on Toshiba Equim L40-10X on 8.04"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by eeeandrew on 2008-09-22
hi all, just installed 8.04 this morning. I'm having two small problems with it. 

Firstly, I can't change the display brightness using the hardware keys on my laptop. I tried to change the display brightness while on the BIOS screen which worked but as soon as ubuntu booted it automatically set the brightness to full again. Its seriously bright and I'm starting to get a headache. Any help would be appreciated.

Secondly, I would like to save the WEP key for my router into a keyring file and have it automatically enter this when I connect to my network. On ubuntu 7.04 it did this automatically but it doesn't seem to do it on 8.04. Any help would be appreciated.

On the whole, 8.04 is a fantastic OS and I'm glad I finally plucked up the courage to play with the partitions. Thanks to everyone who helped make this such a nice bit of kit,

Andrew

---

### Post by kjohansen on 2008-09-22
you can try a program called toshset (not in repositories).  it has controls for toshiba pcs.  The brightness controls in it do not work for me when using the restricted drivers for my video card, but some have had success.

Side note:
when I use the open source drivers my hardware keys work...

---

### Post by eeeandrew on 2008-09-22
hi again. I downloaded toshset and gave it a try unfortunately whenever I try to give commands I get the following reply.

> andrew@andrew-laptop:~$ sudo toshset
required kernel toshiba support not enabled.


I realise that in that particular command I did not use any switches but it is irrelavent as I get the same reply regardless which option I use. Does anyone know how to enable the kernel support?

Also I have sorted my problem with the keyrings, I simply had to select for the keyring to be saved.

Who dares wins,
Andrew

It appears that theres more of a problem with the screen than just the brightness controls. According to the "screens and graphics" programme in the others tab under apps, there is no driver installed for a toshiba screen and its using a generic one. Does anyone know how to get drivers and set up a 15.4" monitor?

---

