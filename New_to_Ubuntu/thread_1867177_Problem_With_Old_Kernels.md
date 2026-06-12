---
title: "Problem With Old Kernels"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by dep0 on 2011-10-22
I have trouble deleting the old kernel's.
I searched linux image at synaptic packages, i deleted those i found and was sure that wasn't the one i was running, but still the old kernels come up when i boot my system.
Any suggestions?

---

### Post by Paqman on 2011-10-22
Grub should re-scan whenever a kernel is removed, but you can prompt it to update itself. Open a terminal and enter:
```
sudo update-grub
```

---

### Post by cap10Ibraim on 2011-10-22
try the computer janitor from system menu (on gnome 2)

---

### Post by dep0 on 2011-10-22
Well i think i did removed them. 
But the old versions of ubuntu remained the same at the boot-screen.
Can i remove them too?

---

### Post by masgeeks on 2011-10-22
Ubuntu tweak has a utility for removing old kernels if I recall... worked pretty nice... easy to use...  :)

---

### Post by beew on 2011-10-22
You need to remove the linux headers as well.

If you are running a multiboot system you need to update grub in the OS which controls grub (assuming it is something that runs grub2), but if you are just doing a single install there is no need for that.

---

### Post by cap10Ibraim on 2011-10-22
> **beew said:**
> You need to remove the linux headers as well.

If you are running a multiboot system you need to update grub in the OS which controls grub (assuming it is something that runs grub2), but if you are just doing a single install there is no need for that.
in synaptic search for linux-image and linux-headers and note the versions

---

### Post by dep0 on 2011-10-22
> **cap10Ibraim said:**
> in synaptic search for linux-image and linux-headers and note the versions

I searched but there are not any of the older versions that are installed.
However i can boot to one of the older versions.

---

### Post by Gadgetech on 2011-10-25
I've written a few blog posts on removing the old kernels from Ubuntu. If you want the quick command line one-liner, follow this one:
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/]("http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/")

If you want the more manual, step by step process, follow this one:
[http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/]("http://tuxtweaks.com/2009/12/remove-old-kernels-in-ubuntu/")

---

