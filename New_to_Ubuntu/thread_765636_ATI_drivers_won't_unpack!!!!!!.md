---
title: "ATI drivers won't unpack!!!!!!"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Universal344 on 2008-04-24
I have downloaded ATI drivers and found instructions.  I tried three different commands in the terminal to unpack it and not one worked!!!!:mad:

These are the commands and there errors:

sudo sh ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu/gutsy
error: sh: Can't open ati-driver-installer-8-4-x86.x86_64.run

 sudo ./ati-driver-installer-8-4-x86.x86_64.run --buildpkg Ubuntu --autopkg 
error: sudo: ./ati-driver-installer-8-4-x86.x86_64.run: command not found

 $ bash ati-driver-installer-8.42.3-x86.x86_64.run --extract ati-driver
error: bash: $: command not found

In the directions he told me to check that universe and multiverse were enabled.  How do I check for this?

PLEASE HELP!!!!

---

### Post by newb1e on 2008-04-24
you need to make it executable first:
```
chmod +x filename
```
then run it with sudo
```
sudo ./filename
```

---

### Post by sdowney717 on 2008-04-24
you can also use the gui for this, right click properties, permissions,  and check the box to make it executable.

---

