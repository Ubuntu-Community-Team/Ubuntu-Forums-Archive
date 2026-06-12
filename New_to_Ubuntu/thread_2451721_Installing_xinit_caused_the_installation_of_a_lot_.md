---
title: "Installing xinit caused the installation of a lot of packages!!!"
date: 2020-10-09
forum: New to Ubuntu
---

### Post by automate-stuff on 2020-10-09
I ran:

```
sudo apt install xserver-xorg
sudo apt install xinit
```

but the second line installed the gnome desktop and everything else....I am now booting into gnome!!

Where did I make a mistake  ?

---

### Post by automate-stuff on 2020-10-09
Doing: 

```
sudo apt install -no-install-recommends xinit
```


fixed the issue.

---

