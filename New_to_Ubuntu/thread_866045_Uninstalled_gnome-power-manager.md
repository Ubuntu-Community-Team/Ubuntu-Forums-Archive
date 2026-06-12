---
title: "Uninstalled gnome-power-manager"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by nepmit on 2008-07-21
Hi, everyone.I've used Ubuntu for several months.Love it but frustrating.
Two days ago I uninstalled gnome-power-manager thru synaptic.Since then I 
can't boot. I get thru the splash screen to the orange/brown desktop and it stops. No Heron image nothing but flashing mouse. Alt f2 and ctrl atl backspace does nothing.I've re installed grub thru the live CD no help. Older kernal don't boot either.
I'm using Hardy on AMD 64 dual,2 gigs of Ram and Nvidia video. 
I really don't want to reinstall Hardy.It took me 3 months off and on to get my scanner working. Thanks for any help.

---

### Post by sisco311 on 2008-07-21
Try to reinstall gnome-power-manager.
Press Ctrl+Alt + F2 and login, then type:
```
sudo aptitude install gnome-power-manager
sudo reboot
```

---

### Post by nepmit on 2008-07-21
> **sisco311 said:**
> Try to reinstall gnome-power-manager.
Press Ctrl+Alt + F2 and login, then type:
```
sudo aptitude install gnome-power-manager
sudo reboot
```

Thanks for your reply.Tried that, shut down the display and I have to reboot. I haven't been able to get the terminal at all. The only typing I can do is in the recovery mode.For some reason I'm not able to retrieve anything from synaptic or the repositories.( Yes they were all active.) 
Still hopeful.

---

### Post by Potatoj316 on 2008-07-21
did you try that command in recovery mode?

---

### Post by sisco311 on 2008-07-21
try to start the network in recovery mode:
```
/etc/init.d/networking start
```

---

### Post by nepmit on 2008-07-21
> **sisco311 said:**
> try to start the network in recovery mode:
```
/etc/init.d/networking start
```

Thanks again. Yes, I tried Aptitude in the recovery mode after your first reply, had already tried apt-get to re install. Thats when I get fail to fetch. As for starting the network in recovery "command not found", not the 
exact phrase.

---

### Post by nepmit on 2008-07-21
> **Potatoj316 said:**
> did you try that command in recovery mode?

Yes. I had already tried with apt-get.That's when I get failed to fetch using both. Sorry for delay,my ISP has been down.

---

### Post by nepmit on 2008-07-21
> **sisco311 said:**
> try to start the network in recovery mode:
```
/etc/init.d/networking start
```

Tried this, no luck "no such command" not the exact pharse.

---

