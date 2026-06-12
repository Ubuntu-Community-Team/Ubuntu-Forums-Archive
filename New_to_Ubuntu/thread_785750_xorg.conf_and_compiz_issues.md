---
title: "xorg.conf and compiz issues"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by ntrgc89 on 2008-05-07
I recently re-installed ubuntu on my thinkpad T41, upgrading in the process (7.10->8.04) and I've been having trouble getting compiz to work. It was finicky in 7.10 but I was able to get it to work.

Now, in 8.04, the settings are confusing me. xorg.cong, under the device section, keeps listing 
Identifier     "Configured video device"
and nothing else. What does that mean? And I've tried changing it to say something like Driver "ati", BusID, etc., but it just reverts back to "Configured video device."

And through all that I can't get compiz to work. My video card is an ATI mobility radeon 7500 with 32mb VRAM, and any help would be greatly appreciated.

---

### Post by D3M0L1$H3® on 2008-05-07
i would also like to know, I could never get compiz to work in 7.10, when I tried to get it to work with a full install of compiz, it never loaded anything when i clicked "Compiz Preferences" and it disabled my ability to use the "Extra" desktop effects.

---

### Post by ntrgc89 on 2008-05-07
What video card do you have? It might not be able to support compiz.

---

### Post by ntrgc89 on 2008-05-07
OK, I finally got it to work. I simply started working under the assumptions that "Configured Video Device" in xorg.conf was not something to be messed with, and followed the instructions for setting it up on the compiz fusion website (it strikes me as silly that I never looked there before)

It still won't activate Xgl, whatever that is, but I simply type SKIP_CHECKS=yes in font of compiz in the terminal and it works. After that I can go into System --> Preferences --> Advanced Desktop Effects Settings and customize how I like. Hope some of that helped.

---

### Post by Rocket2DMn on 2008-05-07
For a more permanent workaround, have a look here - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

