---
title: "why i cant install ubuntu 8.04 ?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by tuts69 on 2008-07-12
hi any one can help me, i try to install the newest ubuntu 8.04LTS. in my system that has already running XP Pro. i want to dual boot my system. but every time i try to install the ubuntu first is ok but later on the installion has stop it freez, what was wrong. here's the spec of my rigs. Core 2 Quad q6600, i got 
2x (500 GB WD) in raid 0.i though i got a conflict on my raid 0 . so  i try to install the ubuntu in 250 GB drive but thesame problem the installation going to freez.? please help me.

---

### Post by ChameleonDave on 2008-07-12
How long did you give it after it seemed to freeze?

Did it totally freeze (stopping you even moving the mouse pointer)?

---

### Post by tuts69 on 2008-07-12
it keep me freez at point where they configure and installing the ubuntu  after the configure and installing the screen is blank blue and white but its not the BSOD.

---

### Post by LowSky on 2008-07-12
How are you tring to install it, wubi, LiveCD, alternate installer? Did you burn the CD at 4x. The Slower the Better

Sometime I find that you should defrag your hard drive and then create a seperate partion from windows before installing linux.

---

### Post by tuts69 on 2008-07-12
i try to install in liveCD and i burn the CD in 16x i going to try again, make another CD, thanks guys. appreciate.

---

### Post by tuts69 on 2008-07-12
thanks chameleondave & thanks lowsky i give it another shot again.

---

### Post by baistaef on 2008-07-12
The same problem was happining with me and i found out that it was a ram problem, one of my rams was broken so the whole system freezes when try to install.
When you boot from the cd do a memory check, it will take quite some time ( it took me 2 hours ) and see if there is any ram problems.

---

### Post by Pastortom on 2008-07-14
> **tuts69 said:**
> hi any one can help me, i try to install the newest ubuntu 8.04LTS. in my system that has already running XP Pro. i want to dual boot my system. but every time i try to install the ubuntu first is ok but later on the installion has stop it freez, what was wrong. here's the spec of my rigs. Core 2 Quad q6600, i got 
2x (500 GB WD) in raid 0.i though i got a conflict on my raid 0 . so  i try to install the ubuntu in 250 GB drive but thesame problem the installation going to freez.? please help me.

> **rockyroadnz said:**
> Hi, I am trying to install Ubuntu on an HP Pavilion 522a, so the neighbours kids can have a PC to surf the net and share music.
There install fails with no hints as to what is wrong. Can anyone help 

I downloaded ubuntu-8.04.1-desktop-i386.iso, burned a CD and booted  it OK.
Selected English language (the default)
Selected 'Install Ubuntu'
Watched the progress bar move up and down for a few minutes.
Screen then switched to blank then faint raster a few times.
Machine then froze with faint raster displayed.
At this point I can't alt/ctrl/delete to reboot and can't eject the CD.
Only way is to force power off.
I've tried this a few times with same result.

I have run 'Check CD' OK and 'Check Memory' OK. I don;t think there's anything wrong with the PC because it boots up Windows OK.
I'm starting to wonder if the HP Pavilion 522a is not good enough to run Ubuntu?

I'm lost - no idea what to do next and don't want to go back to Windows.
Any advice appreciated.
Keep in mind when offering advice that I am a total novice. Until recently I thought Unix were people that protected harems.
Thanks.

Mate, while trying to find a solution for the same problem on my own computer I found the same solution for your problem.

When you boot your computer with the Ubuntu install CD highlight "Install Ubuntu" and push F6 then hook off ALL additional options.. or at least "ACPI=off".. I had the 100% exact same issues as you with all kinds of Ubuntus trying to load GUI (after seeing the loading bar fill up and you see the screen flicker).. but when I added ACPI=off at the end it fixed my problem..

At the moment I also remove the tag "splash" and add the tag "vga=773" to make sure the video resolution isnt the problem during bootup..  if you're still having problems you might wanna try "Safe Graphic Mode" which is under F4 at Ubuntu bootup menu.. 

Good luck mate, and I hope this saves you 12 hours of hard work which Ive been through to accidently find this out..

---

### Post by johnswb on 2008-07-14
I was getting the same thing.  I had a USB device what was preventing the install to complete. The system would freeze during the install. Remove any webcam that you may have connected and try again. Hope this helps.

---

### Post by fancypiper on 2008-07-14
Make sure your CD is good as well.

I get better burns at the slowest speed possible.

---

### Post by Pastortom on 2008-07-14
> **tuts69 said:**
> hi any one can help me, i try to install the newest ubuntu 8.04LTS. in my system that has already running XP Pro. i want to dual boot my system. but every time i try to install the ubuntu first is ok but later on the installion has stop it freez, what was wrong. here's the spec of my rigs. Core 2 Quad q6600, i got 
2x (500 GB WD) in raid 0.i though i got a conflict on my raid 0 . so  i try to install the ubuntu in 250 GB drive but thesame problem the installation going to freez.? please help me.

Hey mate, I had the exact same problem, and been working on it for 12 hours until I accidently came over a solution.. 

at Ubuntu bootup menu (before installing) highlight "Install Ubuntu" and push F6 and choose "ACPI=off" then push F4 and choose "safe graphic mode" then it will work.. I tried installing ubuntu 6 times and messed around with all kinds of stufff.. until I accidently tried ACPI=off at the end of the kernel command line, that worked wonders.. but safe graphic mode and VGA=773 might also be of big help if you got graphic card problems.. 

VGA=773 then goes at the end of the kernel line (which shall be possible to easily edit before pushing enter in the Ubuntu install bootup menu (the first screen you see)..

Goodluck mate ;)

For more information on this Ive written an own thread about just this problem: [http://ubuntuforums.org/showthread.php?t=859692](http://ubuntuforums.org/showthread.php?t=859692)

Hope it works out for ya ;)

---

