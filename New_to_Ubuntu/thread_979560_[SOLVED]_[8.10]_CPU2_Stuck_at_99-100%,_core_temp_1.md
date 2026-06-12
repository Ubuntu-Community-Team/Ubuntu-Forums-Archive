---
title: "[SOLVED] [8.10] CPU2 Stuck at 99-100%, core temp 144C"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by earthpigg on 2008-11-12
ummm yeah.

i just restarted and it stopped that sillyness.

before i restarted, system monitor had itself going at 14% of CPU, and nothing else especially high... like 1 thing at 5%, couple 1-2%, and the rest 0%.

in general, my very fresh 8.10 install hasn't been doing so well in regards to 1) CPU and 2) core temp. (in many other ways, 8.10 has been a vast ~improvement~ so i'd rather stick with 8.10.


```
ep@ep-laptop:~$ acpi -V
     Battery 0: Full, 100%
  AC Adapter 0: off-line
     Thermal 0: critical, 144.0 degrees C
     Cooling 0: LCD 0 of 6
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 3
ep@ep-laptop:~$ 
```

any common cause, suggestions, etc?

edit: im here right now, and ill be keeping this thread open and refreshing every few minutes.

edit2: also, when my screen saver comes on, it tends to get audibly louder and run hot as well... as soon as i put my pword in, sys monitor tells me both CPU's had just been running at 100%.

---

### Post by Liviu-Theodor on 2008-11-12
What is doing the other CPU/core? After seeing this, reboot and see in BIOS what's in there at system temperature.

---

### Post by earthpigg on 2008-11-12
> **Liviu-Theodor said:**
> What is doing the other CPU/core? After seeing this, reboot and see in BIOS what's in there at system temperature.

i dont know wtf the other cpu is doing.

bios tells me 144 (if i just restart, it doesn't have time to physically cool down :) )

---

### Post by jespdj on 2008-11-12
I wonder if the reading of 144 degrees C is accurate. It's incredibly hot, much hotter dan a CPU is supposed to become. I would have expected the system to shut down automatically long before it would become this hot.

Is the CPU cooler in your computer working properly? Open the case and see if the CPU cooler fan is spinning as it should. Did you build this computer yourself? Is there thermal conducting paste between the processor and the cooler?

---

### Post by earthpigg on 2008-11-12
its a laptop...

it is hot enough that the ubuntu sticker i put on it has melted off.

i rest my hands over that part of the computer to warm them up (my room is cold).

but no, on the surface, it does not feel 44 degrees above the boiling point of water.

how can i check if it is accurate?

edit: restart made cpu2 stop running at 100% for no reason, and the fans sound like they have turned off... but that is little picture. big picture, im sure this problem continues.

---

### Post by Onesimus on 2008-11-12
What is the make of your machine ?

I had overheating problems with a DELL laptop, but it is possible to install additional software to control the fan.

---

### Post by earthpigg on 2008-11-12
ibuypower.com. ie: it was made by their random 3rd-party-of-the-month.

:\

8.04 worked fine, in regards to temp, on this machine. in fact im gonna boot into my 8.04 partition to see what 8.04 tells me my temp is....

---

### Post by earthpigg on 2008-11-12
ok 8.04 told me my core temp was 15 celcius. 

meaning 8.10 is not detecting the temperature properly.

output in 8.10 still reads:

> ep@ep-laptop:~$ acpi -V
     Battery 0: Full, 100%
  AC Adapter 0: off-line
     Thermal 0: critical, 144.0 degrees C
     Cooling 0: LCD 0 of 6
     Cooling 1: Processor 0 of 3
     Cooling 2: Processor 0 of 3
ep@ep-laptop:~$ 


any idea how i can make 8.10 learn2temperature? 

i didn't have to do anything special in 8.04.

---

### Post by earthpigg on 2008-11-12
```
ep@ep-laptop:~$ sudo apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  sensord read-edid i2c-tools
The following NEW packages will be installed:
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/126kB of archives.
After this operation, 578kB of additional disk space will be used.
Selecting previously deselected package lm-sensors.
(Reading database ... 119125 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a3.0.2-1ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Setting up lm-sensors (1:3.0.2-1ubuntu2) ...

ep@ep-laptop:~$ **man lm-sensors**
No manual entry for lm-sensors
ep@ep-laptop:~$ 

```

aaaaaaaaand that is about the end of my technical expertise.

---

### Post by 3rdalbum on 2008-11-12
The lm-sensors package installs a program that is just called "sensors". :-)

In future, if you look in Synaptic package manager, right-click on the package you installed, go to Properties and then Installed Files tab, you can see what programs and other files have been installed with the package. That's just a little tip for you.

---

### Post by blackened on 2008-11-12
I had a problem very similar to this yesterday. Core2 was stuck at 100% (didn't waste time taking temp readings). Took a quick look at htop and it showed that exaile.py was maxing out that core, so I quickly rebooted. The weird part was that exaile wasn't even running at the time, but must have had a process that didn't die when I shut it down last. I don't know how long it had been like that, but my fan was going full bore and my keyboard was feeling quite warm.

---

### Post by 3rdalbum on 2008-11-12
> **earthpigg said:**
> edit2: also, when my screen saver comes on, it tends to get audibly louder and run hot as well... as soon as i put my pword in, sys monitor tells me both CPU's had just been running at 100%.

It's probably unusual for both CPUs to be running at 100% during the screen saver, but if one was running at 100% that would be normal. Screensavers are like non-interactive 3D games - they suck as much processing power as they can get.

---

### Post by earthpigg on 2008-11-12
switching to a simple screen saver partially solved the problem - 'sensors' is now returning about 47 degrees... which is still significantly warmer than 8.04 ran.

any other ideas?

---

### Post by nhasian on 2008-11-12
i dont use a screen saver for precisely that reason.  i just have it blank the screen or shutoff the LCD.  Just FYI right now my cores are at 40C and 47C while idle on an Intel Core2 Duo T7700 2.40GHz.

When i do something processor intensive like converting an avi video to a DVD it jumps to 100C.  I get pretty nervous when i start to smell plastic melting but hey i got another year of warranty on this hp :lolflag:

---

### Post by blackened on 2008-11-12
I also bought the extended warranty, so I should be covered till June after next. At first I was apprehensive about spending the extra money on something I might never see a return on (and may well replace before said warranty runs out), but, given my propensity for spilling drinks (especially beer) on/into things, as well as my textbook case of butterfingers, I'm beginning to think this was the smart thing to do.

---

