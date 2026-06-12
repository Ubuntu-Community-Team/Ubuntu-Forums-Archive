---
title: "trying to remove some dependencies..."
date: 2006-02-16
forum: Packaging and Compiling Programs
---

### Post by orlox on 2006-02-16
I've been trying to get a .deb package working correctly (gnomeboyadvance, a frontend for a gameboyadvance emulator), but on installation it claims that the python version must be 2.3.something...However, it works with no problems. Well, except for one, every time i do something in synaptic, it removes the package because it considers it as "broken". I tried to modify the package by modifying the dependencies and making the deb again from a .tgz file with alien. But the installation (although it does not claim for dependencies), doesn't generate the nice gnomeboyadvance icon to acces from the desktop menu...
So, im looking for an answer. If anyone can tell me how to succesfully modify the .deb file, how to stop synaptic from erasing it, or an alternative solution for this, i'd aprecciate it...

---

### Post by gord on 2006-02-20
```
sudo apt-get install python2.3
```

then remove the .deb file and re-install it

---

