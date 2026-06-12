---
title: "X-server doesn't restart"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by tibibo on 2008-06-29
Hi all,
I just installed the Hardy on my laptop Dell Inspiron 1501. All worked fine until I setup Broadcom wireless driver with ```
sudo /usr/share/b43-fwcutter/install_bcm43xx_firmware.sh
``` After rebooting I have pressed <Ctrl>+<Alt>+<Backspace> to restart my X-server, but all the time from this point it makes reboot of my system instead.
Any ideas? 

All the best,
Artjom

---

### Post by spydon on 2008-06-29
Maybe it's best to do a fresh install(if noone comes with a solution) and install your broadcom drivers from System>Administration>Restricted drivers instead.

Was the script made for hardy?

---

### Post by starcannon on 2008-06-29
I have no idea on why your keys are being remapped, you wouldn't happen to have a "del" key near your "bckspc" key would you? and perhaps accidentally pressing Ctrl-Alt-Del?

In the meantime if you need to restart X try ```
sudo /etc/init.d/gdm restart
```

GL and let us know if you solve this, and how you solved it.

---

### Post by tibibo on 2008-06-29
Thank you for the replies. 
> Was the script made for hardy? 
Yes, this is a native script. I get it just installing from the Hardy's CD-box. I found about from [here]("http://linuxwireless.org/en/users/Drivers/b43#devicefirmware") after several unsuccessfully attempts to install driver from System>Administration>Restricted drivers. 

> I have no idea on why your keys are being remapped
I think my keys are NOT being remapped, because <Bckspc> works perfect as it must to. 
> try
```
sudo /etc/init.d/gdm restart
```
I tried and found that system suspend after this (last message: Running local boot script /etc/rc.local, or so) and only <Ctrl>+<Alt>+<Del> is useful to reboot system.
In addition, when I run in the KDE environment all works great, only in GNOME there is the such problems. 
Any help?

Best regards,
Artjom

---

### Post by yo_marcus on 2008-11-01
UP
I have the same problem on my Fujitsu Siemens Lifebook C1320, using Broadcom BCM4318 (Airforce One) on Ubuntu Hardy Heron.
The X server (on tty7) doesn't start (it block after "Running local boot script /etc/rc.local, or so"), I have to login on another tty and type startx.

---

