---
title: "Script Simulation"
date: 2013-02-22
forum: New to Ubuntu
---

### Post by thedawg on 2013-02-22
Hi there,

is there a way that I can run a simulation of an Installation-Script to check it for bugs, similar to the simulation of pkgsync -s ?


:)

---

### Post by Sealbhach on 2013-02-22
Yes, it's much the same.

sudo apt-get -s install package

will tell you what it's going to do (or remove).

.

---

### Post by thedawg on 2013-02-22
Now I remember it, I start the script with the "source" command, same here as well ?

Couldn't find anything on that matter...

---

### Post by schragge on 2013-02-27
Yes, it's the same. The option *-s* works with all apt-get actions.

BTW, I wouldn't call apt-get *script*:
```

[color=green]$[/color]file `which apt-get`
/usr/bin/apt-get: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.26, BuildID[sha1]=0x135dafd8484e618f58d0b4cbf170cad58a534c62, stripped 

```

---

