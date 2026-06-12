---
title: "3d Graphics Problems"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by RussW210 on 2008-10-09
Hello Everyone,

I have been having problems with 3d Graphics on my computer since I got it and installed Ubuntu 8.04 Hardy Heron.  For some reason, anything with 3d graphics will either glitch (flash a black screen), freeze, or lose its texture.  It is so far noticeable in:

SuperTuxKart Linux Game: The screen will flash constantly.  When I try to move the window the flashing image will stay in its old location on the desktop for a few seconds and then move.  When I put my mouse over the window the screen will turn completely black and the music will turn off.

Google Earth : same issue as SuperTuxKart.

3d Screen Savers: such as the screen saver where you move through the pipe.  For some reason it will flash black every second or two and when I came back to my computer after a few minutes the texture was completely gone.

... I currently am using a new Inspiron 530 with 3GB of RAM and a Quad-Core processor.  So my computer should have enough power to run a 3d game or any graphics.

I am also using Compiz Fusion and have the cube enabled.

My computer video card is an ATI Radeon HD 2400 and I am using the Accelerated Graphics Driver in the "Hardware Driver" section, fglrx.

I installed the Fusion Icon, as some have suggested, and switched to Metacity to see if the problem still occurs and it does.

My question, since nobody has been able to fix the problem, is: does anybody know the source of this problem?  If I know the source, I can do more research into fixing that area.

I have tried playing around with Xorg.conf but my limited knowledge of the file doesn't do much help.

I used to have a problem with 3d Accelerated Graphics on YouTube when the video's were on full screen.  The screen would glitch, similar to SuperTuxKart and the others.  But "Psyche3" came up with a fix for my mlb.com and xbox.com menu problems and that seems to have fixed my glitching problem there, but not on my 3d applications.

Would appreciate any help!!!

---

### Post by RussW210 on 2008-10-09
Anyone?

---

### Post by Bölvaður on 2008-10-09
I think I am obligated to say : please do not bump your thread the same day as you posted it.


But your problem kind of sounds like driver problem, like if it isn't tuned exactly for your graphical card.

Try download Warsow, choose to show fps and change max fps to 999. It will reveal how good your graphical card is performing and you will be able to guess how well it should be doing if it had proper drivers.

---

### Post by RussW210 on 2008-10-09
Thanks, will try that.  Also wasn't aware of the bumping guidelines lol

---

### Post by dburnett77 on 2008-10-09
I've heard of others, and myself, with similar issues.  I have luck disabling desktop effects.  I know that's no fun, but your other applications would probably run better.  I can't watch streaming video without a lot of interference if I don't disable advanced desktop effects.

If you want to try it, it's in the "Preferences..." menu.

---

### Post by RussW210 on 2008-10-09
Well, isn't that what the Fusion Icon does when I switch to Metacity?  Doesn't that disable the advanced desktop effects or does it keep the same settings?

---

### Post by dburnett77 on 2008-10-09
Typically, when the new driver is installed, desktop effects is enabled by default.

I have to reset mine via tick in the menus.

---

### Post by MungaMan on 2008-10-09
I am having the same problem.  What I did to solve it was creating 2 effects profiles.  One default, and one with everything turned off called Gaming.  After switching to the gaming profile, everything runs fine.


Alec

---

