---
title: "IGP + Nvidia on the same system: solution"
date: 2011-05-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-05-23
Optimus on Linux Problem Solved

[http://www.martin-juhl.dk/](http://www.martin-juhl.dk/)

---

### Post by Framli on 2011-05-23
Kind of solved. It's far from being optimal on a lot of systems.

If you have an hybrid graphics system, 
please join [https://launchpad.net/~hybrid-graphics-linux](https://launchpad.net/~hybrid-graphics-linux), 
your input and hardware testing is very valuable. :)

---

### Post by MacUntu on 2011-05-23
Yeah, doesn't sound anywhere near solved from that blog post. I'm so glad I asked around before buying my Optimus ThinkPad (BIOS switch).

---

### Post by dino99 on 2011-05-23
of course nothing is solved but the first step is

this post is to let you know about those issues: test and report to help devs

---

### Post by Starks on 2011-05-23
The 2.6.40 kernel should have Optimus support for laptops with a mux. But there are 4 problems with that.

1. Not all Optimus laptops have the mux. It's pretty much 50/50 these days.
2. Bumblebee works on 98% of laptops it's been tested on.
3. While the kernel will have Optimus support; -intel, -nouveau, and the xserver probably won't have the necessary bits.
4. It'll be Nouveau-only as far as I know.

---

### Post by MacUntu on 2011-05-23
Well, you can switch from nouveau to the BLOB without rebooting (X needs a restart), but it's not very user friendly. Also what does "Optimus support" really mean? Optimus should switch cards on-demand - is that meant by "Optimus support" or just the manual switching?

Will try Bumblebee as soon as I have time.

---

### Post by MAFoElffen on 2011-05-24
> **Starks said:**
> The 2.6.40 kernel should have Optimus support for laptops with a mux. But there are 4 problems with that.

1. Not all Optimus laptops have the mux. It's pretty much 50/50 these days.
2. Bumblebee works on 98% of laptops it's been tested on.
3. While the kernel will have Optimus support; -intel, -nouveau, and the xserver probably won't have the necessary bits.
4. [COLOR=Black]It'll be Nouveau-only as far as I know[/COLOR].
Curious and trying to understand this:

[COLOR=Black]Seems to me that basically, the Oprtimus is a chipset that was there to manage and control other or multiple graphics chipsets beyond it... As sort of a com-server for video.

Where the problem is that the OS system was querying the video hardware and only seeing the first chipset and nothing beyond it.  The sandy bridge chipset in gaming laptops (w/ nVidia or ATI Xfires) is doing the same and running into the same "wall."  

I would try to help people diagnose and get their graphics going on those laptops and linux tools were finding the video modes of the first chipset, but only lspci was finding what was beyond it... not xrandr or hwinfo.

[/COLOR][COLOR=Black]My question with all this... Does the Sandy Bridge chipset fall into this somehow?  [/COLOR][COLOR=Black]Has anyone heard anything on help for the sandy bridge chipsets (or might it be include in this)?
[/COLOR]

---

