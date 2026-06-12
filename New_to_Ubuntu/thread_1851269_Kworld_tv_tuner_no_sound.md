---
title: "Kworld tv tuner no sound"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by mars-o on 2011-09-27
Hi,

i have  a kworld pci analog tv tuner (PVR-TV 7134SE).

in ubuntu 11.4, i could watch tv on TvTime, Xawtv, but there is no sound. idk why.
i could play music in banshee, and play movies. but with the tv- no sound.

pls help. what did i miss? or what ubuntu program should i use for my tv tuner?

also, i don't know why i could not have mythtv to work. 
( i have installed mythtv frontend&backend).

thanks.

P.S.
i disconnect my webcam, as suggested online.
is there a way too that both webcam & tv tuner can work, w/o the need to unplug the other?

---

### Post by madvinegar on 2012-01-17
I am having exactly the same problems.

I am looking forward to hearing a solution to the above.

Just for the record, you can experiment with TVtime, and you may be more lucky than I am.

Go to the folder /etc/tvtime/tvtime.xml and scroll down till you find the sentence <option name="MixerDevice" value="default/Line"/>

Change same to <option name="MixerDevice" value="hw:0/Line"/> or <option name="MixerDevice" value="hw:0/CD"/> or <option name="MixerDevice" value="default/Master"/>

and see if this has any result.

---

### Post by madvinegar on 2012-01-18
I did it !!!!! YEEEEEEAAAAHHHHHHH !!!!!            

I did it with Kaffeine !!!!! Which is better because it receives digital channels!!!

I had to change the scan options to:

tuner timeout ms: 5000
source: autoscan with 167khz offsets

All the proper channels were found, and they work GREAT. Picture is great, sound is great!!!!

Try it!

---

