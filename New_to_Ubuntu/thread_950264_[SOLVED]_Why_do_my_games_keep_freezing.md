---
title: "[SOLVED] Why do my games keep freezing?"
date: 2008-10-17
forum: New to Ubuntu
---

### Post by CJ Master on 2008-10-17
*happily runs around shooting blob's brains out*

Aha! Team leader! This ought to score me 5 points! Ready, aim...

*freeze*

Nooooo not again. ;_;

Bottom line: Whenever I'm playing some games (that I got from Add/Remove Programs) it just randomly freezes, starts to go to the ubuntu desktop, then the whole system crashes and I have to do a hard shutdown.

I did a bit of trouble shooting and found it only happens in fullscreen games. Plus even if a windowed program froze I'd just have to use my nifty broken app forcer addon to take care of em...

Ah yes, I just remembered something, I have 64-bit ubuntu and os.

Please help, Forced restarts aren't fun. :)

Edit: Weird no ones replied yet, I guess i'm just spoiled by the people in my last threads replying within two minutes :P

---

### Post by Keen101 on 2008-10-17
do you also have compiz running?

Ctrl + Alt + Backspace usually can log you out without the need to restart.

---

### Post by CJ Master on 2008-10-17
Compiz? I doubt it, not even sure what that is.

Thanks for the logout tip!

---

### Post by CJ Master on 2008-10-17
Good news bad news time.

Good news: The logout tip worked.
Bad news: I had to use it. >.>

I guess it seems to think I want to switch windows. Any way to disable that while playing a game?

---

### Post by patrickballeux on 2008-10-17
For Compiz, open the menu "System - Preferences - Appearance"...

In the last tab, "Visual Effects", make sure that "None" is selected...  This will disable the Compiz effects and use a normal desktop without 3D acceleration...

What is your graphic card? ATI or NVidia? Other?

Also, make sure that you have installed libsdl1.2debian-pulseaudio (if you are using default settings or pulseaudio server).  There is a bug with 3d games and the ALSA driver using pulseaudio at the same time.

You can install it from Synaptic or in a terminal with this command:

sudo apt-get install libsdl1.2debian-pulseaudio

It will probably ask you if you want to remove another library libsdl1.2.  Answer YES...

Then reboot and try your 3d games again...

Let me know!

---

### Post by CJ Master on 2008-10-17
Ok I disabled effects - lets hope that works. 

ATI Radeon Xpress 200

---

### Post by patrickballeux on 2008-10-17
As I was editing, you replied...
Check for this...

Also, make sure that you have installed libsdl1.2debian-pulseaudio (if you are using default settings or pulseaudio server). There is a bug with 3d games and the ALSA driver using pulseaudio at the same time.

You can install it from Synaptic or in a terminal with this command:

sudo apt-get install libsdl1.2debian-pulseaudio

It will probably ask you if you want to remove another library libsdl1.2. Answer YES...

Then reboot and try your 3d games again...

---

### Post by patrickballeux on 2008-10-17
> **CJ Master said:**
> Ok I disabled effects - lets hope that works. 

ATI Radeon Xpress 200

Ok, it figures... An ATI card...  You have several options and several drivers for an ATI card.  Are you using the latest driver for your graphic card?  or the one by default?

If you install the EnvyNG package, it will setup up with the latest from AMD/ATI for Linux.  Look for Envy in Synaptic, after installtion, you will have an icon EnvyNG in your Application - Tools menu...

But I have a wild guess that your problem is related to pulseaudio... 

Let me know if the sound fix or compiz fix did something.

---

### Post by HittingSmoke on 2008-10-17
> **patrickballeux said:**
> Ok, it figures... An ATI card...  You have several options and several drivers for an ATI card.  Are you using the latest driver for your graphic card?  or the one by default?

If you install the EnvyNG package, it will setup up with the latest from AMD/ATI for Linux.  Look for Envy in Synaptic, after installtion, you will have an icon EnvyNG in your Application - Tools menu...

But I have a wild guess that your problem is related to pulseaudio... 

Let me know if the sound fix or compiz fix did something.

I'm no expert, but every graphics issue I've had so far in Ubuntu has been fixed by using EnvyNG to install my graphics drivers vs apt-get or Drivers Manager. Its definitely worth a shot.

---

### Post by CJ Master on 2008-10-17
Thanks very much, that seemed to have worked perfectly!!

---

