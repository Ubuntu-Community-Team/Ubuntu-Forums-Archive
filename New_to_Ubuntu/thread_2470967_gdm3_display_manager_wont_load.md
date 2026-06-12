---
title: "gdm3 display manager wont load"
date: 2022-01-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2022-01-18
i upgraded to ubuntu 21.10 and it messed up the gdm3 display manger. all i get is a white screen with the message 'oh something went wrong'. i switched to other display managers and they will let me login. tried to reinstall just gdm3 display manager and that didnt work. should i try this


sudo apt-get autoremove gdm3
[sudo] password for ray: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following packages will be REMOVED:
  gdm3 ubuntu-desktop ubuntu-desktop-minimal
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 2,077 kB disk space will be freed.
Do you want to continue? [Y/n] 

 and then reinstall the above. or try something else

tks

---

### Post by tea for one on 2022-01-18
> **rburkartjo said:**
>  or try something else

Have you tried to re-configure gdm3?
```
sudo dpkg-reconfigure gdm3
```

---

### Post by rburkartjo on 2022-01-18
tea yes and do luck

---

### Post by tea for one on 2022-01-18
Perhaps boot into [COLOR="#0000FF"]recovery mode[/COLOR] and try the re-configure command again?

---

### Post by rburkartjo on 2022-01-18
tea also tried that. no luck

---

### Post by GhX6GZMB on 2022-01-18
Why would you use gdm3 on Lubuntu?

---

### Post by tea for one on 2022-01-18
> **ml9104 said:**
> Why would you use gdm3 on Lubuntu?

Very good point - I did not notice the tag but in post no.1:-
> **rburkartjo said:**
> i upgraded to [COLOR="#0000FF"]ubuntu 21.10[/COLOR] and it messed up the gdm3 display manger
I wonder if there are multiple Desktop Environments in play here?

---

