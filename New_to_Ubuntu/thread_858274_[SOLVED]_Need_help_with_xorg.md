---
title: "[SOLVED] Need help with xorg"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-13
Hi ubuntuers.
I have a little problem editing xorg.
Here it is:
> diastopher@diastopher-desktop:~$ sudo gedit /etc/X11/xorg.conf
No protocol specified
cannot open display: 
Run 'gedit --help' to see a full list of available command line options.

Thanks.

---

### Post by unutbu on 2008-07-13
Are you logged in to diastopher-desktop directly or through ssh perhaps?

---

### Post by Bachstelze on 2008-07-13
You **must** use [FONT="Courier New"]gksudo[/FONT] instead of [FONT="Courier New"]sudo[/FONT] for graphical apps.

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by cristo-father on 2008-07-26
Problem solved.

---

