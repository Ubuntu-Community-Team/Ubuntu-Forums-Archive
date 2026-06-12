---
title: "Remove Xorg"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by walkingthecow on 2008-09-30
Hey all,

I have just installed Ubuntu and don't really need a GUI. How do I just remove xorg and all X apps entirely from my machine? I am only using this machine for development. I know Ubuntu uses apt-get, like Debian, but I am more of a FreeBSD guy... so, no idea how to do this one.

---

### Post by bufsabre666 on 2008-09-30
pres ctrl alt f2

then 
```
sudo apt-get purge ubuntu-destop && sudo restart
```

i dont suggest removing xorg considering thats where your keyboard settings are too

---

### Post by walkingthecow on 2008-09-30
Well, I don't need a desktop, so what would you suggest I do? I don't need all the bloat of xorg and all the apps installed with xorg either. I just want my command line, and that is all.

---

### Post by kerry_s on 2008-09-30
> **bufsabre666 said:**
> pres ctrl alt f2

then 
```
sudo apt-get purge ubuntu-destop && sudo restart
```

i dont suggest removing xorg considering thats where your keyboard settings are too

that won't do nothing ubuntu-desktop is just a meta package.

---

### Post by kerry_s on 2008-09-30
> **walkingthecow said:**
> Hey all,

I have just installed Ubuntu and don't really need a GUI. How do I just remove xorg and all X apps entirely from my machine? I am only using this machine for development. I know Ubuntu uses apt-get, like Debian, but I am more of a FreeBSD guy... so, no idea how to do this one.

you know you can just do a command line install, it would be a lot easier than trying to take things out when there's already so much tied together.

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

go down to "Install an Ubuntu command-line system"

---

### Post by walkingthecow on 2008-09-30
Ah, thank you! It'll be nice to have Linux back to the way it is supposed to be, not some Windows Desktop environment wanna-be.

---

### Post by MrFSL on 2008-09-30
Seriously. Just install the server version. Its slim and trim.

---

### Post by rybaxs on 2008-09-30
wer can i get the server version? ive downloaded the server version but its like hardy ubuntu 8.04. is the server version GUI great?

---

### Post by aeiah on 2008-09-30
the server version dosent have a windows evironment or desktop manager like gnome, xfce or kde. it isnt the same as a commandline version of ubuntu though in so far as it has the server package installed: apache, mysql etc

---

### Post by hyper_ch on 2008-09-30
download it from ubuntu.com --> Select server edition: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

