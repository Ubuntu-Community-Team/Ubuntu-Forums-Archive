---
title: "firefox 3 on ubuntu 8.05 crashes"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by lunaluna on 2008-04-30
firefox from time to time freezes and makes me unplug the system from power supply.
reinstalling might help but i dont know...
some help?

---

### Post by Dylnuge on 2008-04-30
Did you upgrade to 8.04 from another version of Ubuntu or install it fresh?

---

### Post by warbread on 2008-04-30
> **lunaluna said:**
> firefox from time to time freezes and makes me unplug the system from power supply.
reinstalling might help but i dont know...
some help?

WHAT?  I can't even get Windows to crash that hard anymore.  I suspect that you don't need to do that at all.  Next time you find yourself with such a crash, press CNTL + ALT + Backspace.  

In the meantime, know that there has been a bug report filed.

---

### Post by Zalbor on 2008-04-30
Unplug from power suppy? Why do that?
You can go to System>Administration>System Monitor>Processes and end "firefox" from there, or you can open a terminal and type "killall firefox", or (a bit extreme) you can press Ctrl-Alt-Backspace to restart the graphical environment, or (very extreme) you can restart the computer.
Why do you pull the plug just to stop a frozen program? It's like attacking a fly with a cannon, and not good for your computer. :)

---

### Post by muteXe on 2008-04-30
I just installed FF2.  FF3 isn't there yet in my opinion.

---

### Post by iSplicer on 2008-04-30
I think you meant ubuntu 8.04, not 8.05 =)

---

### Post by Dylnuge on 2008-04-30
> **muteXe said:**
> I just installed FF2.  FF3 isn't there yet in my opinion.

I agree. For an LTS release, I'm not exactly sure why Cannocial decided to package a beta software.

---

### Post by lunaluna on 2008-04-30
> Did you upgrade to 8.04 from another version of Ubuntu or install it fresh?

fresh one
> 
Unplug from power suppy? Why do that?
You can go to System>Administration>System Monitor>Processes and end "firefox" from there, or you can open a terminal and type "killall firefox", or (a bit extreme) you can press Ctrl-Alt-Backspace to restart the graphical environment, or (very extreme) you can restart the computer.
Why do you pull the plug just to stop a frozen program? It's like attacking a fly with a cannon, and not good for your computer. 

i only see black blanv screen helpless

> WHAT? I can't even get Windows to crash that hard anymore. I suspect that you don't need to do that at all. Next time you find yourself with such a crash, press CNTL + ALT + Backspace.


next time i will

__________________________
i'll try reinstalling and see what happens...

---

### Post by Dylnuge on 2008-04-30
> **lunaluna said:**
> 
i only see black blanv screen helpless

Even so, you should always try holding the power button and CTRL-ALT-BACKSPACE first.

Can you go into the terminal (Applications->Accessories->Terminal), run an lspci, and post the results here? You might want to try that before reinstalling.

EDIT: Sorry. To clarify, the results can help us understand the computer you are on. It won't fix the problem.

---

