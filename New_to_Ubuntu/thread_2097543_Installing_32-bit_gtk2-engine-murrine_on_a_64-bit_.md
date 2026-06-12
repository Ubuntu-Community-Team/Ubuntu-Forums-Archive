---
title: "Installing 32-bit gtk2-engine-murrine on a 64-bit system"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2012-12-23
Hi, I'm not sure if I'm just missing something or not, but I can't figure out how to install the 32-bit version of gtk2-engines-murrine in Ubuntu 12.10 64-bit.  32-bit applications aren't capable of using the 64-bit engine that I have installed, which partially breaks desktop consistancy so I was hoping someone knew how to get this.

Thanks in advance for any advice/tips!

---

### Post by Cheesemill on 2012-12-23
Have you tried:
```
sudo apt-get install gtk2-engines-murrine:i386
```

---

### Post by Ozymandias_117 on 2012-12-23
Thank you very much, that was exactly what I was looking for.  I didn't realize I could append :i386 to request the 32-bit version.

---

