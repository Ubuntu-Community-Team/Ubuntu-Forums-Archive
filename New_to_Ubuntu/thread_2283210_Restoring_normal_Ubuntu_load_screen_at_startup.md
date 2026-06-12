---
title: "Restoring normal Ubuntu load screen at startup?"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by Cleaver on 2015-06-20
Very minor thing here, but since I installed lubuntu-desktop it now loads with a Lubuntu screen before taking me to the desktop. Curious about how I might restore the default Ubuntu one. Thanks!

---

### Post by grahammechanical on 2015-06-20
A very minor thing? I do not think so. You can try re-installing ubuntu-desktop. Based upon my one experiment with alternative desktops I have come to the conclusion that they do not play nicely together. I ended up re-installing Ubuntu itself as a way of getting rid of the mess.

Regards.

---

### Post by Cleaver on 2015-06-20
I just mean it's minor in terms of any real damage its done to my system/apparent harm to functionality. It is odd, though. I'm only asking this because it's the default and I don't know if that might make it a different matter than merely uninstalling, say, xubuntu-desktop, but: What harm could reinstalling ubuntu-desktop do? I'm guessing none, and that it'd just return to how it was before at the worst.

---

### Post by CantankRus on 2015-06-21
Is it the plymouth loading screen or the actual greeter where you log on?

---

### Post by RobGoss on 2015-06-21
I did experience this a few weeks back while I was working on a few things with my system, I always keep a clone of my system I just pop that clone in and restored it and no more problems

---

### Post by yetimon_64 on 2015-06-21
> **Cleaver said:**
> Very minor thing here, but since I installed lubuntu-desktop it now loads with a Lubuntu screen before taking me to the desktop. ...

_*If*_ that is the plymouth boot screen for lubuntu you are talking about, the "update-alternatives" command should get you back to the ubuntu splash screen.

In a terminal (Ctrl + Alt + T, in Unity will open the terminal) try,
```
sudo update-alternatives --config default.plymouth 
``` This will give you a selection of splash screens to choose from, enter the number for the ubuntu-logo.plymouth option and press "Enter". Once that command is done you will need to update "initramfs" as the plymouth splash is used before the OS is loaded.
The command,
```
sudo update-initramfs -u
```

If this fixes the boot screen and you have multiple kernels affected then issue the update-initramfs command for all kernels (but only if needed)
```
sudo update-initramfs -u -k all
```

Note when entering your sudo password in terminal that no feedback is given, If you type it in correctly it will still work even though you can't see it going in (a security measure). Good luck with the repairs, yeti.

---

