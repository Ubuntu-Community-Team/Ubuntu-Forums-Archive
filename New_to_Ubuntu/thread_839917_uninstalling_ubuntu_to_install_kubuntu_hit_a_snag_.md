---
title: "uninstalling ubuntu to install kubuntu hit a snag help plz"
date: 2008-06-24
forum: New to Ubuntu
---

### Post by dvlmn on 2008-06-24
ok so i was trying to uninstall ubuntu and i screwed up and forgot to uninstall the memtest86+.bin file so i dont have the kubuntu or ubuntu discs with me but i want it to be empty so when i get home tomorrow i can just load on kubuntu i have grub on still is there a way to erase it in there? if not what should i do?

---

### Post by bluepowder7 on 2008-06-24
1 - if you just want to change from ubuntu to kubuntu, you don't need to uninstall anything.  just load up the kde package and go.

2 - not sure about totally erasing grub and having it redone.  i think the entire grub files are in the /boot directory (or partition, depending on how you set it up), so you could just make the installer format it.

---

### Post by JoshuaRL on 2008-06-24
If you want kubuntu, there is one easy (although long) step to install it:
```

sudo aptitude install kubuntu-desktop

```
It will take a while, since that is a metapackage that installs a bunch of other packages so you get the full "kubuntu" experience.  After that, change the session at login to get into Kubuntu.

Does that work?

---

### Post by dvlmn on 2008-06-30
ok so apparently my so called friend decided to try and help me out he uninstalled all but the memtest86.bin or whatever so when i put in kubuntu or ubuntu it does nothing... is there a way to finish uninstalling all of it through grub or something since now all it wants to do is boot into the memtest and test my system.... im kinda stuck here and dont want to pay some crazy amount for a computer shop to do this and im still learning grub and linux... so please help

---

### Post by bobdob20 on 2008-06-30
If you want to install kubuntu, just insert the kubuntu cd and set bios to boot from cd.

---

