---
title: "system config command ..?"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by adym3333 on 2012-11-18
I want to know that how can I see my system configuration like RAM,hard drive etc . through CLI and GUI .....??:confused:

---

### Post by The Cog on 2012-11-18
Command prompt: ```
lshw | less
``` or for even more detail:
```
sudo -i
lshw | less
exit

```
I don't know of a GUI equivalent.

---

### Post by MG&amp;TL on 2012-11-18
GUI: multiple places, depending on DE, version, preferences...the point of a GUI is that you can find them. :)

CLI: (these should cover most things):

Generic hardware:
```
lshw
```

PCI(e) hardware:
```
lspci
```

USB hardware:
```
lsusb
```

CPU information:
```
lscpu
```

Memory (total/free):
```
free
```

GPU information/capabilities, OpenGL capabilities.
```
glxinfo
```

---

