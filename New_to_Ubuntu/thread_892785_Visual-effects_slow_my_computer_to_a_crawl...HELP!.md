---
title: "Visual-effects slow my computer to a crawl...HELP!!!"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by bronner on 2008-08-17
OK, I'm new to Ubuntu, new as in, I just installed it this morning.

I've played around with it before, and decided it would be cool on my computer.

My system specs are...

A1210N HP Pavilion, with a 500gb hard-drive, 4gb of RAM and an ATI-9250 graphics-card... 

Everything is working fine, except whenever I turn the settings under VISUAL EFFECTS to 'extra,' my computer slows to a crawl. I've spent all morning searching the boards for other users who might've experienced this but all of them are far more advanced users than I am. PLEASE, PLEASE, help. I want to use Ubuntu, but I keep getting scared back to windows... 

Can anybody help me?

---

### Post by overdrank on 2008-08-18
> **bronner said:**
> OK, I'm new to Ubuntu, new as in, I just installed it this morning.

I've played around with it before, and decided it would be cool on my computer.

My system specs are...

A1210N HP Pavilion, with a 500gb hard-drive, 4gb of RAM and an ATI-9250 graphics-card... 

Everything is working fine, except whenever I turn the settings under VISUAL EFFECTS to 'extra,' my computer slows to a crawl. I've spent all morning searching the boards for other users who might've experienced this but all of them are far more advanced users than I am. PLEASE, PLEASE, help. I want to use Ubuntu, but I keep getting scared back to windows... 

Can anybody help me?

Hi and welcome, you may look here 
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)
for ATI graphics older than the 9500

---

### Post by nicedude on 2008-08-18
If you are new and want an easy solution. I would say try Envyng as it is a program that does one thing, install the best Nvidia or ATI driver it can find for your card. It does this all automatically so you don't have to know what you are doing it will do it for you.

Here is the command to install it, which will install envyng and a gtk GUI ( graphic user interface ) frontend for it. Just paste this in a terminal window and hit enter ( For terminal topmenubar Applications -> Accessories -> Terminal )

sudo apt-get install envyng-gtk

Once it is installed click on the top menubar Applications -> System Tools -> Envy-ng and then select ATI and click for it to install your driver. When it asks if you would like it to configure your xorg.conf file for you say yes.

Hope this fixes your problem, make sure to let us know if it does and mark the thread as SOLVED

Welcome to Ubuntu :-)

---

### Post by nikgare on 2008-08-18
You have an old graphic card - it is too old for desktop effects!

---

### Post by subru77 on 2008-08-18
I have similar issues with compiz turned on. The effects are too slow. I have Nvidia 8600M GT 256MB video card.

---

### Post by bronner on 2008-08-19
How do you turn 'Compiz' off?

---

