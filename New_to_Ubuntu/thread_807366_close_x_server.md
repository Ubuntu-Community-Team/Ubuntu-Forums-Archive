---
title: "close x server"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by bdog676 on 2008-05-25
I need to install some nvidia drivers but I'm not sure how to get out of x. CTRL ALT BACKSPACE brings me to the login screen.

---

### Post by scxtt on 2008-05-25
control+alt+F1
(of course you have to stop the X server, plenty of ways to do that.)

---

### Post by Kinst on 2008-05-25
Give the command init 3 while booting and it won't load the x server at all.

---

### Post by mikewhatever on 2008-05-25
> control+alt+F1

You'll probably get 'x is still running' message after doing that. Try the following, or do it from recovery mode:
> sudo /etc/init.d/gdm stop

---

### Post by bdog676 on 2008-05-25
now it wants libc and kernel headers. I'm used to using yum so I'm not really sure where to look.

---

### Post by Tatty on 2008-05-25
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

These two links are good guides on how to compile things in ubuntu :)

---

### Post by mikewhatever on 2008-05-25
> **bdog676 said:**
> now it wants libc and kernel headers. I'm used to using yum so I'm not really sure where to look.

Look under System>Administration>Synaptic.

---

