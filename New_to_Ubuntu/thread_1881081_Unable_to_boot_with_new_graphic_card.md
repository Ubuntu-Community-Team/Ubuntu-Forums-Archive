---
title: "Unable to boot with new graphic card"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by mylisa on 2011-11-14
:P:(I am running Natty 11.04.  I am unable to boot up after installing a new Asus 210 silent Graphic Card.  Can anyone help me understand what's going on.

---

### Post by jtarin on 2011-11-14
Explain your boot process. What happens , what do you see or not see?

---

### Post by cariboo on 2011-11-15
I'd suggest removing your /etc/X11/xorg.conf file, and reboot.

Start in recovery mode and choose drop to root prompt from the menu, once at the prompt type the following command:

```
rm /etc/X11/xorg.conf
```

next type:

```
exit
```

then select resume from the menu.

---

### Post by hansdown on 2011-11-15
Welcome to the forum, mylisa.

Are you, O.K., with the terminal?

---

### Post by mips on 2011-11-16
Can your PSU cope with the new card?
Have you updated your bios to the latest version?

---

### Post by pqwoerituytrueiwoq on 2011-11-16
did your switch from a ati chipset (uses fglrx as the driver) to a nvidia chip set?
if you you have to do this from recovery
[FONT=Courier New]sudo apt-get purge  fglrx;suto apt-get install nvidia-current[/FONT]
if you did the opposite
[FONT=Courier New]sudo apt-get purge nvidia-current;sudo apt-get install  fglrx[/FONT]

---

