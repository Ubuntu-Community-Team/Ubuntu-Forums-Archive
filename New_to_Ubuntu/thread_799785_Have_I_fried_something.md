---
title: "Have I fried something?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by mister_pink on 2008-05-19
Hi all.

Got a bit of an issue. I popped out earlier and left my computer with the screen locked. When I got back the screen wouldn't come out of power saving mode and it didn't seem to want to respond to anything other than the magic sys rq key combos. So I rebooted and I now have all kinds of weird graphics corruption. The thing that worries me is that its not just ubuntu - see the screenshots. 

I tried reseating the graphics card (a radeon 9700pro) and booted up, and all was well. After a few minutes though artifacts started to appear on the screen and then it hung. Like the first time it won't restart X or switch to another tty, only sys rq. 

Any suggestions would be really great. Unfortunately I don't have any bits of old computer to do the old "swap thing around" diagnosis.

Cheers

---

### Post by bhold on 2008-05-19
I don't have a lot to offer other than to confirm I have had similar problems with screen lock since installing 8.04. However, unlike your situation, rebooting always cleared it up.

Currently - not wanting to backdate to a pre-8.04 Ubuntu - I am living with the following workaround.
1. Shut off timed screen saver / screen lock.
2. Lock the screen manually - this has never caused a problem, unlocks on demand every time.

---

### Post by tacutu on 2008-05-19
open the case of your PC and put it in a cool place. See if anything changes (i've seen it happen)
Edit: i mean put the PC in a cool place, not just the case :)

---

### Post by mister_pink on 2008-05-19
I did wonder if it was a heating thing so I cleared all the dust off when I reseated it. If it was though I think the damage is done since the time when it was ok for a few minutes the case was very cool as I still had the side off (cpu showed 35 centigrade, case 21 - yes apparently its summer now so my uni has turned the heating off and my room is freezing!)

A new and highly related question or two then.

1 Any suggestions for a replacement graphics card? I want cheap and similar spec (no point beefing it up too much, the rest of the computer is old anyway) and I'd like to avoid ATI like the plague
2 If I fit a new graphics card will ubuntu have a fit? Im using the restricted drivers, so I'm thinking fit new card, boot into recovery mode, uninstall that package and reboot? Do I need to do an xfix or something?

Thanks for your time

---

