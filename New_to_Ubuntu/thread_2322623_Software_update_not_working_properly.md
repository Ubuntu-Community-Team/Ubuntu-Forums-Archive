---
title: "Software update not working properly?"
date: 2016-04-29
forum: New to Ubuntu
---

### Post by matti123456 on 2016-04-29
When i run Software updater it says ''the software on this computer is up to date. Yet when i opened Ubuntu software there was a OS update waiting to get installed. The update is bind9-host 1:9.10.3dfsg.p4-8ubuntu1. Is this normal?

I am using Ubuntu 16.04.

Edit:To clarify, there is not necessarily any problem with the Software updater. I am just trying to understand how thing work in Ubuntu, maybe this is how it should work.

---

### Post by gameboy9309 on 2016-04-29
Hi, Matti! Could you try to restart your system? That might work.

---

### Post by matti123456 on 2016-04-29
Restarting Ubuntu did not work.

---

### Post by grahammechanical on 2016-04-29
Ubuntu Software is new. It is actually Gnome Software. It replaces the Ubuntu Software Centre because the developers wanted to make use of something called AppStream. And that would have meant re-writing Ubuntu Software Centre. Whereas, Gnome Software is already compatible with AppStream. So, the Ubuntu developers made the switch from Ubuntu Software Centre to Gnome Software/Ubuntu Software.

On my system Ubuntu Software is reporting one package to be updated. But when I click on OS Updates to see what is actually to be updated I see that it is a package that has been held back for weeks and cannot be installed.

You might want try clicking the reload icon. But, for myself I would trust Software Updater. Consider Ubuntu Software as a work in progress.

[https://www.freedesktop.org/wiki/Distributions/AppStream/](https://www.freedesktop.org/wiki/Distributions/AppStream/)

Regards

---

### Post by egeezer on 2016-04-29
The best way to make sure you get all the updates that are current is to open a terminal and type
```
sudo apt update
```
Then press Enter.  The terminal will request your password.  Type it in (nothing will show on the terminal about your password) and press Enter again.
A list of all available updates will appear, along with interactive instructions about installing them.

As to why the Software updater didn't list something, 16.04 is a recent release, and I would guess that new material is still being fed in on a rapid time scale.

---

### Post by matti123456 on 2016-04-29
Thanks for the replies. 

I have been away from my computer, when i get back i will try to install the update through Ubuntu software just to see what happens. I will prefer Software updater over Ubuntu Software as well, i think i need to do bit more research before i start using terminal to manage updates.

---

