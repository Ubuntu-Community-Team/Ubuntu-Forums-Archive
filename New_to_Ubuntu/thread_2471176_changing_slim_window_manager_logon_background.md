---
title: "changing slim window manager logon background"
date: 2022-01-22
forum: New to Ubuntu
---

### Post by rburkartjo on 2022-01-22
running ubuntu 21.10



is there an easy way i can use any jpg image . and if so how/tks

---

### Post by KBar on 2022-01-22
[https://wiki.archlinux.org/title/SLiM#Custom_background](https://wiki.archlinux.org/title/SLiM#Custom_background)
> **Custom background**

 SLiM is hard-coded to load background.png or background.jpg (in that order) from your theme directory. Simply overwrite the appropriate file 
 ```
# cp /path/to/new_background.jpg /usr/share/slim/themes/*<theme_name>*/background.jpg

```

---

### Post by rburkartjo on 2022-01-22
kb tks worked great

---

