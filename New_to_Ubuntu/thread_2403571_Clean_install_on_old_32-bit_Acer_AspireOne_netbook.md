---
title: "Clean install on old 32-bit Acer AspireOne netbook – is it possible for a beginner?"
date: 2018-10-13
forum: New to Ubuntu
---

### Post by 23cricket on 2018-10-13
I have an old Acer Aspire One ZG5 netbook that formerly ran WinXP. I would like to use it when I travel for basic internet, email and simple word processing. It doesn’t have to do much more than that. Is it possible to clean install (via USB – no optical drive) some kind of Ubuntu (or other flavor of Linux?) that is kind and gentle for absolute rank beginners who have no aptitude for the command line? There is so much information out there - it’s overwhelming and mostly incomprehensible to me. I don’t know where to begin or if it is even possible! 

SPECS
Acer Aspire One ZG5 (MFG Date: 0903, AOA 150-1555)
CPU: Intel Atom N270 1.66 Ghz
RAM: 1GB DDR2
HDD: 120GB
Chipset: Intel 945 GM + CH7M
Graphics: Intel GMA 945GMS

Thank you for taking the time to read this. Kind thanks for any help or insight you may provide.

---

### Post by Holger_Gehrke on 2018-10-13
[LUbuntu]("https://lubuntu.net") 18.04 32bit is probably your best option with those specs. The only possible problem I see is web-browsing. Modern browsers and web sites are resource hogs of the worst kind, I'd upgrade to at least 2GB if at all possible and install an ad-blocker and NoScript browser add-ons to speed things up.

You'll need a tool to write the downloaded iso image file to a flash drive and make it bootable (rufus or unetbootin are two options for that, there are more) and you need to find out how to make your netbook boot from that. After booting be sure to use the "Try Lubuntu" option first to get an idea what the system is like and whether everything works and you can use it. In this mode it runs completely from compressed files on the USB-stick, so it's slower than an installed system.

Holger

---

### Post by kc1di on 2018-10-13
The limiting factor may be the ram - 1 GB is not much these days.  I would try one of the following [antix]("https://antixlinux.com/download/"), [lubuntu]("https://lubuntu.net/downloads/"), and [puppy.]("http://puppylinux.org/main/Download%20Latest%20Release.htm") good luck.

---

### Post by Autodave on 2018-10-13
Lubuntu will run fine on that machine. In fact, Xubuntu (a little fancier desktop) will also run on there.  I know that Xubuntu will run because I currently have it running on a very similar machine.

---

### Post by poorguy on 2018-10-13
I have installed ***Lubuntu 18.04*** on several old ***Acer Aspire*** laptops that originally came with ***Windows Vista 32bit ***although all of them had ***2.0 GB ***of memory installed.
[I][B]
Antix 17.2 (Helen Keller)[/B][/I] installs and runs on every computer I've used it on small footprint and hardly uses any resources.

[https://sourceforge.net/projects/antix-linux/files/Final/antiX-17.2/](https://sourceforge.net/projects/antix-linux/files/Final/antiX-17.2/)

---

### Post by 23cricket on 2018-10-13
Hey y'all,

Thank you SO much for your input!

At first look the Lunbuntu looks like it would be the easiest for a complete novice to install and use. Am I correct in that? I have never, ever used any version of Linux before that I know of.

The specs say that the maximum RAM that my little netbook will take is 1.5GB. I am wondering about the processor too. The Lunbuntu site says that *"the minimum specification for CPU is Pentium 4 or Pentium M or AMD K8. Older processors are too slow and the AMD K7 has problems with Flash video."* I am not sure how the Atom N270 1.66 Ghz processor compares to that.

AntiX and Puppy look super lightweight, though the jargon is currently a bit intimidating to me. In browsing their sites the learning curve just seems steeper and I only have a week to make a functional system before I have to travel. I'm going to try the Lubuntu first, and if that doesn't work I'll probably go to antiX.

I appreciate it folks!

David

---

### Post by him610 on 2018-10-13
I own an Acer Aspire One ZG5 AOA110-1955 that originally came with Atom N270 CPU, 512MB RAM and 8GB SSD pre-loaded with Linpus Linux (developed from Fedora). Replaced the Linpus Linux with some flavor of Ubuntu about nine or ten years ago; upgraded the Ram to 1.5GB - ran pretty good. I also installed Knoppix on it at one time which ran pretty good also. A couple of years ago after unintentionally zapping the original SSD, it sat dis-assembled in pieces after I took it apart for about a year. I wound up replacing the 8GB SSD with KingSpec 32GB SSD. The battery has been replaced a couple of times. It now has the latest version of Xubuntu (18.04.1) installed on it. It is my first choice as a travel machine.

Good luck, and have fun. It can be a great learning experience.

---

### Post by 23cricket on 2018-10-14
@him610, that is very encouraging!
@Holger_Gehrke, @kc1di, @Autodave, @poorguy - Thanks to you all!

I have successfully started Lubuntu 18.04 on the netbook from a LiveUSB and been able to connect to the internet. Yay! 

Wow! It sure is different than what I am used to, but even from the USB it's running snappier than XP ever did. Now to start figuring my way around and learning how to apply updates, etc... Started to do the full install and aborted. I'm having some trouble with my keyboard - some keys work and some don't, but that's for another thread...

Thanks again,

David

---

### Post by 23dornot23d on 2018-10-14
If your having troubles with the laptop keyboard ....... the cheapest option I know is to plug a cheap external keyboard into the usb port.

depends how many places you will be using the laptop computer in ....... but just have a usb keyboard at the main place of use.

---

### Post by 23cricket on 2018-10-15
@23dornot23d, Thanks for that. I hope to use the netbook for travel. It's old, small and light and it's not going to break my heart if something happens to it. I have it at a local shop now with a hardware guy who is pretty clever with keyboard repair and charges less than buying even a cheap external keyboard would cost here (I live overseas.)

If that doesn't work out though, I'll be looking for a mini or portable keyboard I can pack along on my travels.

Appreciate your help!

---

### Post by 23cricket on 2018-10-15
You all have been great! Thank you so much for your help.

I'm going to mark this thread SOLVED.

Cheers!

David

---

### Post by syats on 2019-04-28
Was it a keyboard hardware issue? I'm having the same problem with my ZG5: some keys aren't working on Debian 10.
Thanks for any info.

---

### Post by 23cricket on 2019-04-28
Hey @syats,

It was totally a hardware issue. The keyboard needed replaced, there was no repairing it.

I was amazed that a replacement part could even be found, but the hardware guy I went to is an absolute wizard, and I live in a part of the world where things don't get thrown out too quickly, so that was working in my favor too.

Good luck to you!

~D

---

### Post by him610 on 2019-04-28
> The keyboard needed replaced, there was no repairing it.
FWIW, I have a spare ZG5 keyboard.

---

