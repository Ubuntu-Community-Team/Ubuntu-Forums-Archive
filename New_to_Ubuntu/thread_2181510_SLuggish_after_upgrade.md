---
title: "SLuggish after upgrade"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by digimark on 2013-10-18
Hi All,

Friday problem.....I took the upgrade from 13.04 to 13.10 overnight. However my machine now runs very sluggishly.....ie apps take longer to open, and I get alot of system errors.....not major just annoying really.....nothing else has changed.....its not its usual snappy self....

Has anyone else seen this? are there any 'tweaks' I can do to get it back to normal?

Thanks

---

### Post by stinkeye on 2013-10-18
Were you running a proprietary driver before the upgrade?
Check your not being software rendered....
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by okkadiroglu on 2013-10-18
Hi,

I have similar problems, my computer is sluggish too. Also when I open files menu I can change directories but when I click on to a file it crashes. If I try FileManager I have no problem.

In my case I get:

oyo@okk001:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce 8500 GT/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 304.88

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

---

### Post by digimark on 2013-10-22
Hi all,

I took the upgrade to 13.10 from 13.04 last week. I have to say the experience has not been great. The system errors I can handle but its just runs s-l-o-w.....I am using on a acer c7 chromebook. All the last versions rand fabulously no issues....but 13.10...is really not great.....

Has anyone had the same issue? any suggestions would be gratefully received!

/M

---

### Post by digimark on 2013-10-22
Hi Everyone,

I recently upgraded to 13.10 from 13.04. Upgrade went well...all loaded fine, boots ok (with a few errors but these dont seem to be an issue (or are they?) 

anyway the whole machine now runs s-l-o-w....windows take an age to open and close, scrolling though documents lags like you would not believe...

I have no idea if something is wrong, didnt load or the error dialogue boxes are telling me something I need to address.

Any advice muchly appreciated!

BTW 130.4 worked great.....maybe I should not have accepted the upgrade...silly me lol.

Thanks

/M

---

### Post by digimark on 2013-10-22
Hi Stinkeye,

that command gives me

Gen6+ requires Kernel 3.6 or later.
unity_support_test: ../../../../../src/mesa/main/context.c:1501: _mesa_make_current: Assertion `newCtx->Version > 0' failed.

not sure what to make of it. I wasnt running aythign propieatry I don thtink...13.04 ran like a top...no issues at all...

I am at a loss.....

---

### Post by Laiquendi on 2013-10-22
Could you please paste here the boot errors? They might be the problem.

There might be some driver incompatibility, something not loading fully, or something else, best if you provide more data.

---

### Post by coffeecat on 2013-10-22
**Three** threads merged. Please do not post duplicates - this dilutes community effort.

---

### Post by digimark on 2013-10-22
Well the boot errors (which are in dialogue boxes dont always show...so there must be some instability there....the only hard issue I have seen is that when I shut down Iget a diaglogue saying I am running in low graphics mode...I only see when when I shut down......

not much help i guess......

---

### Post by digimark on 2013-10-22
Apologies wasnt sure which forum to post on......wont happen again.

---

### Post by digimark on 2013-10-22
On further searching I fond this response

First, make sure you have the drivers needed, so open a terminal, and run this:

sudo apt-get purge fglrx*
sudo apt-get install fglrx
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo aticonfig --initial
Then reboot.


however not sure if it will do me any good as I have a chromebook not an ati radeon....

---

### Post by digimark on 2013-10-22
also tried

lshw -C video

this shows

 *-display               
       description: VGA compatible controller
       product: 2nd Generation Core Processor Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:42 memory:e0000000-e03fffff memory:d0000000-dfffffff ioport:1000(size=64)

---

### Post by digimark on 2013-10-22
HI All

Also tried this

The Intel graphics driver is part of the xserver-xorg-video-intel driver package, which is installed on all Ubuntu systems by default. And since it isn't a proprietary driver package, it doesn't show up in jockey (aka the Hardware Drivers application).

Just to ensure it didn't get removed by mistake (very slim possibility), just run this command:

sudo apt-get install xserver-xorg-video-intel

however the systems tells me I have the latest drivers installed....

any advice appreciated.

Thanks

/M

---

