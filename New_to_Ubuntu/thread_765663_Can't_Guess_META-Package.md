---
title: "Can't Guess META-Package"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by comsparks on 2008-04-24
[SOLVED] I tried to do an upgrade using the update manager but when it finishes the second step I get the Can't Guess META-Package and the entire process aborts. It acts like I don't have the correct 7.10 version but I do. Any ideas? Thanks.

---

### Post by zvacet on 2008-04-24
```
  sudo apt-get install ubuntu-minimal ubuntu-standard 
```

and after that 

```
  sudo apt-get install ubuntu-desktop 
```

for KDE

```
sudo apt-get install kubuntu-desktop
```

for XFCE

```
sudo apt-get install xubuntu-desktop
```

I give you all options because I don´t know what are you using.

---

### Post by comsparks on 2008-04-24
Minimal and Standard states that I have the newest and Desktop loaded a couple of artwork packages but no 8.04.

---

### Post by zvacet on 2008-04-25
These packages are needed to perform upgrade.

---

### Post by comsparks on 2008-04-25
ZVACET, After I ran what you said I went back and ran the update again. It took all night and finished installing this morning. Thanks

---

### Post by zvacet on 2008-04-25
It is good to know you are back.

---

