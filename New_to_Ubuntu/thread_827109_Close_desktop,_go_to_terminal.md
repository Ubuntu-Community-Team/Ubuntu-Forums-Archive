---
title: "Close desktop, go to terminal"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by japhyr on 2008-06-12
Hi everyone.  I chose the wrong video driver in HH, and wound up with a completely garbled desktop.  How do I use the keyboard to close the desktop and stay at the terminal, so I can replace the wrong xorg.conf?  Ctrl-alt-backspace restarts the desktop.

---

### Post by decoherence on 2008-06-12
ctrl alt f1
ctrl alt f2
etc

alt f7 to get back to the desktop.

---

### Post by kdcoetzee on 2008-06-12
Hi there.

sudo dpkg-reconfigure xserver-xorg

That should run you through setting up X again.

---

### Post by japhyr on 2008-06-12
Oops, it's more messed up than I thought.  I got into the terminal using ctrl-alt-F1.  However, when I replaced the xorg.conf file (sudo cp xorg.conf_backup-061108 xorg.conf), then use ctrl-alt-F7, I still have a garbled desktop.

Does ctrl-alt-F1, copy xorg.conf, ctrl-alt-F7 use the new copy of xorg.conf?  Or do I need to somehow stop x and restart it?

---

### Post by japhyr on 2008-06-12
I think I got it, but maybe not the cleanest way.  I think I stopped x using "sudo /etc/init.d/gdm stop".  Anyway, when I used startx after this, I got into a useable desktop.  Is there a cleaner way to do this?

---

### Post by kdcoetzee on 2008-06-12
you can just type restart 

```
sudo /etc/init.d/gdm restart
```

i think now that you got a usable desktop. 
just backup your xorg.conf file(the working one) 
if this happens again you have a fall back.
something like:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

I think you fixed it. if you reboot the machine. does Ubuntu act normally or does xserver fail again.

---

### Post by Nythain on 2008-06-12
you could have just control+alt+backspace after you replaced the xorg.conf and hit control+alt+f7...

but yeah, the cleanest way would have probably been
sudo /etc/init.d/gdm restart

that stops gdm then starts it back up, effectively killing your xsession and display manager and starting it all over, using the new (or old in this case) xorg.conf :)

---

### Post by japhyr on 2008-06-12
Thanks.  I'll use "sudo /etc/init.d/gdm restart" from now on.

---

### Post by decoherence on 2008-06-13
fyi I've found in the past that "sudo /etc/init.d/gdm restart" occasionally doesn't work. If you find that's the case you can use "sudo /etc/init.d/gdm stop" then "sudo /etc/init.d/gdm start" ... same difference.

---

