---
title: "enlightenment not found in GDM3 selection list"
date: 2021-06-04
forum: New to Ubuntu
---

### Post by maketopsite on 2021-06-04
Ubuntu 20.04 LTS.

enlightenment was installed according to [https://help.ubuntu.com/community/Enlightenment](https://help.ubuntu.com/community/Enlightenment)

Is this please right course of action ?

---

### Post by dddman on 2021-06-04
The last and newest E download I see in the link is Ubuntu 18.04; this link has not been updated for three years.  I wouldn't expect it to work on 20.04.

---

### Post by Frogs Hair on 2021-06-04
I have used the repository version of enlightenment 0.23 on Ubuntu Budgie which doesn't use GDM3. There used to be a session menu in Gnome 3+ on the top right you could try logging out from there and see if there is Enlightenment option. 

[https://www.omgubuntu.co.uk/2020/05/enlightenment-0-24](https://www.omgubuntu.co.uk/2020/05/enlightenment-0-24)

---

### Post by maketopsite on 2021-06-08
> **Frogs Hair said:**
> I have used the repository version of enlightenment 0.23 on Ubuntu Budgie which doesn't use GDM3. There used to be a session menu in Gnome 3+ on the top right you could try logging out from there and see if there is Enlightenment option. 

[https://www.omgubuntu.co.uk/2020/05/enlightenment-0-24](https://www.omgubuntu.co.uk/2020/05/enlightenment-0-24)

Do you know please which Display Manager is used on that machine with Ubuntu Budgie ?

---

### Post by deadflowr on 2021-06-08
> **maketopsite said:**
> Do you know please which Display Manager is used on that machine with Ubuntu Budgie ?

Lightdm.

---

### Post by maketopsite on 2021-06-08
> **deadflowr said:**
> Lightdm.

thank you.

---

### Post by maketopsite on 2021-06-09
enlightenment is visible and accessible in lightdm. Unfortunately, enlightenment runs Xorg under root account.

---

### Post by similar2 on 2021-06-15
Easy & safe way to install Enlightenment on Ubuntu :smile:
[https://github.com/batden/esteem](https://github.com/batden/esteem)

---

### Post by grahammechanical on 2021-06-15
The Enlightenment team have yet to provided a Wayland based compositor for the Enlightenment desktop environment.

> Work is currently underway to land a complete Wayland compositor  (stand-alone, no X11 needed) into the master branch of Enlightenment. At  this stage, we are undergoing heavy testing and resolving any issues.  We will definitely need to extend Wayland protocol to make a fully  functioning desktop or mobile environment, but what we do have (based on  the existing wayland protocol) is quite usable.

[https://www.enlightenment.org/about-wayland](https://www.enlightenment.org/about-wayland)

Regards

---

