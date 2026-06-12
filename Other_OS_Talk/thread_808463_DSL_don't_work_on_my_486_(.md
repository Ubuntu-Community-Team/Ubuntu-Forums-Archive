---
title: "DSL don't work on my 486 :("
date: 2008-05-26
forum: Other OS Talk
---

### Post by Bungo Pony on 2008-05-26
For the heck of it, I tried to get DSL running on an old 486 that was a curbside treasure :)

It's running Win95, 30 pin RAM (which I expanded to 20M!) and a proprietary CD-ROM drive. I tried installing DSL using a PC that will boot off a CD. After it installed, I swapped the HD in the 486 and it doesn't wanna boot it. All I get is a bunch of hex numbers on the screen and then it gives up.

Are there any tricks to getting DSL running on these old beasts, or is it just a waste of time?

---

### Post by Cap'n Skyler on 2008-05-26
> **Bungo Pony said:**
> For the heck of it, I tried to get DSL running on an old 486 that was a curbside treasure :)

It's running Win95, 30 pin RAM (which I expanded to 20M!) and a proprietary CD-ROM drive. I tried installing DSL using a PC that will boot off a CD. After it installed, I swapped the HD in the 486 and it doesn't wanna boot it. All I get is a bunch of hex numbers on the screen and then it gives up.

Are there any tricks to getting DSL running on these old beasts, or is it just a waste of time?

sometimes they dont want to boot for some unknown reason.i would try puppy linux.
it should boot up for ya.

---

### Post by quadomatic on 2008-05-26
> **Cap'n Skyler said:**
> sometimes they dont want to boot for some unknown reason.i would try puppy linux.
it should boot up for ya.

Puppy on a 486? Would that work?

I don't think swapping a HD that had DSL installed on it from another comp would work.

---

### Post by K.Mandla on 2008-05-26
You might have to peer into the DSL forums for some real information. I only can offer this page, which proves it's possible to do. No tangible instructions there though. :???:

[http://www.damnsmalllinux.org/486.html](http://www.damnsmalllinux.org/486.html)

---

### Post by Midwest-Linux on 2008-05-26
> **Bungo Pony said:**
> For the heck of it, I tried to get DSL running on an old 486 that was a curbside treasure :)

It's running Win95, 30 pin RAM (which I expanded to 20M!) and a proprietary CD-ROM drive. I tried installing DSL using a PC that will boot off a CD. After it installed, I swapped the HD in the 486 and it doesn't wanna boot it. All I get is a bunch of hex numbers on the screen and then it gives up.

Are there any tricks to getting DSL running on these old beasts, or is it just a waste of time?


 I am almost with the same problem, I have a HP 5700ct laptop with a interchangeable CD ROM and floppy drive. The ram is 48 MB, the speed is 166 Mhz and the HD is about 2 GB. 

 My problem is that the computer will either boot from the floppy or the hard drive or both, it won't recognize the CD ROM as a boot in fact there is no selection in the bios for the CD rom. Even if you install the CD Rom, the bios recognizes it as a floppy.... 

The computer contained windows 98 on it, I wanted to put DSL on it.

 I saw a post about installing DSL from a network set up

[http://www.damnsmalllinux.org/network-install.html](http://www.damnsmalllinux.org/network-install.html)

 However there are problems, a program called TOMSRTBT disk. And found at [http://www.toms.net/rb/](http://www.toms.net/rb/) will "install" into a floppy, then insert the floppy into the computer and boot it and install DSL through a network.

 Except for one ...little problem....the program to put on the floppy is 2.81 meg after unpacking. Floppy has a limit of 1.44 meg. There is another file that ends in gz, but that file is 1.74...again way over the 1.44 floppy limit. 

 So I threw in the towel and ended the project. the laptop works fine otherwise, it boots up and the screen and audio is fine. The ram is one of those obscure types of ram that costs like nearly $90 for 128 MB. So upgrading the ram is not a solution. I got the laptop for free, probably because nothing can be done to it without spending a lot of $$$. 

 Until I can find a readily installable Linux distro on floppy for it (I don't have much time to devote for it) the laptop goes back in the basement...

---

### Post by Cap'n Skyler on 2008-05-26
> **quadomatic said:**
> Puppy on a 486? Would that work?

I don't think swapping a HD that had DSL installed on it from another comp would work.

oops my bad....i dont know if that will indeed work.crap!

---

### Post by wolfen69 on 2008-05-27
> So I threw in the towel and ended the project. the laptop works fine otherwise, it boots up and the screen and audio is fine. The ram is one of those obscure types of ram that costs like nearly $90 for 128 MB. So upgrading the ram is not a solution. I got the laptop for free, probably because nothing can be done to it without spending a lot of $$$.

yeah, i think it is going to be tough for you to get anything worthwhile happening on an old machine like that. too much work for too little payback. then again, it could looked at as a side project. you could check out swap meets, computer fairs, or even use craigslist to find some cheap ram. you will be surprised at how many people are practically giving away perfectly good computers and parts. i advertised for "wanted: old or unused computers" and got a few usable pc's and parts out of the deal. one guy gave me 8 computers. 3 didnt work, but out of the 5 left, most were P4's. :)

anyway, good luck.

---

### Post by msrinath80 on 2008-05-27
I used to run Red Hat 6.0 on an i486Sx (33MHz clock speed) with a 200 MB drive and 16 MB EDO RAM. Worked nicely back then. See if you can find one of the old RedHat versions on some web page.

---

### Post by Bungo Pony on 2008-05-27
Man, I'd forgotten about trying to use a floppy to boot the CD-ROM. What I might have to do with this thing is temporarily put an IDE CD drive in it to do an install right on the PC. Maybe I'll try that tonight.

As a side note, I've installed DSL and swapped PCs before, and I haven't run into any problems. DSL usually does a hardware scan on boot, which is probably why it usually works. Might be different with this old 486 though.

The network install isn't a bad idea either. I just hope it would work with an ISA network card. This computer only has ISA slots :D

---

