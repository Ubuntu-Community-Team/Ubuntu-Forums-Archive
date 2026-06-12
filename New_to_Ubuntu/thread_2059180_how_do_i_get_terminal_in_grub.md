---
title: "how do i get terminal in grub ?"
date: 2012-09-17
forum: New to Ubuntu
---

### Post by snifer7 on 2012-09-17
im using ubuntu 12.4 , i installed ati driver (that downloaded from amd website) and now ubuntu says:<br>
 "ubuntu is running in low-graphic mode , your screen graphic card .... "

**i wanna use terminal to fix this problem , but dont know how to get terminal in grub !!**

please help :) <br>thanks

---

### Post by Wim Sturkenboom on 2012-09-17
Select recovery mode, I guess ;)

But you can also use <ctrl><alt><Fn> (where n = 1..6) after the boot has completed.

---

### Post by bogan on 2012-09-17
Hi!, **snifer7,**

If you want a terminal in grub, press 'Crtl+c' but that has very limited functions.

Otherwise, for a tty terminal login prompt, press 'Crt+Alt+F1' [or F2-F6, 'Crt+Alt+F7' will return you to what should be a GUI screen]; or boot from a recovery mode, use the 'fsck' option to set to Read/Write, and then choose the 'Drop to root Terminal' option.

Chao!, **bogan.**

---

### Post by Bashing-om on 2012-09-17
There are a number of options to obtain the terminal. As you are looking to make adjustments to your system, might I suggest opening a root terminal ?
 To do so: When booting the system, after the bios screen clears, depress and hold any key->boots into the grub menu. From the grub menu choose a "recovery mode" giving you options on booting.
 
  Using root access can be hazardous to your system in that a slip in thoughts or fingers can have irreverseable effects.

Preferable: Boot into the graphics degraded state ...ctl+alt+t -> terminal ...if admin privileges are required "sudo" is available. 

[INDENT]hth <==BDQ
[/INDENT]

---

### Post by snifer7 on 2012-09-19
thanks ... 
 fixed :)

im using dear ubuntu again :-)

---

