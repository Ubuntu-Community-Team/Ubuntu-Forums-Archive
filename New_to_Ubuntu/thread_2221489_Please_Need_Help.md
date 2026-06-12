---
title: "Please Need Help"
date: 2014-05-02
forum: New to Ubuntu
---

### Post by digs2 on 2014-05-02
i had win vista installed on my pc recently i came across ubuntu so i bought a new hdd and installed ubuntu in that, the hdd on which vista was installed was physically removed, now i wish to attach that vista hdd again to the same pc, now my question is what will happen when i reboot my pc will i get an option to run os of my choice every time?

please anyone who already did that, reply me fast, i'm new to ubuntu.

thanks in advance
Digs:KS

---

### Post by pfeiffep on 2014-05-02
If you're planning on installing a second hard drive you ***should*** be able to select which drive will boot. 

Posting some more info about your hardware will help us help you.

---

### Post by Mark Phelps on 2014-05-02
When you attach the Vista drive, make sure to still boot from the Ubuntu drive.

Then, boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB config file and you should see it add an entry for Vista.

When you then reboot, you should get a menu with entries for Ubuntu and Windows.

---

### Post by drink1297 on 2014-05-02
> **Mark Phelps said:**
> When you attach the Vista drive, make sure to still boot from the Ubuntu drive.

Then, boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB config file and you should see it add an entry for Vista.

When you then reboot, you should get a menu with entries for Ubuntu and Windows.

This is assuming you are going to use both drives together, if your simply planning on swapping the drives each time you want to change OS, Vista will be fine, the NTloader is on that hard drive.

The above quote is the correct method to have both drives in one maching, if you have them both in, and boot into windows first, NTLoader will effectively erase grub, but the other way, grub will acknowledge windows and give you the choice of OS to boot.

---

### Post by digs2 on 2014-05-03
thank you all for your help

---

