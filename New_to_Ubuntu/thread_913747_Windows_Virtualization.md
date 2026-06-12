---
title: "Windows Virtualization"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by Gonz_91 on 2008-09-08
I'm a linux newbie, and as such, I don't feel to safe without a Windoze OS running near me (yet), in case there's something I do wrong in linux.

So, what I wanted your opinion on, was if it's a viable option to run Vista in VirtualBox, just in case, and assingn my whole hard drive to Ubuntu.


Thanks in advance :)

---

### Post by jedi-penguin on 2008-09-08
VirtualBox does support vista, I have tried myself.

---

### Post by blazemore on 2008-09-08
If you want to run full virtualisation, I personally wouldn't use Vista. It uses far too much memory to make it a viable option to run on top of Ubuntu.

I'd recommend Virtualbox, certainly, because of its seamless mode. However, if you can, use Windows XP SP3. It's far faster, and compatible with more applications.

Another option is to use Wine. This lets you run Windows applications "Natively" on Linux systems, and is generally faster to use than a full virtualisation solution.

Conclusion: Use Windows XP, not Vista.

---

### Post by Gonz_91 on 2008-09-08
Thanks, blazemore, for your thoughts :)

Indeed, for now, XP might be a better idea than Vista, since I probably won't be doing too much gaming, since I'm using somewhat weak hardware.

Altough, I really was starting to like Vista when I switched to Ubuntu...
So, I'll be giving it some thought :D

---

### Post by Gonz_91 on 2008-09-08
I can't get virtualbox working :(
Everytime I try to start a machine, it gives me this error:
> VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..

I tried installing that package, but all it did was add some more entries to my GRUB menu :(

help, plz

---

### Post by Gonz_91 on 2008-09-08
Solved it, checkd my kernel version -.-'

---

### Post by juiceman on 2008-09-09
> **Gonz_91 said:**
> Solved it, checkd my kernel version -.-'

what did you actually do to fix that problem?  i have the exact same one and i'm not very experienced... please help.

---

### Post by silverglade00 on 2008-09-09
You have to be careful to load the virtualbox-modules package that goes with your kernel. The latest 2.6.24-21 kernel took a couple weeks for the vbox-modules package to be updated. Just load the modules package that goes with the kernel and you will be ok.

---

### Post by tuxxy on 2008-09-09
> if you want to run full virtualisation, I personally wouldn't use Vista. It uses far too much memory to make it a viable option to run on top of Ubuntu.

I'd recommend Virtualbox, certainly, because of its seamless mode. However, if you can, use Windows XP SP3. It's far faster, and compatible with more applications.

If you on 64-bit Ubuntu then run you could run Vista, it will handle it with ease, heavy virtualization is another benefit of using 64-bit :)

XP SP3 is great though, I would prefer this to Vista anyway prob :lolflag:

---

### Post by lovinglinux on 2008-09-09
> **Gonz_91 said:**
> Indeed, for now, XP might be a better idea than Vista, since I probably won't be doing too much gaming, since I'm using somewhat weak hardware.

As far as I know, VirtualBox doesn't support 3D acceleration, so makes no difference running XP or Vista if you have plans to run games inside it.

---

