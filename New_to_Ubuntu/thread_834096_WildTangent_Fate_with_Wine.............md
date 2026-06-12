---
title: "WildTangent Fate with Wine............"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by daniel7860 on 2008-06-19
I downloaded the Fate installer from wild tangent and it opens in Windows Wine Emulator but it just shows the WT logo and the cancel button, and i cant even press it. I do have all the windows fonts installed.
Can anyone help me install the game???   (does it even work with wine?)

I am using Ubuntu 8.04 and my graphics Card is: ATI Mobility Radeon X300

---

### Post by mikeyphi on 2008-06-19
> **daniel7860 said:**
> I downloaded the Fate installer from wild tangent and it opens in Windows Wine Emulator but it just shows the WT logo and the cancel button, and i cant even press it. I do have all the windows fonts installed.
Can anyone help me install the game???   (does it even work with wine?)

I am using Ubuntu 8.04 and my graphics Card is: ATI Mobility Radeon X300

Try running the program from a terminal - that'll give you access to error messages and provide a clue to the problem. Sometimes it's just a question of a missing .dll.......remember not all programs work under Wine.
Also remember to run wine config  - 'add' the new program and set options...try different settings for the MS emulation.

---

### Post by vanquishedangel on 2010-11-09
Hi, a little late but I got this to work though PlayonLinux, and by pulling out my hair.

Get PlayonLinux, and when it is updated and set up, open it and  click install, then Internet, and install Internet explorer6. 

After Internet explorer 6 is done installing click install, look to the bottom where it says install an unsupported package or a .pol, click it, then click manual install, click forward, select edit an existing application, choose Internet explorer 6, click forward, and then browse to installer file for Fate and select it.

This install works on Ubuntu 10.04 lts, with wine 1.3.6 and PlayonLinux 3.8.6. You need the installer from their website and a "patched"(cracked) fate.exe file that i cant tell you where to get it but just search it out. One issue so far is that in your inventory you can't see the items, they are blurred but if you mouse over them it tells you what they are. I am sure this is a setting, or dll or something easy fixable, I just haven't found it, it seems all else works though and you can see the items on you.

---

