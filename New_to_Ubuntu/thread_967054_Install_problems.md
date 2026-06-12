---
title: "Install problems"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by cmotdibbler13 on 2008-11-01
Firstly my computer specs. :

Asus X70S Series.
CPU: Duo T5550
Optical Drive: 2X Blu-Ray
HD: 250GB
Memory: 3GB
Graphics card: ATI Mobility Radeon HD 2400, RAM:256MB

Oh and it's a laptop (just in case that makes a difference)

Good evening all, 

I downloaded the newest version of Ubuntu from the main site and burnt it to a DVD.

I rebooted my computer and set the boot sequence to CD first, HD second.

The ubuntu screen appeared and I chose the second option, Install Ubuntu.

It went to the next screen which looked like a pong paddle on its side, moving left to right, followed by a cursor in the top left of the screen.

Then (and I apologise for this ) it looks like DOS has come up and I am left with no nice graphic screen, just a flashing cursor and no idea how to get to the install part.

I see from some other posts that ATI cards are causing some problems, but I couldn't find anything about the install not continuing.

Any help would be appreciated, thanks in advance.

Jon

---

### Post by laney_1 on 2008-11-01
are you using a livecd? if not you should as this enables ubuntu to launch from the cd then install (this helps to see if ubuntu will run on your machine before you install). 

it is usally the first option to boot in to the live cd.

when the desktop appears there should be an installer icon this is the nice graphical installer.

laney_1

---

### Post by cmotdibbler13 on 2008-11-01
Thanks I tried that, unfortunately all it did for me was install the dual boot option but I still keep getting the flashing cursor and no graphic front end, any other ideas?

---

### Post by laney_1 on 2008-11-01
is there any writing or is it just a cursor?

laney_1

---

### Post by sirius11 on 2008-11-02
very simple,  if it wont boot or install at the first try  and there is no error on the cd/dvd,  forget about ubuntu,  you will be loosing your time trying to make it work...  specially with a ATI card.  Ubuntu work or not,  plug and PRAY..  and forget support, nobody can know whats wrong... 

so  like me  you have downloaded ubuntu 8.10,  burned it,  and lost your time trying to install it...  you are not alone believe me..

I have a simple AMD 5400+ system with a 8800gts  video card.

---

### Post by DGortze380 on 2008-11-02
> **sirius11 said:**
> very simple,  if it wont boot or install at the first try  and there is no error on the cd/dvd,  forget about ubuntu

This is definitely not true. I would suggest you try the alternate cd. The live cd runs on a limited number of drivers due to space constraints. 

Also, google the name of your graphics cards + ubuntu (or + linux). If there are known driver issues, then the previous post is (somewhat correct), you may have to wait for a driver update.

---

### Post by cmotdibbler13 on 2008-11-03
Thanks, but can you tell me how the alternative install differs from the one I have downloaded.

Jon

laney,

the cursor follows writing that says *ubuntu@ubuntu:*

its like it has installed as a non graphic install, I followed the route I took for my last laptop and distro (7.10) but it just doesnt want to install the same way.

---

### Post by igknighted on 2008-11-03
The alternate install does not use a true graphical system, it uses an 'ncurses gui'.  Basically it uses characters in the terminal to create graphics.

Before you go that route, however, hit the (i think f4 key... look along the bottom for which key is "modes" at boot) and select the safe graphics option.  It might give you crap performance and resolution, but after you are installed ubuntu will install the latest official driver from ati (if you are online) and that should fix things.

---

