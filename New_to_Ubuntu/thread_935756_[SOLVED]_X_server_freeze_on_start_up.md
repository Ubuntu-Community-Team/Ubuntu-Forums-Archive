---
title: "[SOLVED] X server freeze on start up?"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by LastWho on 2008-10-02
Hi
My x server freezes on start up after logging in, with a white window, and 2 empty panels!! Alt-F2, or Ctrl-L (to browse) do not work... only keyboard shortcuts that work are the Ctrl-Alt-F1...F7

when i try the Ctrl-Alt-Bksp and i log in again the screen freeze on the orange page

please help
thx

---

### Post by WWSmith36 on 2008-10-02
This might be a problem with xorg/video drivers/compiz.  You might be able to get to a regular desktop by doing.

ALT-F2

You won´t see anything but type

```
metacity --replace
```

If this does not work.  At gdm login choose options and load failsafe session.

Hope this helps

---

### Post by LastWho on 2008-10-02
thank you WWSmith

i tried what u told me but unfortunatly it didn't work

[INDENT] - Alt-F2: metacity --replace  doesn't work
- i tried to do it on tty1 : 
i recieved that error: cannot display X server

so i used this command: [export DISPLAY=:0]("http://forum.compiz-fusion.org/showthread.php?t=744")
then metacity --replace --> Enter .. no error message, but when i get back to x server, nothing changes

i tried the failsafe session after reboot: the only change was that the panel were full again (Applications, Places, System, trash... ) but i couldn't access to any by clicking or shortcuts

[/INDENT]waiting for your help plz 
thx

---

### Post by Ryadt on 2008-10-02
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by rybaxs on 2008-10-02
> **WWSmith36 said:**
> This might be a problem with xorg/video drivers/compiz.  You might be able to get to a regular desktop by doing.

ALT-F2

You won´t see anything but type

```
metacity --replace
```

If this does not work.  At gdm login choose options and load failsafe session.

Hope this helps


what is the effect of metacity? I've tested then it refresh myscreen. does that bash command affects something?

---

### Post by LastWho on 2008-10-02
> **Ryadt said:**
> Try ```
sudo dpkg-reconfigure xserver-xorg
```

i tried this, my screen looks ugly, but i got back the icons on the panels.. But nothing is clickable, the shortcuts don't work also..
still the only thing i can access to is the "tty"

any other suggestions please?
thx

ps: just after i tried also this:

> sudo apt-get install --reinstall xserver-xorg
it gave me this: 
> Reinstallation of xserver-xorg is not possible, it cannot be downloaded.
0 upgraded, 0 newly installed, 0 to remove

---

### Post by Ryadt on 2008-10-02
Try```
sudo apt-get install ubuntu-desktop
```

---

### Post by LastWho on 2008-10-02
thank you so much Ryadt!! it works now!!
thx


> **Ryadt said:**
> Try```
sudo apt-get install ubuntu-desktop
```


> The following extra packages will be installed:
  pulseaudio-esound-compat totem
Recommended packages:
  totem-plugins-extra
The following packages will be REMOVED:
  esound
The following NEW packages will be installed:
  pulseaudio-esound-compat totem ubuntu-desktop
0 upgraded, 3 newly installed, 1 to remove and 1 not upgraded.
Need to get 66.7kB/95.2kB of archives.
After this operation, 201kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  pulseaudio-esound-compat
Install these packages without verification [y/N]? Y
...

i ve a question please: was this package: "ubuntu-desktop" the cause of my problem??

---

### Post by Ryadt on 2008-10-02
It seems as if it got corrupted.

---

### Post by Ryadt on 2008-10-02
Please mark the thread as solved...:popcorn::KS

---

