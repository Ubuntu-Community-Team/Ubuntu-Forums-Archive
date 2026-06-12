---
title: "[SOLVED] Reinstalling 2.6.24-20-generic kernel help"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by TadeoDiaz on 2008-07-07
This is a very noob question but I know i updated the kernel a few weeks ago and when I go to check the version that I am running (uname -r) I find out that I am running 2.6.24-18-generic

```
uname -r
2.6.24-18-generic
```

I can't find the command line to reinstall 2.6.24-20-generic
I've tried using
```

sudo apt-get install linux-image-2.6.24-20-generic
```

but all i get is:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.24-20-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Can anyone help?

The reason why I am trying to upgrade is because my suspend function is still not working on the 18-generic kernel and am hoping that the 20-generic version fixes it.

I am running Hardy on a Lenovo 3000 v100 laptop, thanks in advanced

---

### Post by forger on 2008-07-07
there's no linux-image-2.6.24-20-generic in the official repositories of ubuntu hardy heron, only linux-image-2.6.24-[COLOR="Red"]**19**[/COLOR]-generic

try this:
```
sudo apt-get install --reinstall linux-image-2.6.24-19-generic linux-ubuntu-modules-2.6.24-19-generic linux-restricted-modules-2.6.24-19-generic
```

---

### Post by fidamehran on 2008-07-08
That's true. 2.6.24.19 is the last one running now. But still if you see that you have one latest kernel installed and is booting into the other one, there are 2 solutions.
**1. Temporary solution**: When Ubuntu is booting, There is a prompt saying "Press ESC to go to boot menu" or as such. Press ESC and you'll see a list of kernels that you can boot into. Select the right kernel and boot into it.
**2. More Solid Solution**: Install Startup manager from Synaptic Package Manager. It is a so easy GUI program that can help you so easily to select which kernel you want to boot into.
I use this.
Very easy. Top class material.

---

### Post by TadeoDiaz on 2008-07-09
Thanks to both of you guys, I think on the road to attempting to fix the suspend problem I installed the 2.6.24-20 generic somehow (I've been working on this since I got Ubuntu on my laptop)

I had changed so many things that I ended just reinstalling to start from scratch.

---

