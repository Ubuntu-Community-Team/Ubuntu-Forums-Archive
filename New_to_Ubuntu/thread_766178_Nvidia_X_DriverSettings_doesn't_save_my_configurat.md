---
title: "Nvidia X DriverSettings doesn't save my configuration"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by gaffurabi on 2008-04-25
[FONT="Georgia"]as you can see in the snapshot X says there is a backup problem and doesnt save my nvidia x driver settings, therefore every time ubuntu starts i have to adjust them manually. any ideas?[/FONT] :confused:

---

### Post by howlingmadhowie on 2008-04-25
this is because /etc/X11 can only be written to by root. however, don't change the rights for the folder, because the nvidia utility will save a new xorg.conf which (on my system at least) is incompatible with the new X11 version on 8.04. this means the desktop won't start. 

at the moment, the only thing i can suggest is to change the resolution every time you log in (or go out and spend hard earned cash on a monitor X11 recognises). but watch this space, because i'm sure an answer will be found soon.

---

### Post by DukeNuke2 on 2008-04-25
open a terminal and enter:

sudo nvidia-settigs


make your modifications and save it to xorg.conf. this works fine for me...

---

### Post by gaffurabi on 2008-07-21
[COLOR="Navy"]I've changed my monitor from CRT to LCD.
damn nvidia-settings even when I run them as sudo dont save my desired resolution.
any ideas why?[/COLOR]

---

### Post by nickftm on 2008-07-21
You have to do this:

```
gksudo nvidia-settings
```

---

### Post by bodhi.zazen on 2008-07-21
As pointed out by nickftm, you should use gksu with graphical applications running as root.

gksu is a symlink to gksudo.

Run:

```
gksu nvidia-settings
```

Set your desired resolution.

Hit the "save settings" button.

---

### Post by gaffurabi on 2008-08-19
> **gaffurabi said:**
> [COLOR="Navy"]I've changed my monitor from CRT to LCD.
damn nvidia-settings even when I run them as sudo (or gksu) dont save my desired resolution.
any ideas why?[/COLOR]
[COLOR="Red"][B]
the issue still continues. please help![/B][/COLOR]:confused:

---

### Post by gaffurabi on 2008-11-13
well, when i re-installed ubuntu the problem disappeared. monitor change in ubuntu might get problematic :(

---

