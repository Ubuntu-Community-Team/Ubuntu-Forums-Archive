---
title: "NOOOOO! ubuntu crashed and now i can't even use my laptop"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by moose12 on 2008-11-05
ok, i recently installed hardy on my laptop and was instantly in love untill it crashed. The keyboard stopped responding, and the mouse didnt do anything either (even pressing caps lock didnt turn the caps lock light on) i noticed this when i pressed a button that turns off the mouse pad and buttons so i could type freely, the next time i hit this button nothing worked. i held the power button, wincing the whole time, and the computer shut down. but now it wont turn back on entirely. when i press the power button the laptop turns on but the screen does not (not like its getting a black picture but it looks like its still off  ??) every single button, aside from the power button, remains completely unresponsive. this is the second time this has happened, the first time i took it to staples where i know one of the employees is an experienced linux user, but he didnt tell me how to fix it.

---

### Post by lukjad on 2008-11-05
When you start up the laptop, can you get to the BIOS and do you see the BIOS information? I want to know because this could be a hardware problem.

---

### Post by moose12 on 2008-11-05
i cant get anything to come up.

---

### Post by lukjad on 2008-11-05
So when you press the power button, *nothing* happens? No beeps, no whiring sound, no fans?

---

### Post by moose12 on 2008-11-05
when i press the power button i hear fans thats it. i know. thats bad.

---

### Post by lukjad on 2008-11-05
So, not beeps  or the sound of the drives? (Just double checking.)

---

### Post by lukjad on 2008-11-05
Also, are there and USB or Firewire devices attached? If so, please remove them.

---

### Post by moose12 on 2008-11-05
Ya. Is there any thing I can even do with this now?

---

### Post by moose12 on 2008-11-05
no nothings attached

---

### Post by dje on 2008-11-05
try removing the battery and power adapter and leaving it for a few minutes then replace them and try again

---

### Post by lukjad on 2008-11-05
Have your tried plugging it in the wall instead of using the battery (if you can do that, that is)?

---

### Post by lukjad on 2008-11-05
> **dje said:**
> try removing the battery and power adapter and leaving it for a few minutes then replace them and try again
+1
Also, If that doesn't work, try leaving it out for the night (8 hours or so) and seeing if it helps.

---

### Post by Kinetic_lord on 2008-11-05
My guess is that this is a hardware problem that doesn't have to do with Ubuntu. I don't know how could the OS interfere with that.

---

### Post by Catalyst2Death on 2008-11-05
> **dje said:**
> try removing the battery and power adapter and leaving it for a few minutes then replace them and try again

Also holding down the power button for five seconds with the battery and AC power unplugged may work too.

---

### Post by vandorjw on 2008-11-05
Do you think it overheated?

1) If you turn on your laptop and it does not beep (POST), then either your computer (hardware) is fine, or your BIOS is gone.

"Leaving it apart overnight doesn't do anything if BIOS is gone. (But do it anyways..because if that fixes it, I am going to research why.)"


- When you plug your laptop into the wall, with the battery in it, does the battery charge? (What kind of laptop do you have?) On my dell, there is a side light that turns on when it is plugged in.

-While plugged in, hold down the power button for about 1-2 seconds.

---

### Post by moose12 on 2008-11-05
holy crap that did it. but why did it crash?

---

### Post by lukjad on 2008-11-05
Also, to add, it may just be time to visit a local technician. Out of curiosity, just how old is this laptop?

EDIT: Never mind. ;) Glad to hear it's fixed.

---

### Post by moose12 on 2008-11-05
brand new lappy

---

### Post by moose12 on 2008-11-05
so it seemed simply taking the battery out and putting it back in did it. and to the questions about how it responded before, it would charge no problem while plugged in. but what made it crash? I understand that keyboard and mouse functions are related to the xserver, and could that button to disable the touchpad and mouse buttons caused an xserver crash? the rest of the computer seemed like it was functioning(i watched the text line thing flash on and off in the text editor i had open). is there a way to prevent this happening again?

---

### Post by bwang on 2008-11-05
If the X server crashes, you can use the Magic SysRq hotkeys. Visit here: [http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/) 
for more information.

---

