---
title: "Ubuntu 14 stuck at purple screen - prior solutions not working"
date: 2016-08-15
forum: New to Ubuntu
---

### Post by bjcowen on 2016-08-15
Hey, So Ubuntu is stuck at the purple screen where I select Ubuntu for startup. It says the usual,
"The highlighted entry will be executed automatically in 10s." However, this timer does not move. I cannot use arrow keys at this screen, and clicking enter to take me to the login screen does not work. Holding shift as the computer boots does not do anything either. What could be going on here? I was running a program earlier, and the computer just restarted (which it has done before). This time though, it does not want to let me log back in. Please help, this is an urgent request. I need to be able to login to get work done.

---

### Post by grahammechanical on 2016-08-15
It sounds like that you are already seeing the Grub boot menu. Therefore, holding shift will have no effect.

If the computer is restarting on its own the machine could be over-heating. You could try entering the BIOS setup utility and checking the temperatures. The CPU might have stopped working. That might be the reason for the countdown stopping.

Regards

---

### Post by bjcowen on 2016-08-16
> **grahammechanical said:**
> It sounds like that you are already seeing the Grub boot menu. Therefore, holding shift will have no effect.

If the computer is restarting on its own the machine could be over-heating. You could try entering the BIOS setup utility and checking the temperatures. The CPU might have stopped working. That might be the reason for the countdown stopping.

Regards


I was able to get in the bios, but the same thing happens. I cannot navigate at all.

---

### Post by Hirak Mehta on 2016-08-16
I think its boot loader problem

Try Boot-repair tool

follow instructions on this[ page ]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by bjcowen on 2016-08-16
> **Hirak Mehta said:**
> I think its boot loader problem

Try Boot-repair tool

follow instructions on this[ page ]("https://help.ubuntu.com/community/Boot-Repair")
 If I can't change the boot order in bios, how can I boot from a live cd?

---

