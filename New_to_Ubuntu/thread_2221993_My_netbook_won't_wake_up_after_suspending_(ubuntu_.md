---
title: "My netbook won't wake up after suspending? (ubuntu 14.04)"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by maria5 on 2014-05-04
If my netbook suspends after inactivity, or I pull down the screen of the netbook without turning off the computer, the screen becomes black. But the problem is that I can't get the screen to come alive again. No matter which button I push or touch-pad mouse, the screen stays black.

The rest of the computer is NOT turned off, there are still lights flickering and the pc makes noise (I think it's the fan?), indicating that it's still active. It's just the screen that won't come back to live. Anyone knows how I can fix this?

Minor details: I have a Compaq-mini 700ED netbook, which first ran WinXP, then I tried Linux Mint 16 (because XP support was about to end) which was slower than my grandma, then I installed Ubuntu 14.04 beta2 (which should have updated into normal 14.04 by now, I think?) and that's mostly running smoothly except for this wake-from-suspension thing.

Other details: I know very little about computers. It's not my job or even my hobby to tinker with computers. I'm an end-consumer. So, please, don't expect me to know any complicated stuff, and explain things simply for me? Thank you! :)

---

### Post by maria5 on 2014-05-08
Uhm... anyone willing to help me?

---

### Post by newbie2244 on 2014-05-08
Try hitting the <enter> key. It works on my system which is an AMD64 HP POS, although slowly. 
Regards

---

### Post by su:bhatta on 2014-05-09
> **maria5 said:**
> 
Minor details: I have a Compaq-mini 700ED netbook, which first ran WinXP, then I tried Linux Mint 16 (because XP support was about to end) which was slower than my grandma, then I installed Ubuntu 14.04 beta2 (which should have updated into normal 14.04 by now, I think?) and that's mostly running smoothly except for this wake-from-suspension thing.

The Beta installation should be normal 14.04 if you have done all the software updates.

What is the Graphics card in your netbook? 
Did you install proprietory drivers for the same ?

---

### Post by maria5 on 2014-05-12
**@ newbie2244:** Hitting <enter> doesn't work. :-(

**@ su:bhatta:** I don't know what[COLOR=#000000] my Graphics card is... how do you find this out (and, actually, what are Graphic cards)? I don't know whether I installed proprietory drivers or not... (what are they anyway)? I just put the ISO image on an SD card, popped it into my netbook and followed the instructions, that's all.

(I think it's obvious from the above how little I know about computers, hahaha :-) also, English is not my first language, so please be clear and use simple words.)[/COLOR]

---

### Post by WoodenWalker on 2014-05-12
Your graphics card is the hardware that is responsible for your display on your computer. Proprietory drivers tend to be the closed source drivers made by the manufacturer of your graphics card (other other such hardware). And to find your graphics card, open the Terminal and run: lspci | grep "VGA"

That should bring up and entry like: 01:00.0 VGA compatible controller: NVIDIA Corporation GF119M [NVS 4200M] (That's what my card is)

---

### Post by maria5 on 2014-05-13
**@ WoodenWalkaer: **I ran that script and it says:

[I]00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)

[/I]
So, what now?

---

### Post by frostfire64 on 2014-05-13
Strange this graphic chip shouldn't have any problems with suspension (at least none that I heard of) did you have similar problems with suspension in Linux Mint 16?

---

### Post by wn1ytw on 2014-05-13
@maria5

I saw something recently where someone suggested hitting the device power button to wake from sleep. Not a long press, just a push/tap.. hope it helps.

---

### Post by maria5 on 2014-05-15
**@ frostfire64:** No, I don't think I had that problem with Mint, though I didn't like Mint because it was really slow on my netbook (I even used the lightweight Xfce version).

**@ wn1ytw:** Hmm... that didn't work. My netbook's power button isn't a press button. You have to pull it very firmly to the left. Here's a picture of the model:

[IMG]http://ic.tweakimg.net/ext/i/1232625881.jpeg[/IMG]

---

### Post by maria5 on 2014-05-21
So... no one knows the answer to this problem?

---

### Post by SwissArmyKnife on 2014-05-21
My Samsung NC10 does the exact same, pressing the power button quickly resumes almost instantly so I consider it a non issue for me, sorry your button is harder to press.

---

### Post by Ripp_Steakface on 2014-05-21
I have this exact same issue on an Asus EeePC 900HA with the Intel 945GSE integrated graphics, running Xubuntu 14.04. It's gotta have something to do with the graphics drivers. I haven't installed anything except the OS, no prop. drivers or anything. I'd love to see a solution because it's really the only problem I have with the computer now that I have Linux on it.

---

### Post by JeQhdMD on 2014-05-21
Well Maria - - one thing you can do is to shut off "suspend" - - by going into the ubuntu "System Settings" (click on the icon with the gear & wrench).  You should see a "power" icon (a battery) in the Hardware row.   Click on the Power icon and there are 4 selections you can change to read "Don't suspend" or "Do nothing" (when lid is closed).   This will affect the amount of battery time when not plugged in, but it's a trade-off and should solve the problem until a better fix is communicated.

---

### Post by maria5 on 2014-05-25
**@ JeQhdMD: **Thanks, I did as you suggested. It's not the solutions I was looking for, but it will have to do until Canonical comes with a proper fix.

I heard many others experienced this problem, across different versions (14.04 and older) and flavors (ubuntu, xubuntu, etc.), but still no proper solution; so I really hope Canonical takes this seriously and does something about it, especially if they want to compete against bigger players in the field (Windows, Apple, etc.). A computer that cannot suspend is rather... well, amateurish.

---

### Post by etimer on 2014-06-26
Having the same problem on an old HP Pavillion zv 5000.

The problem is a recent problem and appeared after one of the recent updates.  I've had no problems before the updates.

I've turned off suspend / turned on energy screen saver / turned on screen saver (activates in 1 minute).  So far the previous set-up has not froze.  The screen goes into screen saver mode but turns back on when hitting the space key.  I haven't tried using the mouse to wake it up.  Before there was nothing that would bring the screen back on --- not the mouse, space bar, no ctrl+F keys, nothing worked except a hard restart.

I know that an update changed something because my effects off key was changed and would turn the screen off.  The same things was happening on my Acer.  I had to change the key combo to shft+F12.  When the same thing was changed on two different computers I say it was caused by an update.

 > **maria5 said:**
> **@ JeQhdMD: **Thanks, I did as you suggested. It's not the solutions I was looking for, but it will have to do until Canonical comes with a proper fix.

I heard many others experienced this problem, across different versions (14.04 and older) and flavors (ubuntu, xubuntu, etc.), but still no proper solution; so I really hope Canonical takes this seriously and does something about it, especially if they want to compete against bigger players in the field (Windows, Apple, etc.). A computer that cannot suspend is rather... well, amateurish.

---

