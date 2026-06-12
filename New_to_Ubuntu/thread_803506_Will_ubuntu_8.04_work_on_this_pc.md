---
title: "Will ubuntu 8.04 work on this pc?"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by kilis on 2008-05-22
These are the spec:
Intel Dual Core 2 E8400 3.0Ghz
ASUS Nvidia geforce 8600GT 512 MB
usb bluetooth :D
Card reader inside pc
I think asus mother board p5k.
Will it work on that new machine?

---

### Post by indytim on 2008-05-22
Easy answer... download and burn the LiveCD iso.  Boot to the CD and try it out :)

IndyTim

---

### Post by kilis on 2008-05-22
> **indytim said:**
> Easy answer... download and burn the LiveCD iso.  Boot to the CD and try it out :)

IndyTim

I will get the pc only next day.

---

### Post by TheLions on 2008-05-22
it will work but bluetooth and card reader could be a problem...

---

### Post by Cresho on 2008-05-22
NAW!  I have no problems what so ever with my bluetooth.

---

### Post by Inxsible on 2008-05-22
It will definitely work. Bluetooth may or may not be a problem - depending on what make or model it is. I have used bluetooth on my machine without any problems whatsoever.

The card reader will work only for sd cards. Sony Memory sticks will not work under linux.

---

### Post by bigken on 2008-05-22
> **TheLions said:**
> it will work but bluetooth and card reader could be a problem...


bluetooth and card readers work on all my Linux pc's

---

### Post by kilis on 2008-05-22
i mean build in card reader like floppy drive. And the bluetooth usb is from epox.

---

### Post by bigken on 2008-05-22
Like indytim said try the live cd

---

### Post by kilis on 2008-05-22
> **bigken said:**
> Like indytim said try the live cd

I will get my new pc only next day.

---

### Post by stchman on 2008-05-22
> **kilis said:**
> These are the spec:
Intel Dual Core 2 E8400 3.0Ghz
ASUS Nvidia geforce 8600GT 512 MB
usb bluetooth :D
Card reader inside pc
I think asus mother board p5k.
Will it work on that new machine?

I have a PC with an Asus P5K and it works very well.  Ethernet, chipset, firewire, USB, Core 2 Quad proc all worked OOB.


The 8600GT will work after restricted driver install.
Ubuntu has some Bluetooth support.
If the card reader is hooked up via USB then it should work.

I agree, load the 8.04 live CD and give it a try.

---

### Post by kilis on 2008-05-22
> **stchman said:**
> I have a PC with an Asus P5K and it works very well.  Ethernet, chipset, firewire, USB, Core 2 Quad proc all worked OOB.


The 8600GT will work after restricted driver install.
Ubuntu has some Bluetooth support.
If the card reader is hooked up via USB then it should work.

I agree, load the 8.04 live CD and give it a try.
No the card reader is build in the pc like floppy. Card reader is not USB. But thanks :)

---

### Post by stchman on 2008-05-22
> **kilis said:**
> No the card reader is build in the pc like floppy. Card reader is not USB. But thanks :)

How does the card reader connect to the motherboard?

---

### Post by Efros on 2008-05-22
> **kilis said:**
> No the card reader is build in the pc like floppy. Card reader is not USB. But thanks :)

I can guarantee the card reader will be USB but connected directly to the mobo, The only other card reader I have seen is 1394 external and very expensive.

---

### Post by Living2007 on 2008-05-22
> **kilis said:**
> These are the spec:
Intel Dual Core 2 E8400 3.0Ghz
ASUS Nvidia geforce 8600GT 512 MB
usb bluetooth :D
Card reader inside pc
I think asus mother board p5k.
Will it work on that new machine?
I would say that is perfect

---

### Post by philinux on 2008-05-22
Working Fine here 64 bit, java flash etc etc.,

---

### Post by GlennB on 2008-06-21
Hi,

I found this thread while trying to find out more about a problem with the Gigabit Ethernet NIC that's built in to the Asus P5K. I started getting errors with scp and rsync while copying my music collection between machines (around 120GB of data). 

It seems there is a bug in the Attansic L1 driver that affects machines with 4GB or more RAM installed, which may be to blame. There is a bug notification at [http://atl1.sourceforge.net/](http://atl1.sourceforge.net/)

My machine is almost exactly the same as the specs. here, but I have a 256MB GeForce 8600GT. Does anyone who has this combo working have 4 gigs of RAM installed by any chance? Before I pull the box to bits and start yanking RAM, replacing NICs and reseating cards, it would be great to know if anyone else is having network problems, and if so, are you using 4GB of RAM?

The symptom I'm seeing during large scp / rsync copies is an error like this:

Disconnecting: Corrupted MAC on input.00
rsync: writefd_unbuffered failed to write 4092 bytes [generator]: Broken pipe (32)
rsync error: unexplained error (code 255) at io.c(1123) [generator=2.6.9]

Google finds a bunch of similar error reports, but no suggestions for fixes that have worked for me. I'm using 8.04 32 bit, and have tried both the server and generic kernels - they behave the same. Maybe I should try the 64 bit version?

Edit: Cancel the above - I tried a different NIC, with the same results. Could be the RAM. I'll run memtest for a while and see what happens.

Thanks all,

Glenn.

---

