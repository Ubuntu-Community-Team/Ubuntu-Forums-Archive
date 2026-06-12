---
title: "Gateway All-in-One Profile 5"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by orwellus on 2008-09-26
This really isn't an ubuntu question, but there are a lot of smart people on these forums so I'll ask it here anyway. Recently, I bought a Gateway All-in-One Profile 5 computer off of ebay and I've been having some problems. The main issue is when I turn on the computer, I get a message on the monitor that says "POWER SAVE MODE" and then after three seconds the screen goes black, and nothing you do (moving the mouse, typing on the keyboard, hitting the side with your fist) will make it screen come back. Anyone know anything about this? I contacted gateway (via e-mail), but it takes forever for them to get back to me. I would like to put Ubuntu 7.10 (or maybe Mint Linux) on the computer if I can get the monitor working. There is no current operating system installed on the computer.

I think what might have happen is that the guy who owned the computer previous used a magnet or something on the harddrive to wipe the harddrive clean, but he might have also destroyed the BIOS. I would ask, but we are not on speaking terms at this point. 

Any help would be appreciated.

---

### Post by phidia on 2008-09-26
This may sound like a odd question but how many beeps, if you hear any, do you hear when you start up the computer? If the computer isn't passing the POST tests bios won't matter because it won't get to bios. 

There's a way to clear the bios. You usually have to find the little button and press that-you would need to know your motherboard type. 

Using a magnet on the hard drive (which is not reliable or even meaningful) won't affect your bios because the bios is on the motherboard.

---

### Post by orwellus on 2008-09-27
Thanks for the reply. To answer your question I don't hear any beeps when the computer starts. I'm not sure what type of motherboard the computer has. Maybe, Gateway Pentium 4 2.66 GHz?

---

### Post by phidia on 2008-09-27
You can do the search yourself for Power On Self Test beep codes or look at [this]("http://www.computerhope.com/beep.htm") webpage I found.

The first thing POST/Bios tests is the power suppy and depending on what BIOS you have you might get a series of beeps or none at all.

One beep BTW is what you should hear. The motherboard or power supply is not working correctly.

---

### Post by ready4thebreak on 2008-09-27
> **orwellus said:**
> Thanks for the reply. To answer your question I don't hear any beeps when the computer starts. I'm not sure what type of motherboard the computer has. Maybe, Gateway Pentium 4 2.66 GHz?

Wait are you using the Gateway ONE series computer(looks like a black and silver iMac knockoff), or the old all-in-one that they made?

---

### Post by orwellus on 2008-09-27
> **ready4thebreak said:**
> Wait are you using the Gateway ONE series computer(looks like a black and silver iMac knockoff), or the old all-in-one that they made?

I think it's one their Gateway Ones (yes I does look like a silver & black iMac knockoff).

---

### Post by ready4thebreak on 2008-09-27
Well those definitely don't have P4's in them it's a core 2 duo unless whoever sold this thing to you REALLY ripped you off.

---

### Post by orwellus on 2008-09-27
Well I'm going to make this thread as solved. I didn't actually fix the problem, I resold the computer on ebay at a reduced price for parts or repair purposes only. Very disappointing. Thank you to everyone who replied.

---

### Post by emperorwal on 2008-12-06
I have a Gateway Profile 5. It has worked great for a few years. Today my wife tipped it over to clean up the desk and it stopped working. It stopped with the exact symptoms you describe (Power up leads to "Power Save" mode on the screen and then repeating beeps, but no POST or Boot).

I googled for some ideas to fix the is and found this thread. You sold your machine, but I was able to fix mine. I just thought I would post the answer in case some other traveller finds this thread.

I don't know what caused the problem, but following advice from some forums I successfully reset the CMOS settings and then I was able to boot again. Simply remove the cover of the Profile 5 (which is easy once I found the manual online) and then I just removed the CMOS battery and waited about 30 minutes before putting everything back together. My Profile 5 is back to its old self (after reseting the clock).


Gateway Profile 5 manauls - good instructions on removing the back cover:
[http://nzr.mvnu.edu/facilities/items/profile5xmanual.pdf](http://nzr.mvnu.edu/facilities/items/profile5xmanual.pdf)

Wisdom about reseting the CMOS setting to fix odd problems
[http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/189075-computer-wont-power-up.html](http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/189075-computer-wont-power-up.html)

---

### Post by emperorwal on 2008-12-06
I have a Gateway Profile 5. It has worked great for a few years. Today my wife tipped it over to clean up the desk and it stopped working. It stopped with the exact symptoms you describe (Power up leads to "Power Save" mode on the screen and then repeating beeps, but no POST or Boot).

I googled for some ideas to fix the is and found this thread. You sold your machine, but I was able to fix mine. I just thought I would post the answer in case some other traveller finds this thread.

I don't know what caused the problem, but following advice from some forums I successfully reset the CMOS settings and then I was able to boot again. Simply remove the cover of the Profile 5 (which is easy once I found the manual online) and then I just removed the CMOS battery and waited about 30 minutes before putting everything back together. My Profile 5 is back to its old self (after reseting the clock).


Gateway Profile 5 manauls - good instructions on removing the back cover:
[http://nzr.mvnu.edu/facilities/items/profile5xmanual.pdf](http://nzr.mvnu.edu/facilities/items/profile5xmanual.pdf)

Wisdom about reseting the CMOS setting to fix odd problems
[http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/189075-computer-wont-power-up.html](http://www.techsupportforum.com/hardware-support/motherboards-bios-cpu/189075-computer-wont-power-up.html)

---

