---
title: "Ubuntu freezing every time"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by UltraCheese on 2008-05-13
Installed Ubuntu 8.04 through Wubi the other day and the installation went fine.  For the first 30-60 seconds of running it every thing is fine, but then it starts to freeze up.  After this point I can't even log out, it simply freezes to where I can't click anything when I try to.  I was also looking at the system monitor and noticed it was detecting two processors.  Could this be causing it?
My computer more than meets the requirements to run Ubuntu, but I'm planning on using Xubuntu if I can't get this fixed.  I've used 7.04 in the past to try out Wubi and didn't have any problems for the short time I used it.  I was trying to add it to Ubuntu using sudo apt-get install xubuntu-desktop, but it keeps freezing when it gets to that preconfiguring step.  Any help there or am I going to have to uninstall Ubuntu and install Xubuntu?

---

### Post by andrewski on 2008-06-11
Welcome to the forums. Since Wubi is its own animal, maybe you could get more help in the Wubi forum?

But your instincts are right: you should simply be able to install xubuntu-desktop. Definitely something going on there.

---

### Post by jimv on 2008-06-11
Seems that a lot of people are having trouble with lockups in the latest release.  Some people have had success switching to the RT kernel.

Doing it is pretty simple and *shouldn't* cause any problems.

Here's the code:

```
sudo apt-get install linux-image-2.6.24-18-rt linux-headers-2.6.24-18-rt linux-restricted-modules-2.6.24-18-rt linux-ubuntu-modules-2.6.24-18-rt
```

This will get the 2.6.24-18-rt kernel for you (if for some reason it doesn't like -18, try -17...I have some extra repos enabled and I'm not sure that -18 is a normal upgrade yet).  It will add the entry to your menu.lst automatically.  If something goes wrong, you can simply remove the kernel through apt with this command:

```
sudo apt-get remove linux-image-2.6.24-18-rt linux-headers-2.6.24-18-rt linux-restricted-modules-2.6.24-18-rt linux-ubuntu-modules-2.6.24-18-rt
```

---

### Post by andrewski on 2008-06-12
> **jimv said:**
> ```
sudo apt-get install linux-image-2.6.24-18-rt linux-headers-2.6.24-18-rt linux-restricted-modules-2.6.24-18-rt linux-ubuntu-modules-2.6.24-18-rt
```This will get the 2.6.24-18-rt kernel for you (if for some reason it doesn't like -18, try -17...I have some extra repos enabled and I'm not sure that -18 is a normal upgrade yet). 
You could just use the main package, which is simpler, and good if you want to continue using the RT kernels when they are upgraded:
```
sudo apt-get install linux-rt
```
From the package description: "This package will always depend on the latest complete rt Linux kernel available."

---

### Post by jimv on 2008-06-13
The more you know!

---

