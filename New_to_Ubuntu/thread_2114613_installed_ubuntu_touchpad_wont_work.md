---
title: "installed ubuntu touchpad wont work"
date: 2013-02-10
forum: New to Ubuntu
---

### Post by philipwade6 on 2013-02-10
just installed ubuntu on my netbook.

my touchpad doesnt do aything but if i plug my wireless mouse in it works fine. How can i get the touchpad to work (theres nothing wrong with it i dont think)

---

### Post by sanderj on 2013-02-10
Which Ubuntu version?

I would do update/upgrade, then reboot (so that all updates are done) and then check again.

If it still doesn't work, some more analysis (lspci, lsusb, dmesg) is needed.

---

### Post by philipwade6 on 2013-02-10
> **sanderj said:**
> Which Ubuntu version?

I would do update/upgrade, then reboot (so that all updates are done) and then check again.

If it still doesn't work, some more analysis (lspci, lsusb, dmesg) is needed.

the latest one (12.04 i think thats it yeah)  desktop.

ill try and update it now but i heard there was a glitch with touchpads if thas the problem can it be fixed

---

### Post by philipwade6 on 2013-02-10
so updates  are finished and still nothing

anyone got any ideas?

---

### Post by sanderj on 2013-02-10
Does

```
dmesg | grep -i synap

```
say anything useful?

---

### Post by philipwade6 on 2013-02-10
> **sanderj said:**
> Does

```
dmesg | grep -i synap

```
say anything useful?

i dont know what that means sorry

---

### Post by sanderj on 2013-02-10
Open a terminal, a type (or copy) that command. If there is output, post it here.

---

### Post by GameX2 on 2013-02-10
> **philipwade6 said:**
> i dont know what that means sorry

Paste the result of the command; do Ctrl-Shift-C to copy from the Terminal (Or Right-Clic>Copy) and paste it here (If the command display anything).

---

### Post by philipwade6 on 2013-02-10
how do i get a teminal

---

### Post by GameX2 on 2013-02-10
Ctrl-Alt-T;
Or press the Windows key, and start typing "Terminal" in the Dash.

---

### Post by 0N3 on 2013-02-10
Use your mouse and search for Mouse in the dash open it up and see if touchpad is disabled.

---

### Post by philipwade6 on 2013-02-10
copied and pasted that command but nothing happened

thanks guys what else can i do

---

### Post by 0N3 on 2013-02-10
Have you tried?

Use your mouse and search for "Mouse" in the dash open it up and see if touchpad is disabled.

---

### Post by philipwade6 on 2013-02-11
> **0N3 said:**
> Have you tried?

Use your mouse and search for "Mouse" in the dash open it up and see if touchpad is disabled.

i went on mouse and touchpad and it didnt say anything about touchpad once inside just a tag for mouse.


also the keyboard has gone funny- u stopped working and l became a forward slash it was working fine before (i checked configuration and its still on the korean keyboard layout the computer was designed for.

the updates have just made it go funny :(

---

