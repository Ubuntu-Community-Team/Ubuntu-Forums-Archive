---
title: "Fujitsu Stylistic ST 4120 Ubuntu?"
date: 2012-10-06
forum: New to Ubuntu
---

### Post by Anzem on 2012-10-06
Heya everyone, 

I got pissed off about my Windows XP tablet and I think I am finally ready to do a switch to Linux, any ideas, suggestions... ect would be greatly appreciated.

I have a Fujitsu Stylistic ST4120 specs are as follows:

Intel Pentium III-M 933.0 MHz

L2 cache - 512.0 KB

Intel 830MG Chipset

AGP - Intel Extreme Graphics - 48.0 MB
 
768 MB of PC 133 Ram

60 GB HDD

10.4 Inch Display
Max Resolution 1024 x 768
Touch Screen Digitizer (X,Y Coordinates... might be an issue)


I am currently thinking about Lubuntu 12.04 but that might change very quickly depending on the feedback I get.

What I would like to do that I am currently doing on XP is as follows:

Play Movies
Read Comics (With the side buttons working to flip pages)
Draw Stuff
Browse the web with flash support (XP does this poorly atm, I would like to see an improvement)
View/edit windows shares on my network.
TightVNC control my other PC's.
SNES Emulator Support
Dosbox Emulator Support
USB - Wifi, Mouse, Mass Storage, and Headphones.
Power Saving for on the go.

This will probably turn into a weekend project, so it should be a good time.

---

### Post by Bashing-om on 2012-10-06
Anzem; Hi ! Welcome to the forum.

As the only difference in ubuntu spin offs is the desk top and the supplied applications;

I suggest that you download the .iso of current interest, take it for a test drive in "try ubuntu" mode, see which you personally prefer. Install one of them and take it from there.

Using in "try ubuntu" mode also insures all your devices can/will work upon actual install.

Open Source => All things are possible --enjoy.

---

### Post by Anzem on 2012-10-06
Now I am having problems, I am using a burnt disk that I got of Lubuntu 12.04 it shows the menu but the only thing that I can get to is a Memory Test. I tried all of the other modes and it goes to a black screen, I have also tried burning a second disk and it does the same thing. 

I am going to try a different version and do some research... maybe my Tablet isn't good enough for 12.04.

---

### Post by DuckHook on 2012-10-07
> **Anzem said:**
>  ... maybe my Tablet isn't good enough for 12.04.

It seems that your problem might be with the graphics chipset, so post your video chipset specs and Google for them as well.

---

### Post by Mark Phelps on 2012-10-07
Good Luck with this ...

I had the Fujitsu T4020 - predecessor to your version.  Last Ubuntu version that worked well with was 8.10.  Then, in 9.04, they changed the Linux kernel so it no longer saw the buttons on the bezel -- basically ending my Linux use on it because I needed those features badly at the time.

So, the "side buttons" (if these are the ones on the bezel) most likely are not going to work.

Also, the processor is not very powerful.  For simple stuff like email and web browsing, it was OK.  But for more demanding stuff like videos, it lagged badly.  I even boosted it to the maximum of 2GB of memory, and while that worked better, it was still a poor performer.

The newer Ubuntu versions are designed for more power machines with more recent video chipsets -- so even if it does work, it's likely to have low resolution (1028x764 at best).

---

### Post by Bashing-om on 2012-10-07
The lubuntu version might run (or lighter still ?)...
Black screen: Try-> soon as bios screen clears, depress any key (12.04) yields the boot options menu. (ubuntu) f6 selects "nomodeset" f10 to continue booting.

If able to boot "nomodeset" maybe able to install better graphics driver after the install completes.

[INDENT]hth >==BDQ
 
[/INDENT]

---

### Post by Favux on 2012-10-07
I think the thing has the Intel i830m chipset.  So you want the Intel driver:  [http://www.x.org/archive/X11R7.6/doc/man/man4/intel.4.xhtml](http://www.x.org/archive/X11R7.6/doc/man/man4/intel.4.xhtml)

If you could get to a command line you could confirm that with:
```
lspci | grep VGA
```
Anyway something to google with.

If so you probably need the kernel boot parameter:
> i915.modeset=1
added to "quiet splash", i.e. "quiet splash i915.modeset=1"
At least that's what I think these are saying:
[http://www.murga-linux.com/puppy/viewtopic.php?t=63092&sid=584bc875bea124fa4b59dce3d50c4bd8](http://www.murga-linux.com/puppy/viewtopic.php?t=63092&sid=584bc875bea124fa4b59dce3d50c4bd8)
[http://forums.debian.net/viewtopic.php?f=17&t=81999](http://forums.debian.net/viewtopic.php?f=17&t=81999)

---

### Post by netipot on 2012-10-09
I have a motion computing le1600 tablet and found ubuntu very slow on it. I tried lubuntu & it was much faster, however bodhi linux, another ubuntu based distro using the enlightenment desktop runs very fast indeed. My external buttons don't work but I never really used them anyway. They still work in the boot set up & that is convenient.

---

