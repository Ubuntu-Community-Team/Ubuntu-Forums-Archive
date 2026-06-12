---
title: "Ubuntu Still Won't Run"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by mikeMarek on 2008-05-08
I've been tryig to get Ubuntu to work using th regular installation and the alternate installation (both burnt on CDs after downloading from site). They install perfectly, but when I boot up Ubuntu, after the intro loading screen, I get this crazy display:

[IMG]http://img145.imageshack.us/img145/5618/dscn0703hp3.jpg[/IMG]

I'm not sure if I installed somethig wrong or something in my PC is conflicting, but when I test Ubuntu on my bro's PC it works fine.

Can anyone please help?
I deleted Windows off my PC to make way for Ubuntu, but won't work and now have no computer (BTW I'm posting this on my bro's PC :P)

Any help would be most appreciated! :)
-Mike

---

### Post by mano cazalet on 2008-05-08
hi mikeMarek

what are the hardware specifications of the pc?

are you installing 32 or 64 bits?

mano

ps.:did the live cd work on it?

---

### Post by Wolf_UK on 2008-05-08
No expert here, but have had similar troubles when the video cards not quite right.
Have you tried booting in recovery mode and asking for the X-server to be fixed?  I think this just drops your screen resolution so you can fiddle.

Wont call it safe mode though (Chuckles)

---

### Post by hotchkikr on 2008-05-08
try safe graphics mode, it usually works for me

---

### Post by mikeMarek on 2008-05-08
> **mano cazalet said:**
> hi mikeMarek

what are the hardware specifications of the pc?

are you installing 32 or 64 bits?

mano

ps.:did the live cd work on it?

Hey mano!

I believe my PCs a 64-bit, it's only a few years old.
The live CD is just the test of Linux, right? If so, no... It didn't work.

Thanks for the help,
-Mike

---

### Post by mikeMarek on 2008-05-08
Thanks for the tips! I'll reply with the results!

---

### Post by abn91c on 2008-05-08
> **mikeMarek said:**
> Hey mano!

I believe my PCs a 64-bit, it's only a few years old.
The live CD is just the test of Linux, right? If so, no... It didn't work.

Thanks for the help,
-Mike


there aren't many 64bit PC's that are "a few years old" if you used the 64bit on a 32 bit system you will have major issues. If you can get to a terminal try reconfiguring the xserver and use the vesa video driver.

---

### Post by abn91c on 2008-05-08
> **mikeMarek said:**
> Hey mano!

I believe my PCs a 64-bit, it's only a few years old.
The live CD is just the test of Linux, right? If so, no... It didn't work.

Thanks for the help,
-Mike


there aren't many 64bit PC's that are "a few years old" if you used the 64bit on a 32 bit system you will have major issues. If you can get to a terminal try reconfiguring the xserver and use the vesa video driver.

---

### Post by hotchkikr on 2008-05-08
i wouldn't say 64 bit - that screen looks like it got its horizontals and vertical refreshes wrong
but 64 bit would be a little worse...

If you did get the 64 bit cd, you really should try the 32 bit one, which usually always works, but when I can see "ubuntu" in that picture, it's just them darn graphics

---

### Post by Wolf_UK on 2008-05-08
By the way...I have a 64bit PC and installed the 64bit version but so many things wont run I decided it needs someone in a Linux T shirt at least to fix it all and installed the 32 bit version instead.

The live CD will do an install just as well as any but just gives you a chance to try 1st ;)

---

### Post by Raccoon1400 on 2008-05-08
What graphics driver are you using?

to check, boot the recovery option. Type
nano /etc/X11/xorg.conf (capital X)
Scroll to the graphics card section and check.

---

### Post by mikeMarek on 2008-05-09
Thanks for the tips, but it still won't work.
My computer wizard friend says that I need to re-install windows and partition my hard drive and dual-boot linux. He says that's the reason as my copy of Windows id something to my PC. I unno, but I'm going to try it anyway.

Also, I'm not 100% sure I have a 64-bit PC, so sorry if any confusion arose.

I'll also get the specs for my PC, so if anyone can help me with that info when I get it that'd be geat!

Thanks for helping and best regards,
-Mike

---

### Post by mikeMarek on 2008-05-09
Took my PC apart. I'm using a 128-bit ATI Raedon 9200 series graphics card. I also figured out a quick-fix to the problem... If I boot Linux in "Safe Graphics Mode", it works fine.

Thanks for the help,
-Mike

---

### Post by mano cazalet on 2008-05-09
Does this mean that you got it installed?

Hope so.

---

### Post by mikeMarek on 2008-05-11
Well, it's sort of installed. I got it to install on my PC, but some of the stuff won't run. Mainly the special effects and multiple desktops. I do belive that the problem is with my graphics card. So I'm re-installing Windows, updating my graphics card with a CD, then partitioning my hard drive for Linux, so if any more problems arise I can switch to Windows.

Thanks for everything you've all been extremely helpful, and best regards to everyone! ;) :)
-Mike

---

### Post by mano cazalet on 2008-05-11
noooo

updatin ur graphics driver in win won't help in ubuntu

try to post ur graphic cards specs here, maybe it is poosible to make it work without un and re and reinstalling OSs

---

### Post by free2useemail on 2008-05-12
It looks like to me that it is a graphic card. There is a chance that your graphic card is not capable with this, but it should not do that. Also, you need to make sure you are downloading and installing the right version of Ubuntu, like 64 bit or 32 bit, whatever your processer is capable of. If your processer has a 64 after it, like AMD 64, then you can run it, otherwise, you cannot. 
      ALSO! Make sure you have installed Ubuntu right. If you are burning an ISO, use a good program and BURN AT SLOWEST SPEED POSSIBLE!!! 

   Also, try using Wubi to install Linux, or order a free CD of Linux Ubuntu 8.04.

If this does not help, replay to this and I will try to help some more.

PS: We need more info about your PC hardware, if you are using windows XP, go to run, type in DXDIAG in the run command, and save all info, and copy and past the first part of the info you see in the notepad.

Hope this helps!

---

