---
title: "Acer Laptop designed for Vista...want Ubuntu"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by chilliepierre on 2008-04-28
Please help me.  I tried to put on Ubuntu and it keeps crashing and telling me the video card isn't configured, etc.

Can you help me?  Please?

Can I not use this laptop with Ubuntu?  Do I have to use Vista?  I will be honest, I bought the laptop on Ebay without an OS for the sole purpose of using Linux.

Please assist.

---

### Post by SOULRiDER on 2008-04-28
What model is it?

---

### Post by chilliepierre on 2008-04-28
Acer 5520 ICW50
AMD Athlon 64 x2 Dual Core processor

Does this help?

Thanks!

---

### Post by Helios1276 on 2008-04-28
Whats your card?

---

### Post by chilliepierre on 2008-04-29
Nvidia GeForce 7000M

---

### Post by Boyohazard on 2008-04-29
Are you able to boot a Live CD at all?

---

### Post by chilliepierre on 2008-04-29
No I haven't been able to even run Ubuntu off the live cd.

---

### Post by FredB on 2008-04-29
I have nearly the same model. First verify you made a good burn of installation iso.

For the screen, it is normal. It will be fixed after installation.

After your install Hardy, go to System / Administration / Restricted Drivers menu.

Check for nvidia hardware. You'll get your driver installed. Reboot. After that, open a terminal, and enter :

```
sudo aptitude install nvidia-settings
```

After nvidia-settings is installed, just type again in the terminal :

```
sudo nvidia-settings
```

And you'll be able to select the right screen resolution.

---

### Post by chilliepierre on 2008-05-02
I can set the video to 1280 x 800, but then when I reboot it doesn't stay...how do I get it to stay put on the setting?

---

