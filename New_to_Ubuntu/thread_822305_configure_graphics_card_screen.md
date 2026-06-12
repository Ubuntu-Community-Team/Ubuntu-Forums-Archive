---
title: "configure graphics card screen"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by ex-wirecutter on 2008-06-08
When I transferred my hard drive to a new PC I got a screen telling me it was in low graphics mode and asking me to re configure and listing graphics cards and monitors. How do I get this screen back if I want to try different settings please ?

---

### Post by Jookia on 2008-06-08
If you have an nvidia card, go to add/remove and install the nvidia card. Then there's system-> preferences -> screen resolution etc

---

### Post by didac on 2008-06-08
Or try 

```
sudo displayconfig-gtk
```

in a terminal.

Or try:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Abu_Dayya on 2008-06-08
paste the output of
```
lspci
``` so we can know what is your graphics card

---

### Post by ex-wirecutter on 2008-06-08
The card is a Radeon 8500 ,its working o.k. but not quite filling the screen on 1024X768 so was just going to try different settings like you can with Windows. Many thanks for your fast responses .

---

### Post by ex-wirecutter on 2008-06-08
Thanks a lot , that was EXACTLY what I wanted . Screen resolution now o.k.
Glad you guys are around .

---

