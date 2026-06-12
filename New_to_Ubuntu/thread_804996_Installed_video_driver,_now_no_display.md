---
title: "Installed video driver, now no display"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by jockmullin on 2008-05-23
Greetings.

Total newbie just installed Hardy on Dell Inspiron laptop. Was going great but I couldn't enable video effects so it said to install a new video driver which I did and rebooted as requested. Now at boot I see the startup but at logon screen goes black. I can still log in, but can't see anything.

Can I roll back the driver? How to boot to console? 

Any help appreciated.

Jock

---

### Post by alienexplorers on 2008-05-23
What video card are you running and what driver did you load?

---

### Post by geezerone on 2008-05-23
Boot into safe mode for Ubuntu. Then at the command prompt type the following:

```
sudo dpkg-reconfigure xserver-xorg
```to reconfigure your xserver settings. Most are default settings and this will set screen resolutions as well as selecting your driver. With nvidia problem drivers you normally use *nv* instead of nvidia in the /etc/X11/xorg.conf file (edit with *nano /etc/X11/xorg.conf* command)

Let us know how you get on.

---

### Post by jockmullin on 2008-05-23
Bios saysNVIDIA GeForce4Go.
I loaded the GeForce driver (sounded like a good idea at the time :))

---

### Post by jockmullin on 2008-05-23
Bios says NVIDIA GeForce4Go.
I loaded the GeForce driver (sounded like a good idea at the time :))

---

### Post by subzero316 on 2008-05-23
Boot normally ,
press CTRL+ALT+F1 you`ll enter console mode...

---

### Post by jockmullin on 2008-05-23
Hi, geezerone

OK that is what I was looking for.
Hwver, still stuck at "boot into safe mode". How is that done, pls.

Jock

---

### Post by alienexplorers on 2008-05-23
Hit <esc> when the grub loader starts loading and select from the menu safe mode.

---

### Post by jockmullin on 2008-05-23
Thanks guys.

Geezerone & Anish - bang on. Back in business now, many thanks.

Jock

---

