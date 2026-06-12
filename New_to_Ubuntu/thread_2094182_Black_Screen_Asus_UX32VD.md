---
title: "Black Screen Asus UX32VD"
date: 2012-12-13
forum: New to Ubuntu
---

### Post by Tafrija on 2012-12-13
I replaced Windows 7 with Ubuntu 12.04 and it went well though I lost operation of fn keys. On upgrading to Ubuntu 12.10, start up is giving black screen though I can hear the drum beat. Kindly assist.

---

### Post by Bashing-om on 2012-12-13
Tafrija; Hi ! Welcome to the forum.

Other than the function keys not working in 12.04, all else was good ?
In the 12.04 install did you have a proprietary graphics driver installed ?
Try this: Boot up ubuntu in "recovery mode" from the grub boot menu;
software center->additional drivers-> install the recommended driver.

[INDENT][INDENT]just ry'n to help < == BDQ

[/INDENT][/INDENT]

---

### Post by COMECON on 2012-12-13
If you can boot from the rescue mode, try running this before installing the drivers:
```
 $ sudo apt-get install linux-headers-generic 
```

(You must be connected to Internet)

Catbuntu

---

### Post by adrien214 on 2012-12-13
As for the FN keys, you might wanna check over [here]("https://help.ubuntu.com/community/AsusZenbookPrime") also, get better support [here]("http://ubuntuforums.org/showthread.php?t=2005999").

---

### Post by squakie on 2012-12-14
You may also want to look at the VGA= options for the boot line, then try various of those (you do this before Ubuntu starts booting).  That *might* get you to a GUI.  Normally I would also recommend trying things like nomodeset, acpi=no and noapic, but I don't know at what point they "kick in" compared to just being at the login screen.

---

### Post by Tafrija on 2012-12-14
Thank you guys for your responses...very encouraging indeed. Got my GUI back but have to put my Asus UX32VD on sleep mode (fn+f1) and back up using power button every time I start up. Alternatively with the dark screen on at start up, once i hear the drum beats prompting for login password, I close the lid and open it ..and hey, GUI is back.!

---

