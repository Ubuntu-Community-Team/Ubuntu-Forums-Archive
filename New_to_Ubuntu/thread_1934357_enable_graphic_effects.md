---
title: "enable graphic effects"
date: 2012-03-02
forum: New to Ubuntu
---

### Post by karlhutt on 2012-03-02
i am new with ubuntu. i'm using ubunty 11.04 

i thought i had an NVIDIA graphics card, so i installed all i could find on the software center about NVIDIA graphics and then i found out my video card is not NVIDIA. 
very silly me.. 
so i unistalled all i could find about NVIDIA. 
i did it without paying much attention to what i installed and unistalled. 

the problem is that now my graphic interface works only WITHOUT effects. 
i am using ubuntu clasic with no effects. 
if i try to sign in with the Ubunty nicer look, it doesn't work. 

i believe I unistalled something that is crucial for that, but i cannot find it now. 
can anyone tell me what it i need to have installed to make it work?

thanks!

---

### Post by alphacrucis2 on 2012-03-02
> **karlhutt said:**
> i am new with ubuntu. i'm using ubunty 11.04 

i thought i had an NVIDIA graphics card, so i installed all i could find on the software center about NVIDIA graphics and then i found out my video card is not NVIDIA. 
very silly me.. 
so i unistalled all i could find about NVIDIA. 
i did it without paying much attention to what i installed and unistalled. 

the problem is that now my graphic interface works only WITHOUT effects. 
i am using ubuntu clasic with no effects. 
if i try to sign in with the Ubunty nicer look, it doesn't work. 

i believe I unistalled something that is crucial for that, but i cannot find it now. 
can anyone tell me what it i need to have installed to make it work?

thanks!


First things first:

```
sudo lshw -C display
```

Please post output from above back here.

---

### Post by karlhutt on 2012-03-02
here what comes out: 

  *-display:0             
       description: VGA compatible controller
       product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:16 memory:fc200000-fc27ffff ioport:1800(size=8) memory:d0000000-dfffffff memory:fc300000-fc33ffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:fc280000-fc2fffff

---

### Post by karlhutt on 2012-03-03
anybody has any idea?

i believe the proble is that i unistalled something that is needed to have the graphic effects available. 
right now, i can do pretty much everything, graphics, video, etc, but only on the classic look with no effects. 
if i try to load the nicer Ubuntu interface, it doesn't do it. 

how can i fix it?

---

### Post by Mark Phelps on 2012-03-04
Sorry to tell you this, but you probably can't.

You have an Intel 945 video chipset -- which is really OLD and came out around the time of Vista.  The fact that you can even see a desktop indicates that you have the proper Intel drivers already installed.

Unlike with AMD and Nividia, there are no restricted Intel drivers you can download and install.

---

### Post by karlhutt on 2012-03-06
well, that could be true.. but, it used to work before. 
i always used the other interface, the nicer one, and when i used the classic look, i used it with effects on. 
and now i can't. 
and it is the same computer. 
???

---

### Post by rectec794613 on 2012-03-06
Yeah we all miss the classic Gnome desktop...

You could try Gnome-Fallback, but as of now, it isn't perfect and Compiz doesn't work on it.

I would install [Lubuntu]("http://lubuntu.net/") or [Xubuntu]("http://xubuntu.org/") 11.10 and install Compiz if you want desktop effects. That's probably the best bet with your GPU.

---

