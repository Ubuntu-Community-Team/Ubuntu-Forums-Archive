---
title: "VirtualBox Server"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by philk949 on 2008-07-28
Hi,
I have just installed VirtualBox Server from Synaptic but don't know how to activate it. A little help, please?
Thanks,
Phil     Hardy Heron 8.04

---

### Post by Jeremy23 on 2008-07-28
There is no such product called "VirtualBox Server".

Either you mean "VirtualBox", or you mean "VMware Server". Which one?

---

### Post by kool_kat_os on 2008-07-28
err...what Jeremy23 said :)

---

### Post by philk949 on 2008-07-28
**virtualbox-ose modules for linux-image-2.6.24-19-server**

This is located in Synaptic on Hardy 8.04.
If you have info on running VM Ware in Ubuntu and how to install, I would also be glad of that, Jeremy23
Thanks.
Phil

---

### Post by kool_kat_os on 2008-07-28
I had the same problem,

If it is not in the Applications > something i dont remember > Virtual Box OSE

Then remove the one you installed.
```
sudo apt-get autoremove virtualbox-ose
```

then get the deb from sun and install it.

if that doesnt work...reinstall the deb and it worked for me.

---

### Post by Jeremy23 on 2008-07-28
By the sound of it, you have installed the VirtualBox kernel modules, but not the actual VirtualBox application.

Make sure the "virtualbox-ose" package (not just "virtualbox-ose-modules") is installed.

Once it's installed, you can run it either by going to Applications &#8594; System Tools &#8594; VirtualBox OSE, or by typing:

```
$ virtualbox
```

...in a terminal.

---

