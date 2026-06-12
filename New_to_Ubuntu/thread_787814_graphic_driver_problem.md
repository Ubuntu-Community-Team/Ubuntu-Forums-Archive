---
title: "graphic driver problem"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by Abu Noor-Eddin on 2008-05-09
I am new to linux and ubuntu. 

I was having a problem that I thought it is related to resolution problems. I uninstall all graphic drivers :) (so stupid). Now Ubuntu cannot start X window. 

I tried to replace xorg.conf with my backup one but the problem still exist. 

What should I do?

Thanks in advance.

---

### Post by Biggy on 2008-05-09
System > Administration >Hardware Drivers and check Device Drvers

---

### Post by Canis familiaris on 2008-05-09
Press Ctrl+Alt+f1 to go to tty0.
Login and in the command line type:

```
sudo dpkg-reconfigure xserver-xorg
```

Set your video driver as vesa and choose the rest of settings according to your configuration.
Restart.
And you can run GUI.

---

### Post by Abu Noor-Eddin on 2008-05-09
> **Anurag_panda said:**
> Press Ctrl+Alt+f1 to go to tty0.
Login and in the command line type:

```
sudo dpkg-reconfigure xserver-xorg
```

Set your video driver as vesa and choose the rest of settings according to your configuration.
Restart.
And you can run GUI.

Thank you. It works.

---

