---
title: "Screen Resolution - Unreadable"
date: 2008-11-02
forum: New to Ubuntu
---

### Post by DanManIt on 2008-11-02
I changed the resolution on my monitor and now the screen is completely unreadable. I have searched the forums and I have not been able to fix my problem.


I have tried using:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

but nothing happens and I obviously can't read what the terminal is saying anyway.

---

### Post by DanManIt on 2008-11-02
after trying again, i opened the terminal... the previous command returns "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2008...."

but does nothing else

---

### Post by Haluci on 2008-11-02
You may want to try booting off a live cd and editing xorg.conf from there.

---

### Post by overdrank on 2008-11-02
> **DanManIt said:**
> after trying again, i opened the terminal... the previous command returns "xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.2008...."

but does nothing else

Have you restarted x after using that command? ctrl, alt, backspace
You may also boot into recovery mode which is usually the second choice from the grub and use the xfix option.

---

### Post by DanManIt on 2008-11-02
> **overdrank said:**
> Have you restarted x after using that command? ctrl, alt, backspace
You may also boot into recovery mode which is usually the second choice from the grub and use the xfix option.

yeah i did both, neither of those fixed it which surprised me

---

### Post by overdrank on 2008-11-03
> **DanManIt said:**
> yeah i did both, neither of those fixed it which surprised me

What is the model of graphics card.

---

### Post by DanManIt on 2008-11-03
7600gt. this happened right after a fresh install of ubuntu

---

### Post by DanManIt on 2008-11-05
does that help at all?

---

### Post by overdrank on 2008-11-05
> **DanManIt said:**
> does that help at all?

If the xfix option and the reconfigure of the xorg fail also then I would test the system with the live cd.

---

### Post by Peter09 on 2008-11-05
In a terminal type
```
lshw -C display
``` and post the output.

Lets see what driver is installed.

---

### Post by DanManIt on 2008-11-05
> **overdrank said:**
> If the xfix option and the reconfigure of the xorg fail also then I would test the system with the live cd.

it works fine with the live cd

---

### Post by DanManIt on 2008-11-05
> **Peter09 said:**
> In a terminal type
```
lshw -C display
``` and post the output.

Lets see what driver is installed.

it would just be the standard one as this happened right after a fresh install of ubuntu

---

### Post by DanManIt on 2008-11-07
maybe I'm best off just reformatting.

---

