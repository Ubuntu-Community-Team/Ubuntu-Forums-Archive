---
title: "No return from terminal mode"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by ingeva on 2008-08-25
If I use for instance Ctrl+Alt+F1 to go to terminal mode, there's no return.

When I press Ctrl+Alt+F7 the screen goes into graphics mode but is completely black. If I try to go back to terminal mode nothing happens.
Ctrl+Alt+Backspace doesn't work.

Only the power button does (there's no reset on this computer).

I have a Dell Vostro 400 with Nvidia graphics. I run 8.04.1 Hardy Heron.

Any ideas?

---

### Post by Pro-reason on 2008-08-27
If you are running Compiz, try disabling it.

---

### Post by ingeva on 2008-08-27
> **Pro-reason said:**
> If you are running Compiz, try disabling it.

Probably not. I've read something about it, but not enough to know what it is. :)

Tried to run it and got this:

```
inge@Pantera:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:9588 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

So I guess that's not it? :)

---

### Post by mcduck on 2008-08-27
Do you have the "desktop effects" enabled? That's Compiz. ;)

Anyway, next time that happens you could try hitting Ctrl-Alt-backspace. That will reload X, at least saving you from rebooting..

---

### Post by ingeva on 2008-08-27
> **mcduck said:**
> Do you have the "desktop effects" enabled? That's Compiz. ;)

Anyway, next time that happens you could try hitting Ctrl-Alt-backspace. That will reload X, at least saving you from rebooting..

No, I don't want any "effects". They are just processor-consuming gimmicks.

I'll try CTRL+ALT+Backspace next time. Right now I'm in a hurry! :)

Thanks!

---

### Post by Nythain on 2008-08-27
> **mcduck said:**
> Do you have the "desktop effects" enabled? That's Compiz. ;)

Anyway, next time that happens you could try hitting Ctrl-Alt-backspace. That will reload X, at least saving you from rebooting..
control alt backspace wont work, as the original poster mentioned, and as i've encountered.

whats happening here is more than likely an xserver lockup/crash for god knows whatever reason... on one install it happend to me every time i switched to tty and back, on another install it only happend about one out of every 5 switches, and on most installs, its never happend at all.

i wish i could tell you more. you could try looking in your xorg logs, but you more than likely arent going to find much, and yeah, i've found the only real solution is a damned annoying power kill :(

---

