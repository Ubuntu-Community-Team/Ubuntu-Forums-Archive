---
title: "Lost USB drivers?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by sevenape on 2008-04-24
Hi I recently converted to ubuntu and have been playing around (more fool me) with hardy heron, It was the case that my computer would talk to various things via usb like my mp3 player, psp, external hard drive etc but now it seems it won't recognise anything I plug in to the USB except for my mouse. I was thinking maybe it happened with the recent update session I had yesterday. Does anyone know why this is, or more importantly how I can get my devices on speaking terms again?

Thanks very much in advance

---

### Post by sevenape on 2008-04-24
I ran lsusb and the computer isn't detecting anything except my logitech mouse :(

---

### Post by Tatty on 2008-04-24
Is there anything you did that may have triggered this?

---

### Post by sevenape on 2008-04-24
umm very possibly... I've been installing and uninstalling games recently.. 

but that's it really... I haven't been messing around with anything hardcore... I did unplug my camera without dismounting it the other day by mistake :/

---

### Post by Tatty on 2008-04-24
So when you run lsusb, do the things you plug in simply not show up?  It could be a hardware problem.  Try booting to a live CD and see if that can detect your devices when you plug them in.

---

### Post by sevenape on 2008-04-24
this is what it reads: 

Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c018 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

will try using live cd see what happens

---

### Post by sevenape on 2008-04-24
No dice... same results with live cd 


guess this means a new computer right? It's a 3 year old laptop (almost to the day) So I imagine it's got it's fair share of issues

---

### Post by Tatty on 2008-04-24
Im not totally sure what to suggest.  
I assumed it was a desktop so i was going to suggest opening it up and seeing if something has got disconnected, but clearly thats not the case with a laptop.

The only thing i can think of is checking out the bios to see if there might be some silly thing gone wrong in there.  Aside from that im afraid i dont know what else to try... other than maybe a different distro to see if its hardy specific... :(

---

### Post by sevenape on 2008-04-24
do you think I might have done something fiddling around in the synaptic manager?  I'll try a complete reinstall at the weekend and see what happens. My live CD is gutsy so I dunno if it will help :D

Thanks for helping out anyways :) I'm not at all sure about BIOS tbh!


Thing is under windows sometimes the usb ports wouldn't work when a disc failed to burn and I had to restart to get it working again. I did burn a cd yesterday but it went ok and I assumed that problem would be windows specific... Prhaps not!

---

### Post by Tatty on 2008-04-24
do you still have windows installed on the machine?  see if it happens in that.

---

### Post by sevenape on 2008-04-24
nope i got rid of it for better or worse... maybe worse hehe! 

i'll try getting a usb hub if the reinstall doesn't work!

---

### Post by sevenape on 2008-04-24
so... the live cd didn't work, I turned off the comp and turned it on with my external hard drive plugged in and turned on by mistake... now everything works!!! very odd!!!

---

### Post by Tatty on 2008-04-24
well, at least thats a result!  :)

---

### Post by sevenape on 2008-04-24
:D yeah it definitely is of sorts!

Thanks for helping out!

---

