---
title: "Ubuntu 8.04 Installation Black Screen"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by Crypterion on 2008-06-15
im a supernoob...

I think this has happened to a lot of people before, but right now it's really bugging me. When I boot from the CD and enter the installation menu, everything is still clear. But after I select the Install Ubuntu option and the orange bar is full, the whole screen turns black with my laptop still running. I can hear some strange african sound after the black screen appears for a while, but the screen wont show itself. I have the following:

1. a BenQ laptop with Intel duo core, 32-bit
2. a VIA Chrome9 HC IGP integrated graphics card

Is there anyway to fix this? I dont see anyway to install without the menu, and im not really familiar with the commands, i dont even know where to type them. Should i install with the alternate CD? help is really needed, thanx...

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-15
The first thing you should do is, at the startup of the CD menu, check the CD for faults. There should be an option for it. If it comes out O.K. then try booting the live cd itself.

P.S. That wierd African sound is the song for Ubuntu. I find it catchy ;)

---

### Post by Crypterion on 2008-06-15
the african song's one less thing to worry about...
but ive checked the CD many times, it found no error, could it have something to do with my video card? should i update my driver? at what part of the installation does the song play anyways?

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-15
Try booting from the live CD (wait until the time for the language runs out) and going through the manual installation. Otherwise it might be a problem with the hardware.

By the way, the song plays at logging in, so you can log in, I suppose.

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-15
> **Crypterion said:**
> im a supernoob...

That doesn't matter at all if you are enthusiastic about Ubuntu or any other Linux distro anyway. Everyone at some point WAS a noob at some time, even the moderators of the forums, I suspect (no offense guys, not saying you still are) ;)

---

### Post by Crypterion on 2008-06-15
thanx ill try that after i download the alternate version. if it's the hardware problem then what may be the cause of it? the video card (i think i might have stressed this too much)?

---

### Post by @_R_|\/|_@_G_E_|)_|)_0|\| on 2008-06-15
If you're using another lower distribution of Ubuntu than you COULD update. I wouldn't suggest it though. Many people have had problems with upgrading to 8.04

You could, however try going to the installation and hardware section of the forums and give it a shot there. There, people who are more experienced than me are browsing there, so you will get better answers.

Try everywhere before taking the alternate CD,
Armageddon

---

### Post by Joeb454 on 2008-06-15
You can boot the Live CD into safe graphics mode, have you tried that?

I think you press F4 at the boot menu, just after choosing your language :)

---

### Post by Pastortom on 2008-07-14
Ive got the exact same error when trying to install Ubuntu 8.04.. Really annoying..

I tried "Install Ubuntu" , "Install Ubuntu - safe graphic mode" and "Try Ubuntu without touching the hard drive/ Live mode".. Same stuff happens each time, I see the progress bar fill up and then blank screen, like the monitor isnt getting any feed, and the power button flashes just like if the computer was off.. 

Really annoying.. Help?!

---

### Post by ET! on 2008-07-14
even i have the same problem...iam using 8.04 and the installation went without an issue...but when i have to enter the password the screen goes black...but i can still enter the password and the system boots..and it takes a while for the desktop to appear

---

### Post by Pastortom on 2008-07-14
> **Crypterion said:**
> im a supernoob...

I think this has happened to a lot of people before, but right now it's really bugging me. When I boot from the CD and enter the installation menu, everything is still clear. But after I select the Install Ubuntu option and the orange bar is full, the whole screen turns black with my laptop still running. I can hear some strange african sound after the black screen appears for a while, but the screen wont show itself. I have the following:

1. a BenQ laptop with Intel duo core, 32-bit
2. a VIA Chrome9 HC IGP integrated graphics card

Is there anyway to fix this? I dont see anyway to install without the menu, and im not really familiar with the commands, i dont even know where to type them. Should i install with the alternate CD? help is really needed, thanx...




Mate, while trying to find a solution for the same problem on my own computer I found the same solution for your problem.

When you boot your computer with the Ubuntu install CD highlight "Install Ubuntu" and push F6 then hook off ALL additional options.. or at least "ACPI=off".. I had the 100% exact same issues as you with all kinds of Ubuntus trying to load GUI (after seeing the loading bar fill up and you see the screen flicker).. but when I added ACPI=off at the end it fixed my problem..

At the moment I also remove the tag "splash" and add the tag "vga=773" to make sure the video resolution isnt the problem during bootup..  if you're still having problems you might wanna try "Safe Graphic Mode" which is under F4 at Ubuntu bootup menu.. 

Good luck mate, and I hope this saves you 12 hours of hard work which Ive been through to accidently find this out..

---

### Post by Xardes on 2008-07-22
Hi!
I also had the same problem. I tried to boot from the Ubuntu CD and my screen turned black after starting the linux kernal. Until now i have not tried your solutions, but i could see the install menue when i connected my laptop with an external monitor.
In this case i also could activate the laptop screen with the hotkeys (you know? - in my case Fn + Crt/LCD). Unfortunately this would not work if i did not connect an external monitor.

so my advice: If you have this problem with your laptop and you have an external monitor, perhaps you can see the install menue after connecting this monitor.

I'm not sure if it can help you... in my case it works.
Good Luck! :)

---

### Post by brokenLockpick on 2008-07-22
I had some really nasty installation graphics issues, I needed to turn off my frame buffer (hit F6 and added fb=false to the beginning of the line) and then used safe graphics mode. So there is yet another option.

---

### Post by ben2talk on 2008-08-07
I had this trouble - a guy took his box to work, and I tried an 8.04.1 liveCD three times, and then he picked up an XP disk and it installed without losing the display.

Ubuntu still needs work on this!

XP 1, Bunty 0

Sorry guys, but in real life, people want their computer to work - they often don't want to have to try to find out what is wrong and fix it!

---

