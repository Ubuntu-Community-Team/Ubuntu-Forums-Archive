---
title: "Ubuntu 12.04 on 1.86GHz Pentium M 1GB ram"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by Gabcat on 2012-09-07
Dear all, 
I am trying to give new life to my old laptop. here are the specs.

ProcessorPentium M 750 / 1.86 GHz
Memory: 1.0 GB DDR2 533Mhz
Hard Drive- 5400.0 rpm (0GB
Graphics Processor: ATI Mobility Radeon X600 HyperMemory w/64MB VRAM.

Can it run Ubuntu 12.04 LTS smoothly? What if I upgrade to 2GB ram?
Or is it better that I install Xubuntu 12.04?

Thanks very much for your help. I imagine you must get bored of answering questions like this from all the beginners like me.

---

### Post by Epodx64 on 2012-09-07
Unity probably won't run well under those specs I suggest Xubuntu or Lubuntu

---

### Post by offgridguy on 2012-09-07
your computer should run ubuntu 12.04,  that is  what i have done to breathe life into an
older laptop.
An upgrade to 2gb ram is not a bad idea.
Are you already running an other operating system on this machine?

---

### Post by jerome1232 on 2012-09-07
Unity can be a little slugish on my Netbook which is a 1.6 Ghz Intel Atom with 1 gb of ram. It's usable, but a little sluggish. Gnome Classic with no effects is okay, Xubuntu runs good, Lubuntu runs suburb. I think the cpu is the limiting factor, particularly in my case as I have my users home encrypted.

I deal with the slight sluggishness of Unity, I like it and I don't want to spend time tweaking another DE to my liking.

---

### Post by pqwoerituytrueiwoq on 2012-09-07
> **jerome1232 said:**
> Unity can be a little slugish on my Netbook which is a 1.6 Ghz Intel Atom with 1 gb of ram. It's usable, but a little sluggish. Gnome Classic with no effects is okay, Xubuntu runs good, Lubuntu runs suburb. I think the cpu is the limiting factor, particularly in my case as I have my users home encrypted.

I deal with the slight sluggishness of Unity, I like it and I don't want to spend time tweaking another DE to my liking.
in the case of unity 3d it is the GPU

---

### Post by Gabcat on 2012-09-07
I am running Window SP pro service pack 3 on it. I would still keep some partition for XP as I have some software/hardware that I am not sure I can set up with linux (e.g. program to set up/manage my high speed internet with my provider here in switzerland)

---

### Post by jerome1232 on 2012-09-07
> **pqwoerituytrueiwoq said:**
> in the case of unity 3d it is the GPU

I just fired it up to take a look, it's actually much snappier than I realized, the trouble comes when I'm loading heavily scripted sites in firefox, the cpu peggs out at 100%. It's not doing any heavy swapping or anything, so that leads me to believe it's the cpu. Maybe I should try seamonky or some other lighter browser.

I'd say Unity was on par with Windows 7 starter edition, Ubuntu having faster startup and shutdown times.

At any rate, I think the op's computer can handle it.

---

### Post by plucky on 2012-09-07
My Pentiun M 1.5G will not run the 12.04 install as it doesn't support the PAE kernel.Try a Live CD or USB to see if it will handle the PAE kernel.

Xubuntu 12.04 doesn't use the PAE kernel.

Good Luck

---

### Post by mastablasta on 2012-09-07
> **Gabcat said:**
> 
Graphics Processor: ATI Mobility Radeon X600 HyperMemory w/64MB VRAM.
.

this ^^ could (or not) also be a problem. some mobility radeon are not supported as well as i windows, because AMD dropped support for these cards (remember that windows XP kernel is from 2001, while Ubuntu from 2011). and things run sliggish. best thing would be to use a liveCD or liveUSB and boot from it to see how well it works.

there are 2 unity interfaces one is 2D (3D is default and needs good hardware acceleration from GPU and drivers). another option is Gnome fallback. if it doens't work or works too slow there is also Xubuntu and Lubuntu (as menitoned these two also don't use PAE kernel=> CPU must support it). both of these two are descent desktops. Xubutnu is a bit more mature and IMO easier for newbies to setup.
 
also the programme you use for managing your high speed internet on windows is likely just bloatware. i could be wrong though...

---

### Post by HeroOfCanton on 2012-09-07
I've got twice the RAM/Processor in my laptop and Unity ran painfully slow and choppy. Switched to Xubuntu when Unity became the default and haven't looked back.

---

### Post by Gabcat on 2012-09-07
Thank you all.
I think I will install xubuntu. Unity and HUD seem interesting but I can live without them for now.

---

### Post by alex2399 on 2012-09-07
I have an older similarish PC. AMD 2500+ (1.8GHz) + 1 GB ram and a Radeon 9800 pro 128MB.

I tried a lot of desktops. Unity,Gnome 3 & Cinnamon (Linux Mint) will bring it to a halt. It is not snappy with XFCE and LXDE.

Reasonably well with MATE (Linux Mint) and surprisingly responsive with KDE 4.8.... without toning down too much on effects. KDE is on the machine now. It seems faster then any other Gnome 2/3 desktop since Ubuntu 10.10. This is coming from a former 100% Gnome2/3/Unity user a few days ago.


You may try installing via Ubuntu server and add desktop packages as you need. That may give some aditional speed enhancement but it can be tedious. So make sure you have some time.

---

### Post by Hadaka on 2012-09-07
works great on an old 2005 Dell Inspiron B130, the cheapest laptop dell ever made.
40 gig drive set up dual boot 20/20  Ubuntu 12.04 LTS and Ubuntu 11.10

[ATTACH]223845[/ATTACH]

---

