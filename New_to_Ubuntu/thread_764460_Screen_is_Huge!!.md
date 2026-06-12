---
title: "Screen is Huge!!"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by bt224 on 2008-04-23
My screen is gigantic, and I don't mean the monitor. I have to scroll around with the mouse to see the corners. Help!

---

### Post by Opeth115 on 2008-04-23
do a ctrl + alt + f1, to get into a command line then do a 

sudo dpkg-reconfigure xserver-xorg

answer all the questions and when it gets to where you sleect ur screen resolution, choose teh correct size for your mointor, see if that works for you.

Edit: after you go through with the reconfiguring hit alt + f7 to get back to a gui.

---

### Post by Can+~ on 2008-04-23
Before you do that!

Remember that to jump back to the GUI view:
Ctrl+Alt+F7

The F1-F6 are other terminals

---

### Post by Opeth115 on 2008-04-23
> **Can+~ said:**
> Before you do that!

Remember that to jump back to the GUI view:
Ctrl+Alt+F7

The F1-F6 are other terminals

yea yea i added it ;)

---

### Post by bt224 on 2008-04-23
No luck, it kicked me out to the prompt

---

### Post by Opeth115 on 2008-04-23
doing a 
 
sudo dpkg-reconfigure xserver-xorg

didn't give u like a blueish dialouge box, with a bunch of steps?

---

### Post by austin.lund on 2008-04-23
Also try Ctrl-Alt-+ where the plus is the one on the numpad (I think it makes a difference).  Try it a few times.  

Basically your desktop resolution is bigger than the screen resolution. 

Try fiddling with the resolution settings in with the tool located in the configuration menu.

---

### Post by bt224 on 2008-04-23
No, it started to take me thru the questions, but it didn't finish. 

I rebooted and it wanted to configure. I selected my monitor and card. When it booted it was much better, but not enough resolution. So I enabled the nvidia prop driver. Now I'm back where I was. I just disabled and am rebooting.

---

### Post by SunnyRabbiera on 2008-04-23
what version are you using?

---

### Post by bt224 on 2008-04-23
8.04

Not sure WTF I did, but it's fixed. I appreciate the help, seriously appreciate it.

---

### Post by SunnyRabbiera on 2008-04-23
the beta or the release candidate?

---

### Post by bt224 on 2008-04-23
been running it and updating since beta

---

### Post by SunnyRabbiera on 2008-04-23
ah, there may be your problem.
sometimes doing stuff like that can mess up the system very easily.

---

