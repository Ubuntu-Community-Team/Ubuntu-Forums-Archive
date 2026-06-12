---
title: "How do I drop down into a terminal?"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by Zukaro on 2012-04-28
How do I drop down into a terminal when in Ubuntu 12.04?
(like, I need to disable graphics mode; when I type "sudo stop lightdm" my system hangs after stopping it (I can still type but commands wont work as it's not in the spot you enter them (like, it's still doing stuff like stopping services but it freezes and wont get to the part where I can start entering commands))).

I need to install some NVIDIA drivers and I can't do it while X is running (or lightDM? (it says NVIDIA can't install while X is running)).

I've searched Google for about and hour and found absolutely nothing.

---

### Post by zombifier25 on 2012-04-28
At login, press Ctrl - Alt - F1 to drop into tty1. It will give you a terminal, no X. Whether or not you need to kill X in tty7 after doing so, I don't know.

---

### Post by ubudog on 2012-04-28
Try pressing CTL+ALT+F1.

Then login with your username and password.

Edit: zombifier beat me to it!

---

### Post by Zukaro on 2012-04-28
Okay; thanks.  But despite doing that the NVIDIA installer still tells me I'm running an X Server or something like that.

*isn't sure what to do to disable that*

---

### Post by ubudog on 2012-04-28
Once you're at the console, type: 
```
sudo service lightdm stop
```

That *should* do it.

---

### Post by Zukaro on 2012-04-28
It worked; thanks.  :)

---

