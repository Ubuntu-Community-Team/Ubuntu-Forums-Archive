---
title: "old video card could do better"
date: 2008-11-26
forum: New to Ubuntu
---

### Post by Thriell on 2008-11-26
I just recently got 8.10 installed on my (incredibly outdated) system. Now I'm having an "issue" with my video card.

I have an ATI Rage Pro video card. It's kinda old, but it's what I've got, and it works.

Ubuntu insists that it can't do better than 800 x 600 and I know this ain't so. I just don't know how to convince Ubuntu of that fact.

Do I need to go searching for a different driver, or is there something else that I'm missing as an absolute beginner?

---

### Post by LowSky on 2008-11-26
go to System> admin > hardware drivers
make sure you have proprietary drivers turned on

---

### Post by Thriell on 2008-11-26
> **LowSky said:**
> go to System> admin > hardware drivers
make sure you have proprietary drivers turned on

"No Proprietary drivers are in use on this system"

and the list (or the place where the list would be) is empty.

---

### Post by MockY on 2008-11-26
You could install the ATi drivers using Envy.
Open terminal (Accessories - Terminal) and type or paste the following and hit enter:

```
sudo apt-get install envyng-gtk
```

Envy should now be located in the menu. Just launch it and follow instructions.

---

### Post by Thriell on 2008-11-26
> **MockY said:**
> You could install the ATi drivers using Envy.
Open terminal (Accessories - Terminal) and type or paste the following and hit enter:

```
sudo apt-get install envyng-gtk
```

Envy should now be located in the menu. Just launch it and follow instructions.

Ummmm. nope. 

I saw that it downloaded 2 files and installed them, but there's nothingnew on any menu... not even after a logout/login. What am I missing?

---

### Post by mapes12 on 2008-11-26
I had the same problem with my ATI Rage XL device. To fix the problem I had to go back to 8.04 LTS. Then in Terminal:```
gksudo displayconfig-gtk
``` then select your device, monitor and preferred screen res from the options in the GUI.

---

### Post by Thriell on 2008-11-26
> **mapes12 said:**
> I had the same problem with my ATI Rage XL device. To fix the problem I had to go back to 8.04 LTS. Then in Terminal:```
gksudo displayconfig-gtk
``` then select your device, monitor and preferred screen res from the options in the GUI.

I'm assuming that command MUST be run in 8.04, because in 8.10 it does nothing. Problem is, I spent a week trying to figure out why 8.04 won't see my hard drive (LiveCD boots, Hard Drive boot dies while waiting for root filesystem)  before I got a chance to try 8.10.

---

