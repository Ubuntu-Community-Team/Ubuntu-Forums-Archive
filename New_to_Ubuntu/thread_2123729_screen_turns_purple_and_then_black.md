---
title: "screen turns purple and then black"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by amz1 on 2013-03-08
Hi everyone

I've decided to try Ubuntu 12.4 32 bit lts after my Windows 7 desktop computer gave me so many headaches.
I have installed ubuntu alongside a reformatted version of windows 7. After reboot, i managed to enter my personal details and machine name etc and rebooted again. Now when i try to boot, i can select what operating system to chose from then the screen turns purple and then black but nothing happens afterwards,


could it be that i use to use windows 64 bit and now im using ubuntu 32 bit? Im not really a tech expert so please advise in laymans terms thanks.

---

### Post by DomOctober on 2013-03-08
Well, if you have a 64-bit system, you can run the 32-bit version without issue. The main reason I'd suggest running the 64-bit version is to take advantage of additional memory. 
This, however, sounds like video driver issue or the like. Were you able to run the live CD to test the OS?

---

### Post by MasterWayne on 2013-03-08
do you have broadcomm wlan?
if so, enter your BIOS settings and set your pxe (network) boot as 1st boot options

---

### Post by DuckHook on 2013-03-08
> **MasterWayne said:**
> ...enter your BIOS settings and set your pxe (network) boot as 1st boot options

PXE is designed to load the whole OS from over a network and was developed for diskless workstations or highly structured uniform boot environments. This is not the OP's situation and could make his computer unbootable from his HDD. I would second the recommendation to try booting from a LiveDVD/USB. The objective would be to test if a generic environment works. From a working LiveDVD session, additional tests can be run to collect data and narrow down problem.

---

### Post by fantab on 2013-03-09
Give us some details about your machine, especially what Graphics Card you have, make and model to be able to help you quickly. As also as suggested, boot your Ubuntu CD/USB and use the option to "Try Ubuntu". See if it runs properly and satisfactorily and report back. "Try ubuntu" option boots you into a working Ubuntu desktop without installing anything on your machine.

---

### Post by mörgæs on 2013-03-09
Even better: Try X/Lubuntu in a live boot, as they are less demanding with regards to the graphics card.

---

### Post by amz1 on 2013-03-09
Thanks for all the replies. This community is very helpful.

BOOTING FROM USB WORKS! I can see the desktop - I booted the ubuntu operating system from a USB and was successful in doing so.
 
Therefore i dont think its a graphic card issue. My computer is a HP core i5 desktop running windows 7 dual boot with 6gb ram and Nvidia GT 230 graphics card. Im in the process of reinstalling the entire operating system again.

---

