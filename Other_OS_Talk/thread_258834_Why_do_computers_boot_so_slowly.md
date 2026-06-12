---
title: "Why do computers boot so slowly?"
date: 2006-09-16
forum: Other OS Talk
---

### Post by Sprogg2001 on 2006-09-16
Ok let me rephrase that, why do they still boot the way they do? 

I am by no means an "expert" but here is my undertanding of what goes on when you push the big "on" button.

1)Basic Input Output System loaded from ROM chip from motherboard

2) by means of drivers Input/output devices are recognised ie vga card, keyboard, hardrives 

3) Drivers are loaded for the rest of the system hardware 

4) Instructions from the hard drive are executed and the system Operating system begins to start

(please dont flame me on how little I know about all this)

why are mother boards not fitted with flash drives that after the bios loads restore the system state to its exact state before it was switched off, and I dont mean hibernation 

I mean bios then flash drive then os in the exact same place you left it in less than 5 seconds it can be done, but why are there no machines that do it or am I missing somthing?

---

### Post by nereid on 2006-09-16
It can be done in 5 seconds with the help of a flash drive, but we also got the old grandpa BIOS still with us. IMHO this has mostly to do with compability and that no one has done it for the home users. The desktop market is not that big as it seems to be, so everything is a little bit slow here (except 3d video cards).

---

### Post by Sprogg2001 on 2006-09-16
so wheres the bottle neck that slows it all down the bios I dont think so because that loads pretty fast, but your right its has been with us since the first pc was invented and has not changed that much at all 

Loading drivers, detecting hardware hmmm ok I say about 1/3 of the time wasted loading the the same old drivers.  

But the operating systems now they hog the whole arena loading exacty the same instructions again and again and again  why cant they just keep that part of the os in a faster piece of hardware?

---

### Post by cptnapalm on 2006-09-16
Because speeding it up costs money.  It would not be until well after the point of purchase that anyone would begin complaining about it, so there is no sale advantage to it.  The competition is already pretty fiece so it would be like putting up a few seconds saved on boot vs. the competition's dual ethernet jacks.  The additional functionality would win out.

The only way anyone would bother is if it was just as cheap to produce, if there were significant time savings which would lead to higher sales or if a new industry standard were set, so everyone else would have to do it too.

---

### Post by 3rdalbum on 2006-09-17
As Macs use EFI rather than a BIOS, it might be a good idea to start lobbying Apple for this functionality. Their rapid pace of software development also means that they're likely to have it implemented before many more OS X versions go by.

Windows Vista doesn't even support EFI unless it has a "BIOS compatibility mode", so I think the PC world won't crack onto this idea for at least another 4 or 5 years.

---

