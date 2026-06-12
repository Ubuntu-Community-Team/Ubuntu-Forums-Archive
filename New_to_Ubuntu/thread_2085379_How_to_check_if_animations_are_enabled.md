---
title: "How to check if animations are enabled?"
date: 2012-11-18
forum: New to Ubuntu
---

### Post by abraham.varricatt on 2012-11-18
I have a Dell laptop, installed Ubuntu 12.04.1 (the long term release) and installed the propitiatory nVidia drivers.

How can I tell if the desktop animations are enabled? Or better yet, is there a GUI-based method by which I can customize them?

---

### Post by zombifier25 on 2012-11-18
There are many ways to find out but the surest way is to run this in the terminal:
```
echo $DESKTOP_SESSION
```
If it returns ubuntu, then it is using Compiz to render animations. If ubuntu2d, then it's not.

To customize Compiz, install compizconfig-settings-manager.

---

### Post by abraham.varricatt on 2012-11-18
> **zombifier25 said:**
> There are many ways to find out but the surest way is to run this in the terminal:
```
echo $DESKTOP_SESSION
```
If it returns ubuntu, then it is using Compiz to render animations. If ubuntu2d, then it's not.

To customize Compiz, install compizconfig-settings-manager.

It returns,

ubuntu-2d

Which confirms my fears. I'm going to try installing compizconfig to see if I can enable the 3D stuff.

---

### Post by abraham.varricatt on 2012-11-18
Some good news is that I've got 3D working again in Ubuntu 12.04.1

The bad news is that I had to uninstall my nVidia drivers to do it. And not just a simple uninstall, but a full "purge" of them using "apt" from the terminal.

In brief, my laptop has an optimus-supported configuration and that is NOT currently supported under Linux from nVidia. I'll probably need to figure out some way to disable the extra GPU to save power, but for the time being, it looks like 3D is working again.

---

### Post by zombifier25 on 2012-11-18
For your NVIDIA Optimus card, there's [Bumblebee](http://bumblebee-project.org/).

---

