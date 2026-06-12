---
title: "Sound stopped working...."
date: 2008-07-01
forum: New to Ubuntu
---

### Post by symbol86651 on 2008-07-01
Hi, I am really confused....
  I just rebooted and my sound does not work...
  I looked my hardware up it shows up...
  Also, when i use Amarok and play a song, a message appears and says 
   "Audio output unavailable; the device is busy.
xine parameters: "
  I've tried rebooting and it seems stuck....
                             Any help greatly appreciated

---

### Post by jingo811 on 2008-07-01
This little bugger might have been unclicked by a ghost :) happened to me once after 3 years of perfectly working sound on the same Ubuntu operating system.

You sure it's not some codec problems you're having when testing some new mp3 you've never tested before?

[IMG]http://i25.tinypic.com/2duatkn.png[/IMG]

---

### Post by symbol86651 on 2008-07-01
Well I tried opening ALSA mixer and it comes up in a blank window, also, when  I try to configure my sound card, it just exits....

---

### Post by symbol86651 on 2008-07-01
Also, sound works in XP so it cant be a hardware issue its gotta be with ubuntu.....

---

### Post by symbol86651 on 2008-07-01
I read a couple other forums and i learned to test my sound via prefrences > sound
  when i do that an error appears 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

this leads me to believe that Ubuntu could not find a suitable device to play sound.....
              Any help greatly appreciated

---

### Post by jingo811 on 2008-07-02
I'm no technical solution guy but I'm sure this thread might be of service to you :) he has written a pretty good from scratch sound troubleshooting guide.
[http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+tutorial](http://ubuntuforums.org/showthread.php?t=205449&highlight=sound+tutorial)

---

### Post by zakirs on 2008-07-02
whats your sound card any way ? ...  did u do any kernel update ?

---

### Post by symbol86651 on 2008-07-02
I was fully updated + had just gotten rid of Frets on Fire, rebooted and no sound....
   I am using whatever intergrated sound card comes with dell insperon 1520

---

### Post by jingo811 on 2008-07-02
Linux games are scary they can screw up your entire base system in the weirdest ways.  Especially FoF I liked that game in the beginning but when they did some updates to the game no Ubuntu version was happy after that.
I tested and fiddled with that game for 6 months on both Feisty and Gutsy.

In the end I had to flush the entire base system and re-install fresh to get rid of all the weird monitor problems.

---

### Post by symbol86651 on 2008-07-02
You know, one thing I have always been confused with ever since I switched to Ubuntu, I still wanted to have a backup operating system so I did a fresh install with XP sp2 on an extra hard drive and moved Ubuntu to an external hard drive, I had to look up all my drivers and install them and still many things still do not work without me fiddling with windows, ex. My laptop touchpad can not scroll up + down, sound is extremely loud, and when I install a dell recomended wireless application, it does not work....
  But, with Ubuntu, almost everything worked right after install which makes me wonder, why, with all the money pouring into microsoft, do these problems still happen????

---

### Post by symbol86651 on 2008-07-02
Well, after some time, I decided to look to my good friend Google and found someone else had the same issue as me and solved it by opening terminal and typing-

sudo apt-get install linux-backports-modules-generic

Then rebooting...


Thank you all who spent your time and effort for helping me and hopefully this will be the last of my Ubuntu problems..hopefully

---

### Post by jingo811 on 2008-07-02
Unless you have a contract with god then no this isn't the last problem you've seen with Ubuntu :)

---

### Post by symbol86651 on 2008-07-02
Does he take appointments?

---

