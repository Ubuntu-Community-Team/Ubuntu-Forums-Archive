---
title: "How do i install nvidia drivers?"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by luvlinux on 2008-07-05
Hi! I am new to Ubuntu and i cant figure out how to install the nvidia drivers for my 9600gt card. How can i do that? I am currently running in 800x600 so it's kinda annoying :P

---

### Post by damis648 on 2008-07-05
On the top panel: System>Administration>Hardware Drivers and make a check next to your card.

---

### Post by drs305 on 2008-07-05
If the above doesn't work for you, you can install the gui-based envyng-gtk.
It will get the nvidia driver and install it. I've found that the ones I've gotten from Envy were newer versions than what was in the normal repository (at least when I did it). 

To install:
```
sudo aptitude install envyng-gtk
```

To run it:
System Tools, EnvyNG

There will also be the System, Administration, Nvidia X Server Settings. If envygn-gtk doesn't install it, it's available with:
```
sudo aptitude install nvidia-settings
```

---

### Post by sdennie on 2008-07-05
I believe for that card you will have to manually install the drivers.  This thread has helped many people: [http://ubuntuforums.org/showthread.php?t=850632](http://ubuntuforums.org/showthread.php?t=850632)

---

### Post by luvlinux on 2008-07-05
My card doesn't show up

---

### Post by aktiwers on 2008-07-05
If you wanna try install manually, this should work fine for you:
[http://ubuntuforums.org/showpost.php?p=5309952&postcount=6](http://ubuntuforums.org/showpost.php?p=5309952&postcount=6)

---

### Post by luvlinux on 2008-07-05
i did what you to me drs305 and now my screen is totally messed up. i can only see half of it and the rest is black and green. What should i do?

---

### Post by drs305 on 2008-07-05
> **luvlinux said:**
> My card doesn't show up

I don't know if this was directed at my post. EnvyNG installed version 173.14.05. The following  [URL="http://ge.ubuntuforums.com/showthread.php?t=810661"]post
[/URL] says that this release supports, among others:
```
o GeForce 9800 GX2
o GeForce 9800 GTX
o GeForce 9600 GT
o GeForce 9600 GSO
o GeForce 9600 GS

```

If you installed envyng and it doesn't show this version of drivers, perhaps you need to run an update or were looking at Envy's ATI list. I don't have any special repositories except medibuntu and the hardy-updates enabled.

---

### Post by aktiwers on 2008-07-05
I would try Envy first, and if it fails, then go for manual install

---

### Post by TheTrlak on 2008-07-06
problem is for the absolute newest cards neither the manual or the envy works, and even if envy does work it has mixed results, sometimes with crashes or lag. So depends on car and rig I suppose.

---

### Post by luvlinux on 2008-07-06
But i can only see my upper half of the screen so its kinda hard to do anything!
[picture](http://bildr.no/view/223201)

---

### Post by Huss on 2008-07-07
Envy made it easy for me. Thanks!

---

