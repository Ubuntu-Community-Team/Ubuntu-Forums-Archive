---
title: "confusing system monitor!"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Zopiac on 2008-08-09
in the attachment i have an unexplainable problem in my system monitor; also my computer's been acting very slow recently, and freezing very often. Please Help D':

---

### Post by InfinityCircuit on 2008-08-09
It looks like something might be leaking memory.  Does this problem persist through a reboot?

---

### Post by Zopiac on 2008-08-09
> **InfinityCircuit said:**
> It looks like something might be leaking memory.  Does this problem persist through a reboot?
it's been going on for a week or so, but things only started freezing a few days ago.

i recently installed new RAM, but i just got it, so i can get e replacement, if neccesary.

---

### Post by bpowell2005 on 2008-08-09
I think your problem is you have a program tying up about 17 Exabytes of memory...Unless you have that kind of RAM installed, it'll slow things down!

Seriously though, you might want to go to (in your system monitor) "View" and check "Dependencies" this will help you see which program specifically is running away with your memory.

---

### Post by bpowell2005 on 2008-08-09
> **Zopiac said:**
> it's been going on for a week or so, but things only started freezing a few days ago.

i recently installed new RAM, but i just got it, so i can get e replacement, if neccesary.

You might want to run the memtest from the grub boot menu just to see if the RAM is okay. If you have errors, you can pull one stick at a time to help isolate which one is bad.

---

### Post by Zopiac on 2008-08-09
> **bpowell2005 said:**
> You might want to run the memtest from the grub boot menu just to see if the RAM is okay. If you have errors, you can pull one stick at a time to help isolate which one is bad.

i only have one stick >.<

also, a good half of my programs are pumping out 17 'exabytes' of memory :\

the 'dependencies' button didnt seem to do anything...what is it supposed to do?

edit: never mind, i figured out what it does...but it doesnt seem to be helping at all... i dont know

and i only have 1GB of RAM, i tried running with a 2GB too, so its not the specific RAM.

i believe...what are the limits of various hexidecimal strings? it might be telling me that the programs are pumping out the max my processor can handle each (64bit; i dont know, how much can they handle???)

i believe my motherboard's RAM slots are going bad; i dont trust the place where i got the computer anymore anyways >.< (their 'best available' computer only has 1gb ddr 400 ram, and i only got a 280w p/s from them)

also, last time i tried a memtest it ran for 3 days and i had to cancel it, this was on a 756mb pc100 ram pentium III comp tho, how long is it supposed to take???

---

### Post by bpowell2005 on 2008-08-09
Memtest will run forever...it keeps repeating the same test...so once you've seen one pass complete, you know you're ram is "good"...you can let it run a few hours just to ensure your RAM doesn't fail after it heats up or something....3 days is a good test!

I think infinitycircuit called it right, you have a program with a memory leak...it's just manifesting as a variety of programs but they're probably all linked...I don't know how to tell you to start hunting it down.

Maybe start closing programs or eye-candy that you have installed, see if everything looks okay...keep shutting down services until you find the culprit.

---

### Post by xzaverax on 2008-08-09
I would try to isolate the program that is using so much memory, I doubt it is more then one, that it is just linked to them all, so if you can find a program that they all depend on to run you will have found the problem.

---

### Post by Zopiac on 2008-08-30
well im still having this problem (i havent used the comp since a day after my last post anyways D: ) but if anyone has scrounged up any more information on this, i would be very grateful!

More possibly potential info:

Gnome Do, Emerald, and Python are all pumping out tons of memory, do they all use Python? perhaps i have to reinstall that, or something. I would not be surprised, maybe a recent update of its is not compatable, or something...

perhaps i should check out emerald and gnome-dos sites to check it out :)

---

### Post by Zopiac on 2008-08-31
well it turns out Kopete, Opera, XFCE4-Terminal, the system monitor, and all but ONE python instance has this bug. I tried reinstalling python (sudo apt-get remove python && sudo apt-get install python) but it crashed in the middle of removing, i believe (only terminal crashed). I tried it again, and it gave me:

zopiac@zopiac:~$ sudo apt-get remove python && sudo apt-get install python
sudo: unable to resolve host zopiac
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
zopiac@zopiac:~$ sudo dpkg --configure -a
sudo: unable to resolve host zopiac

Synaptics Package Manager won't let me make any changes, but when i looked at Users and Groups, it said user Zoiac was there and had all of the administrative priviliges!

---

### Post by Zopiac on 2008-09-06
Well it seems as if this is only happening in Gnome, as in KDE and XFCE (dunno about IceWM) the programs arent doing this.

One curious thing im noticing is that pidgin itself doesnt freeze the computer, but a chat window does. about 10 seconds after i open a chat the window fades to black and white, and not even force logout doesnt work.

i fixed the 'sudo: unable to resolve host zopiac' problem, but i cant reinstall python from within X/K/Ubuntu, maybe IceWM, but im going to try it at the lognin screen...

---

### Post by hyper_ch on 2008-09-06
you can use sudo?

---

### Post by Zopiac on 2008-09-06
yes, i can use sudo....

well i reinstalled python but on gnome it still says its using the RAM...

and it turns out that YES, theoretically, the maximum for 64Bit rocessors is 16 exabytes, just as i hypothesized :P

---

### Post by hyper_ch on 2008-09-06
why shouldn't it use the ram upon reinstalling?

---

### Post by Zopiac on 2008-09-06
> **hyper_ch said:**
> why shouldn't it use the ram upon reinstalling?

huh?

---

