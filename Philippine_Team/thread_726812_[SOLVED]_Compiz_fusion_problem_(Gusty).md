---
title: "[SOLVED] Compiz fusion problem (Gusty)"
date: 2008-03-17
forum: Philippine Team
---

### Post by Pedro0727 on 2008-03-17
Need help i got error when enabling compiz fusion 

msg error(The Composite extension is not available)

---

### Post by Thanoulis on 2008-03-17
You'll have to enable it in your /etc/X11/xorg.conf :

```
Section "Extensions"
Option      "Composite" "Enable"
EndSection

```

---

### Post by februarius on 2008-03-17
na try mo nba i install ung driver ng video card mo

---

### Post by Nhatz on 2008-03-17
para mas madali install mo yung driver ng video card mo using envy...
Astig! :guitar:

---

### Post by dodimar on 2008-03-17
saan ba yung envy.. nasa repo ba yun?

---

### Post by Nhatz on 2008-03-17
dodimar.... DL mo nlang dito [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) yung .deb file ng envy. hehehehe :)
Astig! :guitar:

---

### Post by Pedro0727 on 2008-03-18
ok n po mga sir. solved n po tnx po s help.. 

install ko ung xserver, xorg and other addins para gumana..

---

