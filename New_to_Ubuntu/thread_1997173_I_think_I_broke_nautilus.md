---
title: "I think I broke nautilus"
date: 2012-06-04
forum: New to Ubuntu
---

### Post by IAmTheAnswer on 2012-06-04
My computer decided to stop searching for applications in Unity and one of the solutions was to reset nautilus.  I found [this]("http://ubuntuforums.org/showthread.php?t=878606") answer (post #6).  Now I cannot login (it just kicks me back to the login screen) and there are no options for Unity or Unity 2D under the little icon in the login menu.  I tried that solutions again, but nothing happened.

What have I done and how can I fix this?

---

### Post by NikTh on 2012-06-04
Hi , 
The fist option if unity stops to respond is ```
unity --reset
``` from terminal . 

I don't know , i am not sure if you purged important packages or broke them. 

try the recovery console and "Dpkg - Repair broken packages" option to see if fix something. 
Thanks

---

### Post by IAmTheAnswer on 2012-06-04
> **NikTh said:**
> Hi , 
The fist option if unity stops to respond is ```
unity --reset
``` from terminal . 

I don't know , i am not sure if you purged important packages or broke them. 

try the recovery console and "Dpkg - Repair broken packages" option to see if fix something. 
Thanks

I tried both.  Resetting unity did nothing and the Dpkg thing said there was nothing messed up.

---

### Post by NikTh on 2012-06-05
Hi , 
try this
```
sudo apt-get install --reinstall ubuntu-minimal ubuntu-mono nautilus nautilus-share nautilus-sendto
```
Thanks

---

### Post by IAmTheAnswer on 2012-06-05
> **NikTh said:**
> Hi , 
try this
```
sudo apt-get install --reinstall ubuntu-minimal ubuntu-mono nautilus nautilus-share nautilus-sendto
```
Thanks

It didn't work.

This is killing me.

---

### Post by NikTh on 2012-06-06
Hi , 
try to reinstall Unity ... 
```
sudo apt-get install --reinstall unity unity-common unity-2d unity-2d-common unity-greeter
```
Thanks

---

