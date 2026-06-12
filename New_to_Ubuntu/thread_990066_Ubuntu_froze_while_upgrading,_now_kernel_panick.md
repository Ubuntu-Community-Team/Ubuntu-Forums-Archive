---
title: "Ubuntu froze while upgrading, now kernel panick"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by TommySprat on 2008-11-22
I was upgrading from 8.04 to 8.10 but in the middle of the installation ubuntu froze and didn't respond to anything. I didn't touch it for 20 minutes becausei wasn't sure what was going on but then i decided to force a restart with the power button.
That's where the trouble starts. I can choose from 2 kernels: 2.6.24-21 and 2.6.27-7. 
If i pick the old one it does some stuff but before i get to the login screen it presents me with a messed up resolution saying no display could be found, and it doesn't respond to the mouse or keyboard.
If i pick the new kernel it doesn't get far (not as far as the other one) and says kernel panick.

I know i can wipe it all off my HDD and start clean again but that way i won't learn anything. So, can i repair this?

---

### Post by Tomatz on 2008-11-22
Dont think there is much you can do. Unless you can boot recovery mode (which i doubt). Kernel panic obviously means there is a problem internally with the kernel from which it cant recover. Probably due to it (or part of it) only being part installed during the upgrade.

I would reinstall :(

---

### Post by Vadi on 2008-11-22
Yeah. Copy your data off (maybe using a livecd), and install the 8.10

---

### Post by Gone fishing on 2008-11-22
What happens if you boot from recovery mode with the old kernel and then try an fix X with xfix?

Then try and complete the upgrade (although I suspect a new install will be better)

---

