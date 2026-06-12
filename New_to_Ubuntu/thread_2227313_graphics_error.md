---
title: "graphics error"
date: 2014-06-01
forum: New to Ubuntu
---

### Post by cybo2 on 2014-06-01
After installing ubuntu. 14. When i logged in after entering the password a part of the screen graphics got distorted. And the system got hung. I have nvidia graphics card. I tried the --reinstall ubuntu desktop.. as given on a website. Tried purging nvidia graphics as suggestes bt no joy. Attaching a pic of the screen.

---

### Post by ajgreeny on 2014-06-01
From your grub menu (hold shift at boot if you don't normally see the menu) hit the E key with the cursor on the kernel you want to boot, then with cursor keys navigate to the line that includes **quiet splash** at the end.  Delete **quiet splash** and replace with **nomodeset**
Now use Ctrl+X to boot that kernel and you should get to a GUI with no graphic glitches.

You can then try installing the proprietary graphic driver for your nvidia card by using **Additional Drivers** from the dash which ought to overcome your problem.

---

### Post by cybo2 on 2014-06-01
thanx a ton...problem solved....

---

### Post by ajgreeny on 2014-06-02
Great.
Can you mark as SOLVED from the Thread Tools menu at the top of this thread.

---

