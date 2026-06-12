---
title: "Reinstalling Ubuntu on my system after a couple years without beiing on Ubuntu"
date: 2013-06-17
forum: Recurring Discussions
---

### Post by lemste on 2013-06-17
Hi everyone,

I reinstalled Ubuntu on a machine that already got an older version of ubuntu (I currently run on Ubuntu 13.04 while I was running on 08.04 in 2008). The machine didnt get any notable changes except than my DVD burner died (no link with the installation of Ubuntu - the burner simply died). My question is : is it possible than my system runs slower? I mean if i compare Ubuntu 08.04 and 13.04, 13.04 seems to be less responsive.

I run an AMD 1600mhz - it was an Athlon 3000+ i think - with 1.5G of RAM DDR2. My computer is, I know, an old boat. I use it mainly as a file backup system and to surf on web sites that does not need many plugins.

lemste

---

### Post by Iowan on 2013-06-17
I have a machine (with much lower specs than yours) that I finally had to start running Lubuntu. With the RAM maxed @512M, it struggles. Gutsy ran fine...

---

### Post by lykwydchykyn on 2013-06-18
There is no question that 13.04 will run slower on the same hardware than 8.04.  A lot happens in five years, and there is a completely new desktop environment running that uses a lot of resources (Unity) compared to the old one.

For that hardware, try Xubuntu, Lubuntu, or Bodhi Linux.

---

### Post by user_of_gnomes on 2013-06-18
You shouldn't try to run Ubuntu on hardware like that, it is far too heavy. Lubuntu is an excellent choice.

---

### Post by mastablasta on 2013-06-19
Kubutnu will also run nicely. Also you could try using gnome fallback mode and see if that speeds up the things a bit. also 12.04 has unity 2D which might help (looks same as 3D only uses less resoruces and no 3D acceleration).

speed of dekstop depends on grpahics card and it's support. for exmaple in 8.04 you might have had special drivers for it that are no longer available.

---

### Post by monkeybrain2012 on 2013-06-19
> **mastablasta said:**
> Kubutnu will also run nicely. Also you could try using gnome fallback mode and see if that speeds up the things a bit. also 12.04 has unity 2D which might help (looks same as 3D only uses less resoruces and no 3D acceleration).

speed of dekstop depends on grpahics card and it's support. for exmaple in 8.04 you might have had special drivers for it that are no longer available.


I find KDE to be the slowest and most resource demanding DE, by a large margin. If Unity is sluggish on that machine, forget about KDE. Lubuntu would run nicely though.

---

### Post by JustinR on 2013-06-19
> **monkeybrain2012 said:**
> I find KDE to be the slowest and most resource demanding DE, by a large margin. If Unity is sluggish on that machine, forget about KDE. Lubuntu would run nicely though.

    I run the latest KDE (4.10.4) on a Intel Atom 1.6GHZ (N270, single core) processor with compositing enabled, with demanding effects like Blur on an Intel Mobile 945GSE Express Integrated Graphics card with no slow down compared to other desktop environments, even with KDE's Nepomuk enabled. All of the KDE processes together use only 125MB of RAM.

---

### Post by mastablasta on 2013-06-20
> **JustinR said:**
> I run the latest KDE (4.10.4) on a Intel Atom 1.6GHZ (N270, single core) processor with compositing enabled, with demanding effects like Blur on an Intel Mobile 945GSE Express Integrated Graphics card with no slow down compared to other desktop environments, even with KDE's Nepomuk enabled. All of the KDE processes together use only 125MB of RAM.


indeed. while first versions of KDE 4 were bloated (afterall as i understand KDE got a complete rewrite) and nepomuk and akonadi can task the CPU too much (they can both be turned off), the latest versions of KDE are fast and lean compared to Unity. The ram consumption is also low. I have an older KDE and with plenty (not all effects) turned on it uses about 220MB ram. i switched off nepomuk and akonadi so the CPU usage is minimal. this one is running on some old celeron (dual core) with 1.3 GB DDR RAM.

i've also tried it on netbook (e-450, 2 GB ram) and it ran fast. way faster than win7 starter. so as soon as i get some money for external disk to do some backup and repartitioning, KDE will go to the netbook as well.

---

### Post by monkeybrain2012 on 2013-06-20
> **JustinR said:**
> I run the latest KDE (4.10.4) on a Intel Atom 1.6GHZ (N270, single core) processor with compositing enabled, with demanding effects like Blur on an Intel Mobile 945GSE Express Integrated Graphics card with no slow down compared to other desktop environments, even with KDE's Nepomuk enabled. All of the KDE processes together use only 125MB of RAM.

Well I am running the latest KDE too, though on Fedora in a dual boot with Ubuntu with Nvidia 319.23 on both systems. I can say Unity is a lot faster. I have also tested Kubuntu 12.10 on this machine and another two (one with Nvidia and the other with Amd), in both cases Unity is  faster and more responsive especially when playing videos or playing games (I don't play too many, and they are not serious games) I have disable syn to vbanks in both DES and disabled composting in fullscreen in KDE. Now I have not used Kubuntu with intel or the open source amd and Nvidia driver, maybe the closed drivers have some issues, I don't know. I run Ubuntu 12.04 with nouveau and it is very smooth and fast too,

---

### Post by craig10x on 2013-06-20
I have used both ubuntu with unity and kubuntu on my toshiba laptop with intel processor and graphics and i find that ubuntu with unity is faster and more responsive then kubuntu on my hardware...
It's a very recent toshiba (6 months old) with i3 core, 4 gb ram...

---

### Post by lykwydchykyn on 2013-06-20
Oh yay, another desktop-environment memory usage debate.  This is productive...

---

### Post by CharlesA on 2013-06-20
> **lykwydchykyn said:**
> Oh yay, another desktop-environment memory usage debate.  This is productive...

Aye... Half tempted to throw this thread in recurring discussions...

But on topic... Lubuntu ftw if you want to run a *buntu.

---

### Post by BR8 on 2013-07-09
I think this has been pretty well covered in this thread. Unity isn't good on that hardware. We recommend either L-, K-, or Xubuntu. You can do more research if you want to see how they look. I can't speak for the others, but XFCE has a panel similar to Mac's dock which you can place on any edge of the screen, or anywhere in the middle if you so please. You can even make multiple panels.

---

