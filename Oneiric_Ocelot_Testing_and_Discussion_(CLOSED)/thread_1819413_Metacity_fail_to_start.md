---
title: "Metacity fail to start"
date: 2011-08-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by dino99 on 2011-08-06
on i386 i need to start it with a terminal, otherwise the windows cant be moved as only the menu is available, and scrolling often freeze. As long as i let the terminal opened after starting metacity (metacity --replace &), the system runs well.

am i the only one with this issue ?

---

### Post by paul_in_london on 2011-08-06
I had a similar issue yesterday where I had to start **gnome-shell** manually - see this thread:

[http://ubuntuforums.org/showthread.php?t=1819208](http://ubuntuforums.org/showthread.php?t=1819208)

All back to normal now with latest updates - **gnome-session-bin_3.1.3-0ubuntu8** etc.

HTH.

---

### Post by dino99 on 2011-08-06
still broken with the latest updates

---

### Post by thonuz on 2011-08-06
One of the updates removed the desktop so there is none. Updating gnome-session did not work. Reinstalling nvidia also did not work.

I had to remove Nvidia and revert back to nouveau driver. 
I did a sudo update-initramfs -u    and now it works. Even lxde would not start before.

I'm not going to upgrade my laptop yet. At least for nvidia there is a problem.

---

### Post by paul_in_london on 2011-08-06
> **thonuz said:**
> One of the updates removed the desktop so there is none. Updating gnome-session did not work. Reinstalling nvidia also did not work.

I had to remove Nvidia and revert back to nouveau driver. 
I did a sudo update-initramfs -u    and now it works. Even lxde would not start before.

I'm not going to upgrade my laptop yet. At least for nvidia there is a problem.

Not using nvidia driver on this box, so luckily didn't have that problem. I do use it on my other box though, so thanks for the warning.

---

### Post by Harry33 on 2011-08-06
> **thonuz said:**
> One of the updates removed the desktop so there is none. Updating gnome-session did not work. Reinstalling nvidia also did not work.

I had to remove Nvidia and revert back to nouveau driver. 
I did a sudo update-initramfs -u    and now it works. Even lxde would not start before.

I'm not going to upgrade my laptop yet. At least for nvidia there is a problem.

If you have upgraded to nvidia-current_280.13, then you have a problem.

---

