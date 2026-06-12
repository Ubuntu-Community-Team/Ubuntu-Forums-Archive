---
title: "Speed up and optimize?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by thecheeks on 2008-09-03
im new to linux but getting a lot more accustomed to it. in fact, i can see a LOT of potential in using this. I stopped using windows 2 years ago for OSX.

ubuntu seems to be running well, but could be faster considering the hardware. this computer has been chopped up with different hardware, cpu is no doubt a bottleneck

specs:
AMD Athlon 1.1ghz
2.5gigs RAM
Nvidia 7800GS (i DID install latest nvidia drivers)
C-Media soundcard (works fine)
[here is a much more detailed system profile [http://thecheeks.googlepages.com/hardwareprofile.html](http://thecheeks.googlepages.com/hardwareprofile.html) ]

the gfx and ram seem to be great stats for linux, but i feel like the AMD is being held back.

i did the normal ubuntu system updates so whatever those are at, is what i have, however i feel like theres a new kernel or core components that can be upgraded for better support?

---

### Post by rossjman1 on 2008-09-03
You can disable some services that you don't use (Tracker and Bluetooth are 2 big ones). You can also stop some things from starting with Gnome.

Services: System > Administration > Services
Sessions: System > Prferences > Sessions

---

### Post by kerry_s on 2008-09-03
> **thecheeks said:**
> im new to linux but getting a lot more accustomed to it. in fact, i can see a LOT of potential in using this. I stopped using windows 2 years ago for OSX.

ubuntu seems to be running well, but could be faster considering the hardware. this computer has been chopped up with different hardware, cpu is no doubt a bottleneck

specs:
AMD Athlon 1.1ghz
2.5gigs RAM
Nvidia 7800GS (i DID install latest nvidia drivers)
C-Media soundcard (works fine)
[here is a much more detailed system profile [http://thecheeks.googlepages.com/hardwareprofile.html](http://thecheeks.googlepages.com/hardwareprofile.html) ]

the gfx and ram seem to be great stats for linux, but i feel like the AMD is being held back.

i did the normal ubuntu system updates so whatever those are at, is what i have, however i feel like theres a new kernel or core components that can be upgraded for better support?


tweak it and use hibernate instead of a straight shutdown, you'll need a large swap recommend 2gb at least.

---

### Post by Tatty on 2008-09-03
On the whole there arent all that many parts of ubuntu which need tweaking to optimise performance, as generally it is pretty streamlined out of the box, althoug there are a few tweaks... there are several threads with suggestions buried somewhere in the forums, see if you can find them.

In the meantime try this [http://ubuntuforums.org/showpost.php?p=1255511&postcount=43](http://ubuntuforums.org/showpost.php?p=1255511&postcount=43)

And you can speed up boot by reprofiling [http://ubuntuforums.org/showthread.php?t=254263](http://ubuntuforums.org/showthread.php?t=254263)  (i think the "bonus hack" on this page is obsoleted now, but have a look)

---

### Post by wolfen69 on 2008-09-03
there is only so much you can do.  first realise that memory is going to be your best ally
. second, realise that if one os doesnt work, dont be afraid to try another.

it's easy for me to say because i have every ubuntu cd on hand, and have tried out many different distros and os's. i'm not afraid of making a mistake. my computers are flexible. and all my personal stuff is on dedicated drives.

---

### Post by thecheeks on 2008-09-03
on a side note, i made by swap 2gigs, thinking i only had 1gig of ram. should my swap be 5gigs instead? and if thats true, is it possible to resize  swap with freespace from my other partition?

---

### Post by kerry_s on 2008-09-03
> **thecheeks said:**
> on a side note, i made by swap 2gigs, thinking i only had 1gig of ram. should my swap be 5gigs instead? and if thats true, is it possible to resize  swap with freespace from my other partition?

5gig swap is to much, 2gig is perfect, when you hibernate it saves the state/snapshot of the system to swap. when you start up again it loads it right back the way it was, so you get the same performance as if you never shutdown, feels like starting your system with a toram option. :)

i  made a launcher for mine and have it set for nopasswd with sudo.
for tweaking just use the config editor and turn on low resource mode, also turn off animations where ever you find them, disable aiglx and compiz.

---

### Post by hyper_ch on 2008-09-03
enable preload and install bootchart to see where it takes how long to start things during bootup.

Besides, as you have 2.5 GB ram and probably are running a 32-bit system then you cannot use more than 1.5 gb addition swap. You could however recompile the kernel with PAE or use one of the PAE enabled kernels.

---

