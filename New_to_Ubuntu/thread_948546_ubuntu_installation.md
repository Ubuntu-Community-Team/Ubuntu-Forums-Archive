---
title: "ubuntu installation"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by iKonaK on 2008-10-15
is there a way to find out since when a GNU/Linux or ubuntu is installed on a machine ?
just curious.....:)

---

### Post by Paul41 on 2008-10-15
Can you clarify what you are asking? I'm not sure what you are looking for.

---

### Post by iKonaK on 2008-10-15
i wanna find out for since when i'm using this install...a specific date, something like the "uptime" command...

---

### Post by Paul41 on 2008-10-15
I don't know how much this helps and I'm not at my Ubuntu machine so I can't try it but it my help some. It wouldn't be perfect for sure though.

[http://ubuntuforums.org/showthread.php?t=520810](http://ubuntuforums.org/showthread.php?t=520810)

---

### Post by Kevbert on 2008-10-15
You can find out when the kernel was installed or most recently updated via
```
cd /boot
ls -l
```
All the files are timestamped.

---

### Post by iKonaK on 2008-10-15
thanks 4 replying but that didn't help me 2 much,
4 one example there are folders that are dated before the actual release of hardy and i know i installed at least 2 weeks later.
my best guess is the date of "/lost+found" and the date of "/cdrom"  witch were both the same, 12 may....if anyone know a better way please enlighten  me  ;)

---

