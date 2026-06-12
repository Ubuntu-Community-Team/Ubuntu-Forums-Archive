---
title: "Lubuntu hangs dureing installation on powerpc"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by bblackbelt on 2012-09-29
Hello guys, I am trying to install lubuntu on a powerpc g4. I manage to start the installation process from a usb stick. 

The installation process hangs on 
[B]
Stopping anachronistic cron [ok][/B] 

and nothing happens.

How can I fix?

Please help

---

### Post by MG&amp;TL on 2012-09-29
Is that when you're shutting down?

That's a bug, I think. It's meant to display a message to remove your installation media, then it will shutdown, but if you have unusual graphics, it may fail. Just press your shutdown button until it powers off, then remove your stick and boot it.

---

### Post by bblackbelt on 2012-09-29
> **MG&TL said:**
> Is that when you're shutting down?

That's a bug, I think. It's meant to display a message to remove your installation media, then it will shutdown, but if you have unusual graphics, it may fail. Just press your shutdown button until it powers off, then remove your stick and boot it.

 no I am at the beginning of the installation process. I boot withe option live screen= as suggested in order to avoid the white screen bug. ANy idea? Should I try a older version of lubuntu?

---

### Post by jrog on 2012-09-29
> **bblackbelt said:**
> no I am at the beginning of the installation process. I boot withe option live screen= as suggested in order to avoid the white screen bug. ANy idea? Should I try a older version of lubuntu?
Have you also added the parameter 'b43.blacklist=yes' (without the quotes) after 'live' when you boot? I have installed Lubuntu on a G4 and I always had to add that parameter. Not sure if it's related to the problem you're having or not, though.

---

### Post by bblackbelt on 2012-09-29
> **jrog said:**
> Have you also added the parameter 'b43.blacklist=yes' (without the quotes) after 'live' when you boot? I have installed Lubuntu on a G4 and I always had to add that parameter. Not sure if it's related to the problem you're having or not, though.

 nope. i will try this one

---

### Post by bblackbelt on 2012-09-29
> **bblackbelt said:**
> nope. i will try this one

  this one work. How do  I install on the whole disk?

---

### Post by MG&amp;TL on 2012-09-29
> **bblackbelt said:**
> this one work. How do  I install on the whole disk?

Just select 'use entire disk' in the installer. I'm not familiar with the G4 installation process though, so you might need to do something more complicated.

---

### Post by jrog on 2012-09-29
> **bblackbelt said:**
> this one work. How do  I install on the whole disk?
Awesome; glad it worked! Can you please mark the thread as 'solved' using the Thread Tools at the top of the page, when you get a chance?

As for installing on the whole disk, I believe MG&TL is right; you should be able to just choose to install on the entire disk. I don't really have a very good memory of the rest of the installation process, though, so there may be more to it. Can you make the question more specific?

---

### Post by jrog on 2012-09-29
By the way, when you install Lubuntu, it would be extremely helpful for you to have a wired Internet connection. This is because you will need to install the drivers for your wifi card once Lubuntu is installed, but doing so will require an Internet connection of some kind. You should install them using this command at the terminal:

```
sudo apt-get install firmware-b43-installer
```

---

### Post by bblackbelt on 2012-09-29
> **jrog said:**
> By the way, when you install Lubuntu, it would be extremely helpful for you to have a wired Internet connection. This is because you will need to install the drivers for your wifi card once Lubuntu is installed, but doing so will require an Internet connection of some kind. You should install them using this command at the terminal:

```
sudo apt-get install firmware-b43-installer
```


Sure. Thanks both for your time

---

