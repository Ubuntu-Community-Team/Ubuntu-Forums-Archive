---
title: "Laptop issues (power profiles?)"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Pas_sa on 2008-05-12
Hi,

I'm trying to set up Ubuntu on my laptop (already got it on my desktop) but I have a few issues. On Windows, I can choose how fast I want the CPU/GPU to run while on battery power. This means I can tell it to run at full speed (reducing battery life to 1h 30min) so I can play games or do intensive processing while on battery. Is there a way to control this on Ubuntu as well?

Also, I am wondering if battery life will be longer or shorter with Ubuntu (compared to XP).. this is somewhat important to me.

By the way, specs:
IBM ThinkPad R50
Pentium M 1.4GHz
768MB RAM (upgraded)
Radeon Mobility 7500
25GB HDD
DVD Reader/CD Writer combo

Hopefully someone has the same laptop and can give me more pointers about it.. I'm assuming there is no 3D support for the graphics card? What about proper video playback (for DivX/Xvid, DVDs..)?

Thanks :)

---

### Post by Canis familiaris on 2008-05-12
Right Click on any empty space in the panel and click Add to Panel and add "CPU Frequency Scaling". This will put an applet in the panel which shows the current speed of CPU. You will notice that the CPU is throttled down when not doing intensive work and the clock speed changes by demand.
To configure it so that you could choose the speed, zoom to the terminal and type:
```
sudo dpkg-reconfigure gnome-applets
```
It will show a text mode wizard. Using keyboard choose OK and when it asks:
> Install cpufreq-selector with SUID root?
Choose Yes And Go.
Now you can choose the speed of CPU using CPU Frequency Scaling applet.

---

### Post by Canis familiaris on 2008-05-12
To install the codecs and other proprietary items install Ubuntu Restricted Extras Package.
Go to Add/Remove, search for "restricted" and install Ubuntu Restricted Extras Package.
It will install most codecs, java and flash, etc.
Also install VLC Media Player in Add/Remove by searching vlc which will play most media files.

---

### Post by Canis familiaris on 2008-05-12
> **Pas_sa said:**
> Hi,

Also, I am wondering if battery life will be longer or shorter with Ubuntu (compared to XP).. this is somewhat important to me.



This is a tough call to make but due to the fact that XP is bundled with your notebook it will have a slight edge.

---

### Post by Canis familiaris on 2008-05-12
Well there is 3D support in Linux. But you have an ATI graphics card and it may give problem.
You may find your answer in this thread:
[http://ubuntuforums.org/showthread.php?t=515573](http://ubuntuforums.org/showthread.php?t=515573)

---

### Post by HotShotDJ on 2008-05-12
> **Anurag_panda said:**
> To configure it so that you could choose the speed, zoom to the terminal and type:
```
sudo dpkg-reconfigure gnome-applets
```

Brilliant!  Worked a treat for me (and it wasn't even my question!)

---

### Post by ubunu on 2008-05-12
"on any empty space in the panel"

and a newbie says what/where is the panel?

---

### Post by Canis familiaris on 2008-05-12
> **ubunu said:**
> "on any empty space in the panel"

and a newbie says what/where is the panel?

Well if newbie asked that I would have told him, the "start menu" taskbar equivalent which is used to launch applications. But then he may have asked: "What's start menu?"

---

### Post by sdennie on 2008-05-12
Power savings under linux is excellent but, unfortunately, at the moment, there is no magic button to press to enable it fully.  Checking out [www.lesswatts.org](www.lesswatts.org) and installing powertop ("sudo apt-get install powertop" from the command line) will get you pointed in the right direction.

---

### Post by Canis familiaris on 2008-05-12
> **vor said:**
> Power savings under linux is excellent but, unfortunately, at the moment, there is no magic button to press to enable it fully.  Checking out [www.lesswatts.org](www.lesswatts.org) and installing powertop ("sudo apt-get install powertop" from the command line) will get you pointed in the right direction.

Does PowerTOP work for AMD Turion?

---

### Post by sdennie on 2008-05-12
I would imagine it would work in some capacity with that chip (might not have the processor states) but, I don't have a way to check that.  It's easy enough to try it out though.

---

### Post by ubunu on 2008-05-12
> **Anurag_panda said:**
> Well if newbie asked that I would have told him, the "start menu" taskbar equivalent which is used to launch applications. But then he may have asked: "What's start menu?"

ah...panel=taskbar

"But then he may have asked: "What's start menu?"

No he wouldn't he would have said thank you very much for your gracious help

:)

---

### Post by Canis familiaris on 2008-05-12
> **ubunu said:**
> ah...panel=taskbar

"But then he may have asked: "What's start menu?"

No he wouldn't he would have said thank you very much for your gracious help

:)

But if he has never used Windows before, then???

---

### Post by notanatheist on 2008-06-15
Let's do some thread digging here since this has the most relevant subject when searching. 

For laptop power management there needs to be an option to set a "power profile" telling the system how bright you want the screen and what default speed the CPU should be for a given profile. For Acer laptops running that other OS there is a little battery icon where you can select a power profile and even create your own. You have options to turn off LAN, WLAN, Card Slot, and Firewire as well. I'd settle for at least screen and CPU though and use my switches for other hardware devices. 

As it is, even with the "dim laptop screen" option selected in power management it still runs at least 60 to 80% of brightness. That's quite a power drain and overly bright in certain situations. Even if you manually set it lower then allow the laptop to idle where it reduces the brightness further once you engage the laptop again through touchpad or keyboard it goes back to where it was originally and not where you had set it. 

Just some thoughts as to what could help increase further adoption. Maybe if the manufacturer stepped up with a utility for their laptops that could increase brand appeal for buyers.

---

### Post by Matt Brooks on 2010-06-27
> **notanatheist said:**
> Let's do some thread digging here since this has the most relevant subject when searching. 

For laptop power management there needs to be an option to set a "power profile" telling the system how bright you want the screen and what default speed the CPU should be for a given profile. For Acer laptops running that other OS there is a little battery icon where you can select a power profile and even create your own. You have options to turn off LAN, WLAN, Card Slot, and Firewire as well. I'd settle for at least screen and CPU though and use my switches for other hardware devices. 

As it is, even with the "dim laptop screen" option selected in power management it still runs at least 60 to 80% of brightness. That's quite a power drain and overly bright in certain situations. Even if you manually set it lower then allow the laptop to idle where it reduces the brightness further once you engage the laptop again through touchpad or keyboard it goes back to where it was originally and not where you had set it. 

Just some thoughts as to what could help increase further adoption. Maybe if the manufacturer stepped up with a utility for their laptops that could increase brand appeal for buyers.

amen. i agree with the need for customizable  power profiles for battery power or AC power. i was told somewhere that laptop-mode-tools and pm-utils-powersave-policies allow this but i havent found a way to configure it

---

