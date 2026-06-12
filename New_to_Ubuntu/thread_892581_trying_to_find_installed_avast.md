---
title: "trying to find installed avast"
date: 2008-08-17
forum: New to Ubuntu
---

### Post by cwh61 on 2008-08-17
just got ubuntu installed and loving it.im am new to linux so please bare with me. when i try to install avast a/v im told that program is already installed.for the life of me i cant find it anywhere can someone shed a little light on this for me any help would be greatly appreciated.

---

### Post by rburkartjo on 2008-08-17
cw, open the terminal and type whereis(space) avast. this should tell you where it is installed/cheesemaker

---

### Post by Paqman on 2008-08-17
How did you install it? Using the .deb from the Avast site?

Btw, you don't really need antivirus if you're just running a desktop system.

---

### Post by thiebaude on 2008-08-17
Paqman is right, you dont need an anti-virus program in ubuntu, unless you want one.

---

### Post by cwh61 on 2008-08-17
yep there it is . thanks

---

### Post by cybrsaylr on 2008-08-17
As others said, you don't really need AV with Ubuntu.
Why did you install Avast?

---

### Post by Sealbhach on 2008-08-17
Yes, welcome to the forum. As the others have said, you don't really need to worry about viruses in Linux, there aren't any out in the wild (yet).


.

---

### Post by sleepingdragon on 2008-08-17
OK. I'm not going to go into the need/want thing of AV in Ubuntu, but to get Avast running, you can call *avastgui* in a terminal to bring up an interface, or you can try *sudo avast-update* to update the AV virus definitions. 

To run Avast from the command-line, you need to call *avast /home/your_username/ *to scan your home directory. It will scan as normal, but without a GUI. The command-line version will give a summary when it finishes a scan.

---

