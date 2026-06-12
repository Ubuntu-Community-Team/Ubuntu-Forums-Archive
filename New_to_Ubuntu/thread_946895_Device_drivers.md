---
title: "Device drivers"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by felldin on 2008-10-13
Hi, I've just installed ubuntu 8.04 on my intel d945gclf2. Since I'm a noob, I wonder if I have all drivers installed correctly? I haven't done anything else besides running the ubuntu installation disc. Where can i check the drivers of my system and if there is some drivers that has to be updatet, how do I get and install them?

---

### Post by cl0ckwork on 2008-10-13
have you noticed anything not working as it did with windows? (if you had it)

ubuntu is pretty good with detecting hardware and getting the drivers for it but its good to play with your system for a while and work out any bugs that might be stuck in it

webcam?
microphone?
video display/resolution?
wireless/ethernet?
sound output?

the biggest problem is usually setting up a wireless internet card so if you're wired, then not much to worry about

---

### Post by kk0sse54 on 2008-10-13
Exactly which driver are you looking for? Test out your system and see if everything is working in good order ie Internet, Display etc etc. Usually Ubuntu will auto detect your hardware and if you require proprietary drivers will ask if you want to install them or not after you've logged into your new system.

---

### Post by Nxion on 2008-10-13
Is this on a clone? HP? Dell? Other?

TO be honest I have had all good luck with Intel based motherboards, I have never had to load anything.Everything It always is detected. Also you can check in

Systems>Administration>hardware Drivers

There you can see if maybe Ubuntu wants to load anything from the Restricted repos.

Does anything show up in there?

---

### Post by felldin on 2008-10-14
Thanks for all replies. I have checked under Systems>Administration>hardware Drivers but the box is totally empty. Does this means that all drivers have been found? 

I haven't experienced any problem (yet) with any device not working at all. The only thing that disturbs me is that I can't scroll smoothly. It 
might be because a slow processor and an integrated graphic card. 

Here below you can see the hardware I'm running on:
[I]Manufacturer: 		Intel D945GCLF2
Processor: 		Integrated Intel Atom 330 @ 2 x 1.60GHz (Silverthorne 45nm)
Chipset: 		Intel 82945G (ICH7)
Memory: 		2GB DDR2 667MHz Memory
Graphic Interface: 	Intel GMA 950
[/I]
Do you thing that I might have some bad driver or do you thing that my hardware are to weak to scroll smoothly in firefox?

---

### Post by hyper_ch on 2008-10-14
intel is generally very well supported and everything works out of the box there. :)

---

### Post by felldin on 2008-10-14
Ok, thank you. I guess I have to live with my slow hardware =)

---

### Post by Nxion on 2008-10-14
> **felldin said:**
> Thanks for all replies. I have checked under Systems>Administration>hardware Drivers but the box is totally empty. Does this means that all drivers have been found? 

I haven't experienced any problem (yet) with any device not working at all. The only thing that disturbs me is that I can't scroll smoothly. It 
might be because a slow processor and an integrated graphic card. 

Here below you can see the hardware I'm running on:
[I]Manufacturer:         Intel D945GCLF2
Processor:         Integrated Intel Atom 330 @ 2 x 1.60GHz (Silverthorne 45nm)
Chipset:         Intel 82945G (ICH7)
Memory:         2GB DDR2 667MHz Memory
Graphic Interface:     Intel GMA 950
[/I]
Do you thing that I might have some bad driver or do you thing that my hardware are to weak to scroll smoothly in Firefox?

I have experienced the same issue you have on Firefox. It's not a bad driver, you can try enabling Smooth scrolling to see if that helps. I leave it off because I notice a little bit of lag with it on.

To enable it go to EDIT > PREFERENCES > ADVANCE: On the general tab near the bottom you will see "Smooth Scrolling" IS it enabled(has check mark)? if not, just put a check mark and restart and see how that works for ya.

---

### Post by ifallacy on 2008-10-17
quick question - does your ethernet work fine? for some reason, my ethernet connection is really spotty and when i run ifconfig, it always tells me that i have a lot of dropped packets...

---

### Post by nixforme on 2008-10-17
> **ifallacy said:**
> quick question - does your ethernet work fine? for some reason, my ethernet connection is really spotty and when i run ifconfig, it always tells me that i have a lot of dropped packets...

What serveice do you have?

---

### Post by ifallacy on 2008-10-18
this is a freshly installed version of ubuntu 8.04 after i ran the latest critical and recommended updates in the GUI - I did use macchanger to change my MAC address once, and for some reason, it doesn't reset back to the original MAC address even if I reboot with the live CD (although i think the MAC address issue might be something seperate altogether?)

let me know if you need any more info - i'm not quite sure what else would help =]

---

### Post by fortran01 on 2008-10-24
> **felldin said:**
> Hi, I've just installed ubuntu 8.04 on my intel d945gclf2. Since I'm a noob, I wonder if I have all drivers installed correctly? I haven't done anything else besides running the ubuntu installation disc. Where can i check the drivers of my system and if there is some drivers that has to be updatet, how do I get and install them?

Appears to be a bug in Linux kernel:
[http://www.gossamer-threads.com/lists/linux/kernel/982159](http://www.gossamer-threads.com/lists/linux/kernel/982159)

---

### Post by fortran01 on 2008-10-26
This is the fix:
[http://linuxtrek1.blogspot.com/2008/10/ubuntu-on-intel-d945gclf-with-intel.html](http://linuxtrek1.blogspot.com/2008/10/ubuntu-on-intel-d945gclf-with-intel.html)

Patched the most recent kernel.

---

### Post by stek79 on 2008-11-10
> **felldin said:**
> Ok, thank you. I guess I have to live with my slow hardware =)

Hi,
  can you please tell us which sites were slow under firefox?

I think FF is not so fast on some sites, perpahs this is the reason.

What kind of applications do you run other than FF? Are they slow?

Thanks

---

### Post by hendrik_morskate on 2008-11-18
Hello,

I have just bought this board as well and I'm still having some issues with this board in combination with Kubuntu 8.04.
- Ifconfig shows loads of dropped packets (in the billions), I guess I can fix that with the new driver.
- The sound volume is very low, haven't found a solution yet (tried:
3stack-dig,3stack-6ch, 3stack-6ch-dig,6stack-dig, lenovo-101e,		  eeepc-p701 and eeepc-ep20 in after "options snd-hda-intel model=" in/etc/modprobe.d/alsa-base )
- TV-out is in black/white (guess it is in NTSC instead of PAL)

Does anyone have experience in solving any (or all... :-)) of these problems?

Cheers,
Hendrik

---

### Post by hendrik_morskate on 2008-12-14
Hi,

Small update on this, I'm now ignoring the dropped packets since it doesn't seem to affect my connection in any way.

As for the sound volume, with alsamixer I've set every volume level to 100% and the volume is quite OK without any distortion as far as I can notice.

I have fixed the TV-out problem by buying an Nvidia PCI graphics card. That was not as easy as I though however.
The problem was that you can't disable the onboard graphics chip, if you try Kubuntu will not boot anymore (processor lock-ups). So you have two functional graphics cards in the system and all the automatix Xorg.conf scripts will try and load the nvidia driver on the Intel board which will cause it to crash KDE. The solution is to manually edit xorg.conf and set 

BusID          "PCI:4:0:0"

in the "Device" section.

And oh yes, I've also replaced the fan with a Scythe Mini Kaze 40x40x10, silent, 3500rpm one which is really silent compared to the one Intel ships with the board.

Hope this helps someone.
Cheers,
Hendrik

---

