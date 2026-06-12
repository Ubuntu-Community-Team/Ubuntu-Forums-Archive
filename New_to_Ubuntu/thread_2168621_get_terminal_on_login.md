---
title: "get terminal on login"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by Autodave on 2013-08-18
Xubuntu 12.4.  Always started fine, now today only boots me into the terminal.  How do I fix this?

---

### Post by ahmad3 on 2013-08-18
what does the reminal say?

---

### Post by Autodave on 2013-08-18
> **ahmad3 said:**
> what does the reminal say?

It asked for my name and password: which I enetred.  Then:
Last login: Sun Aug 18  15:07:39 EDT 2013 on tty1
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-51-generic i686)

---

### Post by ahmad3 on 2013-08-18
are u sure u didnt press any buttons during bootup? that might happen if not look up in the options from the GNU menu

---

### Post by Autodave on 2013-08-18
Tried it 6 times now: just goes to terminal.

---

### Post by Autodave on 2013-08-18
Tried it 6 times now: just goes to terminal.

---

### Post by zealibib slaughter on 2013-08-18
can you post the output of your boot log located at /var/log/boot.log, and maybe /var/log/Xorg.log (it may be Xorg.0.log or some number. When you post these enclose them in the code tags please. You also can try to execute [code]service lightdm (re)start and look for errors.  That also will allow you to use tail on the Xorg log and get any errors.

---

### Post by Jonathan Precise on 2013-08-18
> **Autodave said:**
> It asked for my name and password: which I enetred.  Then:
Last login: Sun Aug 18  15:07:39 EDT 2013 on tty1
Welcome to Ubuntu 12.04.2 LTS (GNU/Linux 3.2.0-51-generic i686)

Try pressing Ctrl, Alt, and F7 at the same time. If not, type in the terminal:

```
startx
```

Then press Ctrl, Alt, and F2 at the same time, and type:

```
sudo lightdm
```

---

