---
title: "stuck in low grapics mode"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by hnf a on 2012-09-29
hi everyone i want to ask how to fix ubuntu in low graphics mode, after yesterday update my computer is showing that error i've try dpkg-reconfigure unity-greeter,light dm ,apt-get purge fglrx (all in sudo) but nothing happen even when i try to go to liveCD it just showing random pixel color i'm using HD5570 , BUT when i put my old nvidia 7300 it works like nothing happen, i have dual boot when i go to windows with my ati it still working i assume the HD hardware is not my prob anyone can fix this?

---

### Post by Gone fishing on 2012-09-29
Sorry but I'm guessing and my guess is that if you have removed the fglrx driver, then you are using the opensource driver and it has a problem with your video card. I suggest you start in recovery mode and pick the safe graphics option. Once you have logged in you try using the Additional drivers tool, install the driver and reboot. 

Hopefully it will be OK - If that doesn't work remove the propriatory driver start again and select a different version of the driver.

---

### Post by hnf a on 2012-09-29
no, the problem start when the fglrx still installed and in tty i remove it hoping the prob will fix but it didn't happen, one more thing i cannot go to the desktop with my ati so i can't istall additional driver.

---

### Post by Gone fishing on 2012-09-29
Can't you start up in recovery mode, then pick failsafe X and then login in?

---

### Post by hnf a on 2012-09-29
i can't do that when i do it its just show low graphic mode and back to tty

---

### Post by mips on 2012-09-30
> **hnf a said:**
> i can't do that when i do it its just show low graphic mode and back to tty

From grub you can edit the kernel line adding nomodeset, you can also try adding nomodeset in conjunction with removing quiet & splash which should allow you to boot to shell from where you can manually install the drivers.

---

### Post by hnf a on 2012-10-01
thaks very much its working by installing the ati beta driver and the unity 3d is BACK

---

