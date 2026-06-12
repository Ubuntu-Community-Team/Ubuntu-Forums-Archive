---
title: "sound and video card issues"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by Avidbullet on 2013-04-01
hello everyone. im new with ubuntu, and ive been looking on forums to try to figure things out myself, but half of it just seems like a different language than im used to for windows. since my soundcard doesnt even seem to be recognised, a video tutorial is even more confusing. i would really love to get my sound card working and learn how to use some of the tools that seem to be necessary to really understand and operate my system.

current video card is working but unrecognized - im using a Radeon HD 4000 series. (i have gone to the radeon site and downloaded the proper linux 64-bit driver) no idea what to do with it from here.

current sound card doesnt even show up. no listed linux driver files on the M- Audio site. i am using the M-Audio Delta 66, i understand i will have to learn about JACK, or some variants to use this once i can get it to be recognized.

would really like know what ubuntu needs me to do, and how to do it, and at the same time, start to understand how it works.

help greatly appreciated

______________________________

again, already looking through forums for a solution, i got this

     [I]  "I have my sound card working!!
       I set a diferent model for my Delta66 in /etc/modprobe.d/alsa-base. I put "options snd-ice1712 model=delta1010lt".[/I]"

so i did this, and it wont let me overwrite the file with the added line. any thoughts?

---

### Post by Bashing-om on 2013-04-01
Avidbullet; Hi Welcome to the forum.
As I understand it ... ATI no longer supports the older HD4XXX series cards, and one has to use what is available (best course anyway, all considered) within ubunt's support structure. 
Let's look and see what we are working with; 
To see your graphics card and info; Post the out put of terminal commands:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga;
```

And very helpful to know what version/distro you have installed on your system.[INDENT=3]
just try'n to help

[/INDENT]

---

