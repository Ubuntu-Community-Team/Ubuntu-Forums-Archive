---
title: "Terrible Sound and Video problems F1A75 amd64"
date: 2012-01-22
forum: New to Ubuntu
---

### Post by TimTow on 2012-01-22
I have an AMD64 bit F1A75 V Pro motherboard and A8-3850 2.9G APU.  I installed 10.04 clean.  

Problem 1:  The audio quality is horrible.  Whenever sound plays over the speakers, or anything for that matter, the sound crackles unbelievably, and then oddly enough, the sound track of whatever I am trying to play (music, movie, etc) starts to play again, a couple seconds delayed, and overlapping.  So if I watched a movie and someone said in the movie "do you know where...", you would hear it like:

"do you know where..."
 ___"do you know where..."
     
so it would sound like same person is saying "you" and "do" simultaneously.  and "know" and "you" simultaneously, etc.  Does anyone  have a clue?  







I grew so frustrated that tried to switch to ubuntu 11.10, but when I try to put the .iso in and boot from CD drive, the screen goes blank with a message "invalid format".  However, I know this loads into the intial installation screens, that the computer just waiting for me to tell it what to do, I just can't see anything on the screen.  This makes me think that ubuntu doesn't work well with the on board graphics this motherboard has.  

Problem 2:  I am stuck with ubuntu 10.04.  Any other distribution .iso results in a blank screen.  Well If 10.04 worked I wouldn't care, but I cannot change my screen resolution.  Period.  It is stuck on 800x600 resolution.  If I try to click system > preference > monitors I get:

   "It appears that your graphics driver does not support the necessary 
   extensions to use this tool.  Do you want to use your graphics driver 
   vendor's tool instead?"

and ATI catalyst control center won't even start.  Under hardware drivers it says there are no drivers available.  I'm not sure why I need a driver considering I don't have an independent graphics card installed.  

I have a dual partition windows 7 sharing the hard drive.  Everything works awesome in windows, the sound, the video, ATI CCC.  So there has to be a way to get linux to work.  Even fedora .iso resulted in a blank screen once I got into the system.  If someone could help me sort this out that would be great.

---

### Post by Cheesemill on 2012-01-22
There are known issues with the drivers for the AMD Fusion APU's.


[http://ubuntuforums.org/showthread.php?t=1782165](http://ubuntuforums.org/showthread.php?t=1782165)

[http://ubuntuforums.org/showthread.php?t=1860361](http://ubuntuforums.org/showthread.php?t=1860361)

Maybe you could try this one to install the correct drivers:
[http://forum.xbmc.org/showthread.php?t=106898](http://forum.xbmc.org/showthread.php?t=106898)

Depending on how far things have progressed there may or may not still be problems, although I don't use AMD myself so I can't give you any first hand experience.

---

### Post by zeeboos on 2012-01-22
> **TimTow said:**
> I have an AMD64 bit F1A75 V Pro motherboard and A8-3850 2.9G APU.  I installed 10.04 clean.  

Problem 1:  The audio quality is horrible.  Whenever sound plays over the speakers, or anything for that matter, the sound crackles unbelievably, and then oddly enough, the sound track of whatever I am trying to play (music, movie, etc) starts to play again, a couple seconds delayed, and overlapping.  So if I watched a movie and someone said in the movie "do you know where...", you would hear it like:

"do you know where..."
 ___"do you know where..."
     
so it would sound like same person is saying "you" and "do" simultaneously.  and "know" and "you" simultaneously, etc.  Does anyone  have a clue?  







I grew so frustrated that tried to switch to ubuntu 11.10, but when I try to put the .iso in and boot from CD drive, the screen goes blank with a message "invalid format".  However, I know this loads into the intial installation screens, that the computer just waiting for me to tell it what to do, I just can't see anything on the screen.  This makes me think that ubuntu doesn't work well with the on board graphics this motherboard has.  

Problem 2:  I am stuck with ubuntu 10.04.  Any other distribution .iso results in a blank screen.  Well If 10.04 worked I wouldn't care, but I cannot change my screen resolution.  Period.  It is stuck on 800x600 resolution.  If I try to click system > preference > monitors I get:

   "It appears that your graphics driver does not support the necessary 
   extensions to use this tool.  Do you want to use your graphics driver 
   vendor's tool instead?"

and ATI catalyst control center won't even start.  Under hardware drivers it says there are no drivers available.  I'm not sure why I need a driver considering I don't have an independent graphics card installed.  

I have a dual partition windows 7 sharing the hard drive.  Everything works awesome in windows, the sound, the video, ATI CCC.  So there has to be a way to get linux to work.  Even fedora .iso resulted in a blank screen once I got into the system.  If someone could help me sort this out that would be great.

I am using a AMD E-350 Processor × 2  which uses the AMD APU and have no problems with video or sound.  If there are APU problems it must vary on the motherboard and other factors.  I am using Ubuntu 64 bit 11.10

---

