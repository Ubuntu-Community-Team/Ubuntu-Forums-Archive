---
title: "HOW-TO Overclock ATI cards...ROVCLOCK"
date: 2005-10-10
forum: Outdated Tutorials &amp; Tips
---

### Post by floyd27 on 2005-10-10
1- Download rovclock..
[http://freshmeat.net/projects/rovclock/](http://freshmeat.net/projects/rovclock/)

2- Extract to desktop
3- cd /home/yourname/Desktop/rovclock-0.6b
4- make
5- sudo ./rovclock-0.6b -i                  ( For Breezy sudo ./rovclock -i )

This will give you the syntax and your current clock speeds.

OVERCLOCKING..

6- sudo ./rovclock-0.6b -c (new mhz) -m (new mhz) 
These are for core and mem respectively.

You can then do step 5 again to see if your changes took..
As for saving after a boot im not sure how to yet..You may not want to as, if you clock too far you may not be able to get the speed back down if you have artifacts and cant see the screen...

Its up to you to make sure its stable, as there is no "find max core/mem" or scanning for artifacts as in ATITool.....

Overclocking can kill your card/system so be careful....!!!!!!!
Im not responsible for any harm that may come to your system...

---

### Post by rimmer on 2005-10-11
floyd27 
Thanks for the how to, it workes a treat so far, i've not tryed clocking yet as I want to know what all the output from "rovclock -i" is first. But as soon as I do I'll let you know.

Nice one !!

What do you think a safe percentage increase would be?

---

### Post by floyd27 on 2005-10-11
Thanx rimmer..
I would stay away from the memory timings though... 
I have never changed them from stock, with any prog. 
I hear you can really mess things up with them.
But as for mhz.. Go ahead and start upping them. Slow at first to see how far you can get..
Id actually go the google and see what others were able to get out of the same card to get a good starting point..

I would say 10%-15% is where you should shoot for....(depending on cooling)
My 9700 pro was... 325 core/310 mem
overclocked is........ 370 core/330 mem 

 I did know this was stable though as I used atitool in windows to find my max stable overclock..And I have a thermaltake dual heat pipe cooler as well..

---

### Post by GameManK on 2005-10-11
wow! nice! thanks

you could probably put the command to overclock in one of the startup scripts to get it to do it on every boot (don't know what file myself though. maybe in /home/user/.kde/Autostart/whatever.sh? (for kde) or would it be more appropriate in something that loads before kde?)

---

### Post by souled on 2005-10-11
Ok, I have a problem. I'm not sure if it's because of overclocking or not, but it started after I did this HOWTO. I have a Radeon 9200 graphics card. I overclocked from 249 mhz (core) 200 mhz (mem) to 275 mhz 225 mem. Everything seemed fine. Didn't notice anything wrong. After about an hour, I restarted my computer. And I don't see anything graphical. I can see the BIOS stuff, but when I start X, my monitor is blank and the led goes to orange (indicating no signal being recieved). I can however switch terminals, and I can see everything. It seems like everything is running fine, just the video is screwed. When I try to boot in Windows, I get as far as the boot logo then the screen turns off when it gets to the login screen (which I don't see). 

So... Is my video card fried?

Edit: Everything is well now. As instructed by floyd27, I reset my cmos and now everything is back to normal. I guess I went a little overboard on the overclocking :). Thanks again floyd.

---

### Post by floyd27 on 2005-10-11
I sent you a PM.

---

