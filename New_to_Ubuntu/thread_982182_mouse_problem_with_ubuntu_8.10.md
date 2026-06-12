---
title: "mouse problem with ubuntu 8.10"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by cliff_bisch on 2008-11-14
I am some what new to Ubuntu trying to figure out every thing on my own, but could not find any help with problem. 
My optical mouse is on and moves but keeps automatically moving back to center of screen before i can click anything. 
I had 8.04 and it worked fine but recently partitioned hard drive to install 8.10  mouse works fine on xp, if any one can help please provide keyboard short cuts to any thing i would need to get to 
thank you.

---

### Post by jpoRS on 2008-11-14
What are you running on? Laptop? Desktop? Digital Abacus?

If it is a laptop maybe your touch pad is interfering?

jim

---

### Post by cliff_bisch on 2008-11-14
No sir, i am running it on a desk top and only have one mouse connected

---

### Post by reggler on 2008-11-14
> **cliff_bisch said:**
> No sir, i am running it on a desk top and only have one mouse connected
Do you have an other mouse to verify that it's not a problem with the mouse/mice?

---

### Post by cliff_bisch on 2008-11-14
i do not have another mouse but pretty sure mouse is not a prob as it works fine with xp and also worked fine with 8.04

---

### Post by LowSky on 2008-11-14
well you can try two things.

Unplug the mouse, wait a few seconds (like 5) then plug it back in, or try another port.

OR
 Try to Repair Xorg.

---

### Post by cliff_bisch on 2008-11-14
tried different ports and unplugging it is a usb mouse btw, let's try to repair xorg?

---

### Post by jpoRS on 2008-11-14
To reconfigure xorg just open a terminal and run

```
sudo dpkg-reconfigure xserver-xorg
```

Follow the prompts and set everything properly, when in doubt of what to set it to, the default values will USUALLY work fine.

Good Luck,
jim

---

### Post by cliff_bisch on 2008-11-17
it is working!!! thank you so much

---

### Post by maxcomx on 2009-04-17
Hi there, i got another mouse problem, like once in a while the mouse can still move but the button of the mouse doent work at all, but i can do what ever with the keybord, everything else then the mouse is working.

i have ubuntu 8.10, install on hp pavilion dv6000 version and i use an optic mouse microsuck.

its a new problem since a week by now, i ve been using this version of ubuntu for at least 6 month by now.

so when the problem append i just log off ctrl+alt+backspace and log back in and it work fine until the next time.

thanx in advance for help.

---

### Post by jpoRS on 2009-04-18
I am guessing you tried reconfiguring Xorg already?

jim

---

