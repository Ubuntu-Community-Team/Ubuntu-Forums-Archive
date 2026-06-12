---
title: "ELECTRICSHEEP program (not working correctly) (max_analyze_duration reached)"
date: 2013-06-02
forum: New to Ubuntu
---

### Post by KELLOGGVOIDS on 2013-06-02
Electricsheep is a program that generates avi fractal images from multiple comptuers. You also have the option of downloading already rendered fractal avi videos, in packs. Here is a video to help you understand (don't watch it all..maybe a minute, or a some seconds):
[http://www.youtube.com/watch?v=jVD67pMdv9k](http://www.youtube.com/watch?v=jVD67pMdv9k)

I have posted on their forums as well. Here is the link to my post:
[http://electricsheep.org/node/5819](http://electricsheep.org/node/5819)

Hello. I have ubuntu 12.04. I did sudo apt-get install electricsheep,  which appearantly gave me an older version, according to this:
 [http://electricsheep.org/node/51](http://electricsheep.org/node/51)

  
 Whenever I ran electric sheep, though the terminal or though the xscreensaver, I would always see at the top left:
max_analyze_duration reached
 I'm assuming if I install it the perferred way, with the 2.9 widgits,  the problem will go away. Can someone please help me understand how to  do it?

 From the link I have in this post, I already completed number 1. Number 2 and number 3 say:
   
[LIST]
[*]install from source the latest [wxWidgets 2.9.x]("http://www.wxwidgets.org/downloads") (autogen.sh; ./configure; make ; sudo make install) and [flam3]("http://code.google.com/p/flam3/source/checkout") (./configure; make; sudo make install), and then:
[*]Checkout [client source]("http://code.google.com/p/electricsheep/source/checkout") and then ./autogen.sh; ./configure; make; sudo make install
[/LIST]
  I downloaded the 2.9.4 widgets, and I don't know what to do. The stuff in the parentheses, I don't understand it. Please help.

 Thanks for reading.

---

### Post by KELLOGGVOIDS on 2013-06-03
Anyone? I mean..I don't think its nessecary to have the program to understand the bullet points. I could be wrong.

---

### Post by squakie on 2013-06-03
Electric Sheep has come up in the past, and I don't think anyone contributed.  The post I remember was just for the screen saver that comes with it, but I (and I guess others) didn't want to test things out because of the peer-to-peer side of things in the project.

---

### Post by andrew.46 on 2013-06-04
I believe that electricsheep uses MPlayer to display the screensaver so there might be a few options here:

[LIST=1]
[*]Alter the Video settings for electricsheep
[*]Install [a newer copy of MPLayer]("http://ubuntuforums.org/showthread.php?t=2149564")
[/LIST]

I have attached a screenshot showing the video settings for electricsheep, a bit of trial and error with these settings might solve the issue...

---

