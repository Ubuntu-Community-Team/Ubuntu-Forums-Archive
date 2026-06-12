---
title: "[SOLVED] Using Computer Temperature Monitor"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by hufferd on 2008-05-11
I installed the Computer Temperature monitor applet and it is tucked away running on the task bar....  

But now there are 4 different temp senors you can monitor with this thing 

Here is the kicker NONE of them AGREE with what my mother board bios says the temps are on any of its sensors.  there are only 2 senors that I know of on the mother board.  one for CPU and one for the case itself...   

The thing is none of the readings on this computer temp monitor are even close to what the bios is putting out...  is all but one sensor the temp  monitor says its below freezing!?!?!?!?!?!? :lolflag: Well reall thats not t


but close
LOL:lolflag:

anyone ever use this thing or have any ideas? 
~d

---

### Post by Ripfox on 2008-05-11
I prefer to install > hddtemp and then > sensors applet from synaptic...seems to work better for me. :)

Sensors Applet is an "add to panel" type applet.

---

### Post by autocrosser on 2008-05-11
You need to open Synaptic & install Lm-sensors & it's depends. Then goto the Tutorial forum & search for Lm-sensors--there is a very good How-To to install & setup your sensors.

---

### Post by hufferd on 2008-05-12
Ah thank you very much for the information I'm at work now but will check it out tonight when I get home 
Thanks to you both 


~dan :)

---

### Post by hufferd on 2008-05-13
ripfox....

I installed hddtemp and
sensor applet

But my sensor readings are all wacky 

What I mean to say is my CPU temp is no where near right by what my mother board is putting out 

ie mobo says CPU temp. is /was 80f (changed read out to (F) 
the sensor applet shows it at like 45f huh??? :confused:

also 

2. in the applet pref. 

under libsensors (I think) 
it show 4 sensors

core 0 
core 0
core 1
core 1

How in the heck do I know what is what there?? :confused:

none of the readings from any of those sensor outputs agree with what my mother board is say.  

My mother board has 5 readings in PC health 

CPU temp 
case or mother boad temp (not sure what this one says)
CPU fan speed
case fan speed1 
case fan speed2 

How do I know what libsensor matches with what output on the motherboard

In the applet pref. the only sensors that have the right output are:
1. hddtemp shows the right temp
2. GPU shows the right temp

This is all very confusing to me:( but I'm sticking with it 

:confused:

I will check all my info when I get home today I am writing  this  from work and trying to do it all from memory.

~D

---

### Post by hufferd on 2008-05-13
Or if anyone  has any ideas anyone can answer :)

---

### Post by Paqman on 2008-05-13
> **autocrosser said:**
> You need to open Synaptic & install Lm-sensors & it's depends. Then goto the Tutorial forum & search for Lm-sensors--there is a very good How-To to install & setup your sensors.

Installing sensors-applet takes care of all that.

---

### Post by BDNiner on 2008-05-13
yes use lm-sensors. it is more accurate i feel.

---

### Post by hufferd on 2008-05-13
Thank you all for your help I got things up and running as they should be :) 

Have a great day!
DH

---

