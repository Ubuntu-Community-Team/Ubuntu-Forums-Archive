---
title: "I installed KDE Plasma and then uninstalled it and now my login screen is messed up"
date: 2021-02-10
forum: New to Ubuntu
---

### Post by lelolelo on 2021-02-10
I have Ubuntu with Gnome but I decided to try out KDE Plasma to see how it is like. I tried it for a bit and even though I liked KDE Plasma I decided I would keep using Gnome so I uninstalled KDE Plasma and most of KDE software. The problem is that now my default login screen is the KDE login screen. There is also another problem, before I installed KDE when I was away from keyboard for a while my screen would turn black and I had to log in again to use the computer now it doesn't do that (I'm using a desktop, not a laptop btw). How do I revert the login screen to Gnome's login screen and how do I turn on the sleep thing after being away for a few minutes?

---

### Post by CatKiller on 2021-02-10
> **lelolelo said:**
> The problem is that now my default login screen is the KDE login screen.

The **display manager** is what provides the login screen and starts the session when you log in. There are several to choose from: Kubuntu uses SDDM and Ubuntu uses GDM, although it used to use LightDM for prior versions. I can't remember off the top of my head the command to switch between them, but a search for "update alternatives gdm" should get you the correct syntax.

---

### Post by deadflowr on 2021-02-10
> I can't remember off the top of my head the command to switch between them
```
sudo dpkg-reconfigure gdm3
```
will allow resetting which will be used by default.
Should be able to switch it on the fly by using systemctl to stop one and start the other.
(Should being the optimal word here)
something like
```
sudo systemctl stop sddm
sudo systemctl start gdm3
```
If it fails, which it might, just run reboot to reboot and if you set the DM with the reconfigure command it will boot to that one.

---

### Post by lelolelo on 2021-02-11
[HR][/HR]It worked! Thank you.

---

### Post by ajgreeny on 2021-02-11
Installing more than one DE as you did is very often not as straightforward as users think it will be and can easily result in the sort of problem you saw.

Much better, if you want to check out other DE versions of Ubuntu, is to simply run the live system from a USB or even install a virtual system in Virtualbox or other virtualisation software.

However, I am delighted that you now are back where you wanted to be so please can you now mark this thread as SOLVED from the Thread Tools menu up top; it is a great help to others searching  the forum.

---

