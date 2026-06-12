---
title: "Wine not installing on 64bit ubuntu 12.10"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by SempronX2 on 2012-10-24
Wine won't install on my ubuntu. It worked fine on 12.04 but i did a fresh install and it dosn't work

---

### Post by danielbauwens on 2012-10-25
Hello, and welcome to the forums.

Do this:

```
CTRL-ALT-T
```
Then type:
```
sudo apt-get install wine
```

That should do it.

---

### Post by Albertint on 2012-10-25
I'm having this issue with 1.5.15 which won't even install on a partial upgrade I did after it uninstalled wine, saying it wasn't need anymore. I was thinking it'd be fine and I could return it back after the partial upgrade.

But it won't do it. It says the dependency "wine:" is not meant in Software Center, and in Synaptic it returns the line "Depends: wine1.5 but it is not going to be installed" when I just try selecting the wine package for installation.

Why is it doing this? :confused:

(PS: Xubuntu user)

UPDATE: A larger message comes up in the terminal:

The following packages have unmet dependencies:
 wine : Depends: wine1.5 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Albertint on 2012-10-26
Nevermind. Upgrading fully has alleviated things. Now onto fixing audio again... Nothing to worry about; I use ALSA, is all.

---

