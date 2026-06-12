---
title: "Installing ATI Drivers"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by damonjablons on 2008-07-22
hey forumers,

sorry if you've seen this post a million times, i just can't seem to find something that tells me how to do this.

i just went through the steps of re-compiling my kernel just in order to get my Sound Blaster X-Fi soundcard to work.  since i've rebooted, i've lost my ATI drivers.  

how do i reinstall them?  thanks in advance!

-damon

---

### Post by Thingymebob on 2008-07-22
[http://wiki.cchtml.com/index.php/Ubuntu]("http://wiki.cchtml.com/index.php/Ubuntu") Always works for me

---

### Post by damonjablons on 2008-07-23
I tried following that wiki, but my graphics card is still not being used :(.  and of course, when i restarted, my sound card stopped working as well!!!

so, to recap:

I need help installing the driver for my ATI videocard

and

I need help installing the driver for my Sound Blaster X-Fi soundcard (which stopped working after a reboot!)

---

### Post by Troll_the_Great on 2008-07-23
For the ATI drivers you can try EnvyNG. Open a terminal and type:
```
sudo aptitude install envyng-gtk
```.
After that you can find it in Applications-System Tools-EnvyNG.
Start it and it will automatically install the drivers for you.
I don't know how to help you regarding the sound problem.
Cheers!

---

### Post by S1xp4ck on 2008-07-23
> **damonjablons said:**
> I tried following that wiki, but my graphics card is still not being used :(.  and of course, when i restarted, my sound card stopped working as well!!!

so, to recap:

I need help installing the driver for my ATI videocard

and

I need help installing the driver for my Sound Blaster X-Fi soundcard (which stopped working after a reboot!)

I had a problem with the audio driver included with my ATI HD card defaulting over my Soundblaster Audigy.   I am curious to see if you are having a similar problem.  Could you open terminal and type

```
cat /proc/asound/modules 
```

and paste the result here please?  Your Ati driver will have to be installed to see if this is indeed the problem.

---

### Post by damonjablons on 2008-07-23
> **Troll_the_Great said:**
> For the ATI drivers you can try EnvyNG. Open a terminal and type:
```
sudo aptitude install envyng-gtk
```.
After that you can find it in Applications-System Tools-EnvyNG.
Start it and it will automatically install the drivers for you.
I don't know how to help you regarding the sound problem.
Cheers!


After installing the drivers using Envy, I reinstalled the sound drivers and everything seems to be working now.  I appreciate the help!

---

