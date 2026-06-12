---
title: "Linux Pc Help"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by UZU309 on 2008-07-12
Ok guys here is the issue, I meant to install Ubuntu Linux on my Lenovo T61 notebook. I wanted to partition the hard drive but somethings went wrong and now my old OS XP got wiped. Now I tried using the XP boot disk but Linux says that it can't open the .exe file because it is not a folder.Also I cant change the boot order because there is a password on my machine. Now I'm not asking for bios passwords, I just need help opening .exe files.

---

### Post by bumanie on 2008-07-12
What do you want to do? Try to recover xp or do a fresh installation of xp? Was ubuntu installed or does it only work off the live cd? It is possible to remove the bios password, but if the computer is still under warranty, removing the password will void the remainder of the warranty.

---

### Post by UZU309 on 2008-07-12
I want to install XP fresh, but I can not change the bios settings to boot from the CD, since there is a password. When I first installed Linux from the live cd I was using XP. I had to install it while still in XP then reboot for it to work.

---

### Post by bumanie on 2008-07-12
Do you want to know how to remove the bios password? But as said if the computer is under warranty it will void the remainder of the warranty. It is up to you. Installing while in xp, does that mean you used the wubi installer?

---

### Post by UZU309 on 2008-07-12
By all means tell me how to remove the bios password, and yes I did use wubi.

---

### Post by bumanie on 2008-07-12
Never heard a wubi install wiping windows before - very unfortunate. 
You don't have much option other than removing the bios password as all the recovery-type discs, boot as live cd's. OK, to remove the bios password (at own risk re warranty), you have to open your computer and find the button cell battery on the motherboard. There should only be one battery, so it should be easy to find. Find the battery and remove it. Next to the battery there will be a jumper with three pins - remove the jumper and shift it ie if on pin 1 & 2, shift it pin 2 & 3. Leave it there for a couple of minutes. Then move the jumper back to its original position, reinsert the battery and reboot the bios password should be gone. Hope it works. I have done this before and it worked fine. Good luck. If you wish to reinstall ubuntu after xp, it is better to put ubuntu on a separate partition. Do some pre-reading first and of course, you can make a new post here if you have any questions.

---

