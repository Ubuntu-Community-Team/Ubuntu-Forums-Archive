---
title: "system&gt;administrator&gt; synaptic package manager in ubuntu 12.04"
date: 2012-11-22
forum: New to Ubuntu
---

### Post by sanjibarpi on 2012-11-22
i am using ubuntu 12.04 version. But I can not open the system>administrator> synaptic package manager. please help me.

---

### Post by coffeecat on 2012-11-22
Two things. Synaptic does not come in a default install of 12.04 so if you want it you will need to install it first using Software Centre.

Second:

> **sanjibarpi said:**
> But I can not open the system>administrator> synaptic package manager.

It sounds as though you are describing the old classic gnome desktop. 12.04 comes with the Unity desktop but you can install others. What desktop are you using?

---

### Post by dniMretsaM on 2012-11-22
> **sanjibarpi said:**
> i am using ubuntu 2.04 version. But I can not open the system>administrator> synaptic package manager. please help me.

Synaptic was dropped in 11.10. You'll have to install it (or just use [FONT=Courier New]apt-get[/FONT] all the time instead):
```
sudo apt-get install synaptic
```

---

### Post by sanjibarpi on 2012-11-22
> **sanjibarpi said:**
> i am using ubuntu 12.04 version. But I can not open the system>administrator> synaptic package manager. please help me.
i am using ubuntu 12.04 version. But I can not open the system>administrator> synaptic package manager. please help me.

---

### Post by sanjibarpi on 2012-11-22
if i want to run a fortran programme initiated by a .bash file. what package  I need to install

---

### Post by dniMretsaM on 2012-11-23
> **sanjibarpi said:**
> i am using ubuntu 12.04 version. But I can not open the system>administrator> synaptic package manager. please help me.

Did you try my suggestion? Also, System -> Administrator -> Synaptic won't exist since that's the GNOME 2 menus. You'll have to launch it through the dash (if you're using Unity, which is the default desktop on Ubuntu 12.04).

---

