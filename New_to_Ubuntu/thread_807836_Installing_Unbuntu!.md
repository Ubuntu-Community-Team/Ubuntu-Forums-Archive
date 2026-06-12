---
title: "Installing Unbuntu?!?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by jeffostrowick on 2008-05-26
I sure that this has been asked and answered everywhere, but here's my story and I'm at a loss.

Ok so i down load unbuntu 8.04 run the live demo on a P3 800Mhz 256RAM. Cool it works... kinda slow... then crashes.

Ok try it on a Toshiba Laptop 1.6ghz with 256 RAM... sorry installer won't run from Windows cos I'm using 32MB of RAM for the video card. Fine I try it from the boot... i get as far as Step 1: in the install - and the live demo gives me a Gnome error and freezes.

Ok try it on a FOXCONN motherboard 2.6 dual core Intel with a 1GB of ram. The windows installer freezes during the Checksum stage... and it won't even see it as a boot CD...

what am i doing wrong. is it the CD? another copy worked in the live demo.

I really want to show this OS to my kids... can anyone help me to get it to work.

-Yes, yes too much time on Apple where it just works ;)[PHP][/PHP]

---

### Post by shifty_powers on 2008-05-26
well first, boot up the livecd and select the "check cd for defects" option...

---

### Post by sayakb on 2008-05-26
Use the Text mode installer for 256MB RAM machines. Plus boot in the LiveCD and select Check CD for defects.

---

### Post by bumanie on 2008-05-26
Ubuntu 7.10 and 8.04 are meant to run on a minimum of 384 mb ram (although I have heard of a couple of people running it at 256). May be you should try 7.04 which was designed to run on a minimum of 256 mb ram.

---

### Post by sayakb on 2008-05-26
> **bumanie said:**
> Ubuntu 7.10 and 8.04 are meant to run on a minimum of 384 mb ram (although I have heard of a couple of people running it at 256). May be you should try 7.04 which was designed to run on a minimum of 256 mb ram.

A li'l correction there :)
7.10, or maybe even 8.04 can run on 256MB RAM, but it needs 384MB for the liveCD.
For that reason, you always have the text install that works fine on 256MB RAM.

---

### Post by jeffostrowick on 2008-05-26
Checked the disk it says its fine. i'm gonna try make another cd and the text option... um how do i do that i don't see an option (i thought of it but not sure how to do it... last time i played with linux was installing Red Hat four or five years ago).

---

### Post by sayakb on 2008-05-26
The text option isn't much different from the GUI install (to say it simply, you just don't have the mouse, and the rest is same) So there isn't much to worry about.

---

### Post by jeffostrowick on 2008-05-26
Ok burnt another CD get the same issues. no really where is the text option? on boot up it gives me a graphic safe mode that did nothing, OEM option - but would affect my Windows installation?

---

### Post by shifty_powers on 2008-05-26
afaik, he's referring to the alternate cd, which is designed to install without a gui...

---

### Post by shifty_powers on 2008-05-26
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and then check the box that says

> Check here if you need the alternate desktop CD. This CD does not include the Live CD, instead it uses a text-based installer.

to get the alternate cd

---

### Post by jeffostrowick on 2008-05-26
ah. ok so now what? I'm trying to figure this out - is it my computers or ubuntu? i've tried 3 different computer configurations and it doesn't work on any of them?!? that doesn't make sense. 
What if I tried install it on unpartioned, unformated drive?

---

### Post by jeffostrowick on 2008-05-26
ah. ok so now what? I'm trying to figure this out - is it my computers or ubuntu? i've tried 3 different computer configurations and it doesn't work on any of them?!? that doesn't make sense. 
What if I tried install it on unpartioned, unformated drive?

---

### Post by shifty_powers on 2008-05-26
could be a combination of both.

in the frist two cases, ubuntu will not like that little ram.

for them i would go with fluxbuntu, a lightweight derivative of ubunt anyways, ubuntu will struggle on them.

as for the last one not sure, but the alternate cd will def help ;)

---

### Post by jeffostrowick on 2008-05-26
> **shifty_powers said:**
> [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

and then check the box that says



to get the alternate cd
A case of "duh" will give it a try. Now what about my own PC why's it not allowing me to boot the live CD? 

- its a Foxconn Motherboard, that I had to set up as raid to get it to see the HDD and it installed windows fine. Why do you think its freezing during the "From within Windows" install and ignoring the boot CD (yes my machine is set to boot from CD in the boot priority)?

---

### Post by shifty_powers on 2008-05-26
could be the raid array i think. not got a lor of experience with ubuntu and raid, but have a feeling ti won't like it...

do you have raid 0 or 1 out of interest?

---

### Post by jeffostrowick on 2008-05-26
hahaha. like i know - i took me 2 days to figure out why it wasn't detecting the drive. If i remember i set it as RAID 0 - I actually don't have an array. just one disk, this bizarre motherboard won't detect a IDE drive without some kind of RAID software running. But it did detect the windows CD

---

