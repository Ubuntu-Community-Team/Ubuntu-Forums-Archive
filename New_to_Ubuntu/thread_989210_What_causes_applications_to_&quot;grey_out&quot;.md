---
title: "What causes applications to &quot;grey out&quot;?"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by dmber on 2008-11-21
I'm running eeebuntu standard on my Eee PC 900.  It has a 900 mhz processor and 1 gig of RAM.  I have a 2-gig stick coming in the mail, but now I'm thinking that's not going to help.  The problem is that Firefox (mainly, along with some other apps) "greys out" really frequently, especially when I'm looking through my feeds on Google Reader.  I just have to wait (10-20 seconds sometimes) for it to "un-grey" and I can continue to use it, but it's just a super pain.  

So, what is causing that?  Will the RAM upgrade help?  If not, can I upgrade the processor?

Thanks.

---

### Post by damis648 on 2008-11-21
It is caused when applications stop responding. This could happen for a number of reasons.

---

### Post by oilchangeguy on 2008-11-21
> **dmber said:**
> I'm running eeebuntu standard on my Eee PC 900.  It has a 900 mhz processor and 1 gig of RAM.  I have a 2-gig stick coming in the mail, but now I'm thinking that's not going to help.  The problem is that Firefox (mainly, along with some other apps) "greys out" really frequently, especially when I'm looking through my feeds on Google Reader.  I just have to wait (10-20 seconds sometimes) for it to "un-grey" and I can continue to use it, but it's just a super pain.  

So, what is causing that?  Will the RAM upgrade help?  If not, can I upgrade the processor?

Thanks.

it's not a hardware issue. also i don't think your 900mhz cpu computer will support 2gb of ram. did you check, before you ordered?

---

### Post by Tony Flury on 2008-11-21
I have observed that the grey screen happens mostly when the system is swapping hard - so the memory upgrade might well help if your machine can cope with it.

Is your disk light flashing furiously when the windows go grey

---

### Post by oilchangeguy on 2008-11-21
> **Tony Flury said:**
> I have observed that the grey screen happens mostly when the system is swapping hard - so the memory upgrade might well help if your machine can cope with it.

Is your disk light flashing furiously when the windows go grey

the op states their computer already has 1gb of ram. this should be plenty. if you have a computer that uses swap/page file (windows) you've got a computer with problems.

---

### Post by Tony Flury on 2008-11-21
My laptop has 1GB RAM and often loads stuff into Swap - after all that is the point of Virtual Memory, and it is a integral part of the Unix design.

using swap space is a normal part of machine operation - and it is normal so efficient that the user never notices it. If you look at systems monitor you will often see the system is using swap space even while RAM is not fully 100% utilitised  - this is normal and often the user notices nothing.

The problem comes when RAM is fully loaded and there is a lot of swap space being used - at this point the system thrashes, since it has to spend a lot of time moving stuff in and out of swap space. At this point the user will probably notice system impacts and slow downs.

---

### Post by dmber on 2008-11-21
well, i got my RAM and i know i'm not imagining things: Firefox is "faster."  my system recognized the new RAM and everything has been great so far.  before, when i click on the drop-down arrow on the URL bar in Firefox, it took 2-3 seconds for my list to pop up.  now, it is instantaneous.  it has also sped up nautilus, as clicking on places/home used to take 5-10 seconds to get the nautilus window to open, it's nearly instantaneous now.

for $21, i'm really happy with my purchase :)

now, as far as swap goes, do i need to change that?  System/Administration/System Monitor/Resources shows that I have a 690 MB swap file.  Should that be bigger?  Smaller?

Thanks!

---

### Post by k3lt01 on 2008-11-21
after your Ram upgrade what are your system specs now?

I don't know about the netbook setups cause I have never played with one but for everything else I just do a standard 2gb of Swap. I do this cause I have the HHD space to spare.

---

### Post by dmber on 2008-11-21
> **k3lt01 said:**
> after your Ram upgrade what are your system specs now?

I don't know about the netbook setups cause I have never played with one but for everything else I just do a standard 2gb of Swap. I do this cause I have the HHD space to spare.
eeebuntu 8.04.1
2 GB RAM (pc2-5300)
Intel Celeron M 900 Mhz
Swap: 690.3 MB

Available disc space: 5.8 GB (out of an initial 14.2 GB)
I'm not sure what's up as far as video goes (it's on-board, that's obvious) but I run Compiz-Fusion with all the effects I want going (Expose, Widget Layer, AWN, etc.)

---

### Post by Kellemora on 2008-11-21
Hi dmber

I do a LOT of very heavy graphical printing through the LAN!

On our machines with only 512 megs of memory, the screen will gray out the whole time while the file is being sent to the printer.

On our machines with 1024 megs of memory, it still occasionally does this on super heavy graphic files, but for only a second or two.

It will also do it if we are checking huge image files and change from like 100% to 200% display of the images.  Again, the more memory, the shorter period of time the screen grays out.

Changing the swap file size from 1 gig up to 2 gigs on the 512 machine, or 2 gigs up to 4 gigs on the 1024 machine, made no difference on either machine on how long the gray screen would last.  So I now have all swap files set to 1024 regardless of how much memory a machine has onboard.

Soon to be switching our LAN to 1gig from 10/100, because I want to experiment with a Cluster to see if it speeds up our image work at all.

TTUL
Gary

---

