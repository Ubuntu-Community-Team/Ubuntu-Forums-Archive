---
title: "Wrong Intel graphics driver enabled after install"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by qrwe on 2008-09-25
Hello,

I have an Intel graphics card ("Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller"). The correct driver was enabled when using LiveCD, but after installing Ubuntu it's something else; e.g. compiz doesn't work now.

Does anyone know what driver I should use and how to enable it from here after?
Thanks for help!

---

### Post by shifty_powers on 2008-09-25
it might be a restricted driver, i.e. not open source.

try going into system>admin>hardware drivers

(iirc... been using kubuntu 8.10 for a while :D)

---

### Post by qrwe on 2008-09-25
> **shifty_powers said:**
> it might be a restricted driver, i.e. not open source.

try going into system>admin>hardware drivers

(iirc... been using kubuntu 8.10 for a while :D)

Nope, just "No proprietary drivers are in use on this system" and an empty box (from where I could choose the correct driver otherwise, I guess).
Is there a way to confirm what driver I should use from the LiveCD in any way?

---

### Post by phidia on 2008-09-25
There is no proprietary driver available for your card or at least not through the Hardware Drivers applet. You should be using the "intel" driver take a look in the device section of your /etc/X11/xorg.conf if the "intel" driver isn't there you could just edit that file. "gksudo gedit /etc/X11/xorg.conf" 

Also check out a related thread [here]("http://ubuntuforums.org/showthread.php?t=897114&highlight=GM965%2FGL960+Integrated+Graphics+Controller").

---

### Post by qrwe on 2008-09-26
> **phidia said:**
> There is no proprietary driver available for your card or at least not through the Hardware Drivers applet. You should be using the "intel" driver take a look in the device section of your /etc/X11/xorg.conf if the "intel" driver isn't there you could just edit that file. "gksudo gedit /etc/X11/xorg.conf" 

Also check out a related thread [here]("http://ubuntuforums.org/showthread.php?t=897114&highlight=GM965%2FGL960+Integrated+Graphics+Controller").

Thank you, it's a step in the right direction.
..but compiz still doesn't work, so something is still missing. As it worked perfectly in LiveCD, there must be something more. Are there any modules that should be added too?

---

### Post by phidia on 2008-09-26
You could open a terminal and enter "lsmod" then boot from the live cd and do the same-compare the two outputs to see if there is something not loading or needed in your install.

---

