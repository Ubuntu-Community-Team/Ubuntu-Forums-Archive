---
title: "[SOLVED] start terminal in specific folder"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by anthonie on 2008-11-26
Hi all,

I would like to have an option under my right mouse button to start a terminal in the specific folder that is selected at that moment. Anyone with pointers as to how to achieve just that? 

Regards,
Anthonie

---

### Post by Sealbhach on 2008-11-26
> **anthonie said:**
> Hi all,

I would like to have an option under my right mouse button to start a terminal in the specific folder that is selected at that moment. Anyone with pointers as to how to achieve just that? 

Regards,
Anthonie

Try:

```
sudo apt-get install nautilus-open-terminal 
```

This should do it.

.

---

### Post by binbash on 2008-11-26
above does the trick with gnome.With kde you can use yakuake open terminal in current folder(kde-look.org)

---

### Post by anthonie on 2008-11-26
It does do the trick and I suppose it does not get any easier than this...
However, for other people that use the info here, I did have to reboot for some reason before the option was available in my context-menu. Small price, though :D

---

### Post by binbash on 2008-11-26
only restart nautilus

---

### Post by anthonie on 2008-11-26
Tried that,Binbash, but to no reveil. Than I logged out and logged in, didn't do the trick either. Once I fully rebooted the terminal-option is there. Because it worked, I did not question it any further. However, I assume it's something on my machine that caused it.

---

