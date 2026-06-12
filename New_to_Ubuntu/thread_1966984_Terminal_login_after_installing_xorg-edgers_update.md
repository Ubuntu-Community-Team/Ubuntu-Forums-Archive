---
title: "Terminal login after installing xorg-edgers updates"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by UnknownFearNG on 2012-04-27
I recently updated my drivers with open-source drivers from xorg-edgers PPA. Now, I rebooted and I get a terminal login. I try starting lightdm and it fails!!! How can I get my desktop back? :(

---

### Post by josephmills on 2012-04-27
please press ctrl+alt+f1 

sign in 

run ```
lsmod
```
what drivers are loaded are there 2 of them ?

you also might want too look at x-swat and not the Crack 

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

---

### Post by UnknownFearNG on 2012-04-27
There is a long list, how do I know which drivers are loaded? Fglrx is 0.

---

### Post by UnknownFearNG on 2012-04-27
Added the x-swat ppa. I'll see if that does anything.

---

### Post by josephmills on 2012-04-27
```
sudo apt-get install pastebinit
```
then 

```
lsmod |pastebinit
```

post link here thanks

---

### Post by UnknownFearNG on 2012-04-27
Here is the link:
[http://paste.ubuntu.com/950778/](http://paste.ubuntu.com/950778/)

---

### Post by UnknownFearNG on 2012-04-27
I tried running a java program for fun and it said "No X11 DISPLAY variable was set, but this program performed an operation which requires it."

How do I go about reinstalling one? I didn't think the xorg ppa would kill my display.

---

### Post by UnknownFearNG on 2012-04-27
I'm just going to reinstall Ubuntu 12.04 and not install open-source drivers.

---

### Post by josephmills on 2012-04-27
After looking thou your paste you had no driver loaded  for card

---

### Post by UnknownFearNG on 2012-04-27
Must of been when I installed the open-source drivers. From now on, I'll install the proprietary drivers so I don't have any issues.

---

