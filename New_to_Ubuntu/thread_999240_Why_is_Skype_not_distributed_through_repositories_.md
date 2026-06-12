---
title: "Why is Skype not distributed through repositories with automatic updates?"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by brucewagner on 2008-12-01
Why is Skype not distributed through repositories with automatic updates, like all other software is...?

---

### Post by funrider on 2008-12-01
coz it is not opensource

---

### Post by mikewhatever on 2008-12-01
Actually, skype is in Medibuntu, an unofficial Ubuntu repository.

---

### Post by plucky on 2008-12-01
And to add it see this [link](https://help.ubuntu.com/community/Medibuntu).

---

### Post by kostkon on 2008-12-01
You can use its official repository, if you want:
```
deb http://download.skype.com/linux/repos/debian/ stable non-free
```

---

### Post by linux_tech on 2008-12-01
Get Skype:
```
sudo apt-get install ia32-libs lib32asound2 libqt4-core libqt4-gui
```
```
wget -O skype-install.deb http://www.skype.com/go/getskype-linux-ubuntu
```

Install skype:
```
sudo dpkg -i --force-architecture skype-install.deb
```

---

