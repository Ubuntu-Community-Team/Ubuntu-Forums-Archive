---
title: "Can't get boot menu on Acer Aspire One D257 -13DQkk"
date: 2013-01-12
forum: New to Ubuntu
---

### Post by nic2549 on 2013-01-12
I have just bought a low powered laptop (netbook), running Windows 7. I have run Linux on previous laptops and my intention was to set up this machine to dual boot Windows and Ubuntu. Unfortunately the BIOS seems to be locked down and although I can get to a set up menu using F2, I cannot get to a boot menu. On my previous netbook (motherboard died over Christmas) I could enable the boot menu from within setup, but this new one doesn't give that option Any ideas? A friend told me that I might have to flash the BIOS. I have no idea how to do that and I'm concerned that I would invalidate the warranty and it might not work.
Any help would be appreciated.
Nic

---

### Post by Mark Phelps on 2013-01-12
Don't charge into flashing the BIOS.  Any mistake there will turn your netbook into an electric brick! You should only flash your BIOS when (1) there is a know specific problem that a BIOS upgrade fixes, and (2) you know EXACTLY what you're doing.

Sorry, but BIOS upgrades aren't magical cures.

---

### Post by krustenBrot on 2013-01-12
Have you tried this?
> 4) On Netbook, Turn On, and Hit F2 right on the first Intel Screen (Boot Screen)
 5) Go into "Main" and go to down to "F12 Boot Menu" and Make it "Enabled", Press F10 and Restart..
 6) Press F12 on the boot screen and it will bring up a Boot menu,  select USB (The only one not empty/blank but it should be the "USB HDD"  if you put it in the one on the right side.


Found this on another forum.. and if it is true you have to enable the boot menu first. Please report back if it worked. 
Would  be interesting... I do know Acer sometimes shuts down the whole BIOS by  setting a Master Password disabling it will cost you around 100 $ and  you'll have to send your machine in.

---

### Post by nic2549 on 2013-01-12
I had an Acer Aspire One previously, on which I could enable the boot menu as you've described. Unfortunately on this new Aspire One, they seem to have locked it right down and there isn't an option to enable the boot menu.
This is looking like I'm stuck with Windows 7. Ugh.

> **krustenBrot said:**
> Have you tried this?


Found this on another forum.. and if it is true you have to enable the boot menu first. Please report back if it worked. 
Would  be interesting... I do know Acer sometimes shuts down the whole BIOS by  setting a Master Password disabling it will cost you around 100 $ and  you'll have to send your machine in.

---

### Post by nic2549 on 2013-01-16
I finally managed to resolve the problem myself. I knew that it must be possible to get to the boot menu, because I've seen other posts on linux forums discussing issues with this particular model of Acer Aspire.
In case anybody else wants to get to the boot menu, you need to hit F2 when booting the machine. This will initially take you into the very restricted Setup menu (which doesn't enable you to change boot order). Once in the Setup menu, hit Esc to exit. The system will try to start Windows, but if you quickly hit F2 again it takes you into a full Setup menu which enables you to set the boot order.
Anyway, it worked and I've set the netbook to dual boot Linux or Windows 7 (Linux first of course).

---

