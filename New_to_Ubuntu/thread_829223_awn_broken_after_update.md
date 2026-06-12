---
title: "awn broken after update"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Knacker on 2008-06-14
hi, 
i just updated everything from update manager. updates included updates for AWN and AWN applets. after restarting, i can't get AWN to run. it flashes a little grey box in the top left of my screen and then nothing... 

what should i do? is there some way to undo changes from update without making a mess? is there any kind of known glitch that i could address to make this updated version of AWN work? 

anyone? please....
thanks in advance!

---

### Post by Knacker on 2008-06-14
well, i've discovered part of the problem. i can't enable visual/desktop effects. i'm so tired of ubuntu nvidia-driver problems. i finally fixed everything by installing 173.08 beta drivers (because ubuntu's proprietary drivers make a mess of everything)...which took me FOREVER and enjoyed about 5 days of a functional computer. i keep imagining that eventually ubuntu will just work, but it never does. so tired of nvidia driver problems. please please, i don't want to switch back to windows, but it never ever works for more than a week or so. please tell me there's an easy fix.

---

### Post by Knacker on 2008-06-14
how do i revert things back to the way they were before the update and stop ubuntu from updating (i.e. rendering my computer useless once a week) without making even more problems for myself? 

please...?

---

### Post by Knacker on 2008-06-14
is there something wrong with my post? am i not allowed to ask something that I'm asking? i'm sorry if i've missed something, i really don't know where else to ask about this.

---

### Post by overdrank on 2008-06-14
> **Knacker said:**
> is there something wrong with my post? am i not allowed to ask something that I'm asking? i'm sorry if i've missed something, i really don't know where else to ask about this.

HI and I am kinda at a loss. You have figured out the issue with AWN is the desktop effects correct? You installed the new nvidia drivers and the effects are working now?

---

### Post by Knacker on 2008-06-14
no, sorry if i've been unclear.. i installed the new driver from nvidia website a week or so ago to fix all kinds of other problems with ubuntu's proprietary nvidia driver...and things WERE working. i updated an hour ago and now I can't start effects and awn doesn't work.

does this make more sense? thank you so much for replying...i need help.

---

### Post by LeoSolaris on 2008-06-14
Which nVidia card do you have?

I am using an nVidia GForce 8400GS in a laptop, and jockey installs them just fine. Never had a problem till recently, but I think that may have been my fault.

(There is a reason it is a beta drive by the way, it will have issues)

Just so ya know, popping in every ten minutes or so to bump your thread doesn't help. If no one that knows anything is online at the moment, then no one will answer. Patience young padawan.

If it is stable, and working, just go to Administration->Software Sources, Updates tab, and uncheck everything but security updates. (Never wise to stop security updates)

Definitely take off the proposed updates and unsupported updates (although if you're using AWN's bzr version, the non-standard one, it will stop it from updating. I have to use the bzr version for 64-bit hardy) they are the most likely to break something.

Recommendation: Do not turn off security updates. Their for... well... security.

Leo

Edit: Just read the latest post you made before mine. You may need to re-install the nvidia driver after the recent update. I had too as well. It's a pain in the ****, but it happens. I hope you installed the driver with a package rather than from source, otherwise you may have a mess on your hands. 

I seem to remember seeing a refresh command or something like that for nvidia, that may solve the issue too. Let me do some poking around, see what I can find.

---

### Post by overdrank on 2008-06-14
> **Knacker said:**
> no, sorry if i've been unclear.. i installed the new driver from nvidia website a week or so ago to fix all kinds of other problems with ubuntu's proprietary nvidia driver...and things WERE working. i updated an hour ago and now I can't start effects and awn doesn't work.

does this make more sense? thank you so much for replying...i need help.

Ok you should be able to reinstall the nvidia drivers. Or Try and you screens and graphics to in sure you are using the correct driver.

---

### Post by LeoSolaris on 2008-06-14
I'll let ya handle it overdrank. You may want to show him envy. The issue with the proprietary nVidia drivers from Ubuntu may be a conflict with jockey rather than the drivers themselves. Envy may clear it up so he doesn't have to use the beta drivers, which are still a little buggy from what I have heard.

Leo

---

### Post by Knacker on 2008-06-14
ahhhh....a refresh video driver or anything to avoid the hell which is messing with nvidia drivers would be amazing. since hardy, packaged nvidia driver (proprietary) has been a disaster for me. 

installing from source (the beta) is my only option...this took me a week to figure this out with the help of other people with same problem. 

yes, reinstalling drivers is a HUGE pain in the a** for me. however many working backups of xorg.conf i have, however closely i follow the exact same routine, i end up with days of problems. 

didn't mean to bump thread...just distressed with yet another nvidia+ubuntu problem. 

will hope/look for nvidia refresh command and otherwise decide whether to go through another round of video driver, xorg.conf, etc. etc.... hell.

---

### Post by Knacker on 2008-06-14
envy "works" as well as ubuntu driver manager...they both install the same driver successfully, which doesn't allow me to get out of low-resolution mode. 

oh, video card: nvidia quadro 140m in a thinkpad t61.


...thank you so much for your help LeoSolaris!! very grateful for your time...you guys  are all seriously saints.

---

### Post by Knacker on 2008-06-14
fixed. reinstalled driver and, miracles and miracles(!!), no big configuration nightmare! Desktop effects enabled, AWN running. Thank you again and again. It's a huge help to just be told that what you are going to do (reinstall drivers) is not crazy. You guys are all amazing. Thank you!!:)

---

### Post by overdrank on 2008-06-14
> **Knacker said:**
> fixed. reinstalled driver and, miracles and miracles(!!), no big configuration nightmare! Desktop effects enabled, AWN running. Thank you again and again. It's a huge help to just be told that what you are going to do (reinstall drivers) is not crazy. You guys are all amazing. Thank you!!:)

Thanks and please mark the thread a solved under thread tools. Good luck!

---

