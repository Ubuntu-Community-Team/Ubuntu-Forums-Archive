---
title: "what should i do when ubuntu freezes?"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by T2manner on 2008-11-08
in windows, when something froze i could just to Ctrl+Alt+Delete (ctrl+shift+esc) and end the app/process.

what should i do when something freezes in ubuntu?

---

### Post by Zzl1xndd on 2008-11-08
if its just a progeam then System > Administration > System Monitor will give you pretty much the same options as the Windows Task Manager. If everything freezes CTRL+ALT+Backspace will restart X.

---

### Post by niccholaspage on 2008-11-08
I would just do a CTRL+ALT+BACKSPACE.

---

### Post by Shazaam on 2008-11-08
And if the above posts do not work do this...
Hold down your Alt+SysRq (PrintScreen) keys and type reisub.
From here...
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

### Post by T2manner on 2008-11-08
> **Shazaam said:**
> And if the above posts do not work do this...
Hold down your Alt+SysRq (PrintScreen) keys and type reisub.
From here...
[http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

yeah, but i heard that that's not really safe a lot of the time and that you should stay away from using that command.

---

### Post by lykwydchykyn on 2008-11-08
> **T2manner said:**
> yeah, but i heard that that's not really safe a lot of the time and that you should stay away from using that command.

It's safer than just cutting the power, if it comes down to that.

If I get a process locking up the system, my method is:

 - ctrl-alt-esc (xkill) 
 - ctrl-alt-f1 to virtual terminal and use kill or killall 
 - ctrl-alt-backspace to kill my x session
 - alt-sysrq-rseiub (I learned it in a different order: Raising skinny elephants is utterly boring)
 - cut the power.

That's a "failover list"; i.e. -- if the first one fails go to the next.

---

### Post by handydan918 on 2008-11-08
> **T2manner said:**
> yeah, but i heard that that's not really safe a lot of the time and that you should stay away from using that command.

Yeah, good point, but the theory of that command is that it is safer than a hard shutdown. 

In reality, if you have installed Ubu with an ext3 filesystem, it will probably recover flawlessly from an inelegant exit.

Edit: Hey again, lykwyd! Good tip! hard to beat a good "failover" (which I constantly hear pronounced as "fallover").

---

