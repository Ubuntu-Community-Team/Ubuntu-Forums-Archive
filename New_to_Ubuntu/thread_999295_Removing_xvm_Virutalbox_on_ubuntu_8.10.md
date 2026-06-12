---
title: "Removing xvm Virutalbox on ubuntu 8.10"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by hitmankb on 2008-12-01
There is nothing wrong with it, I would just like to remove it, so I can install the OSE version.

I downloaded and installed the deb package.

Any help is appreciated, and by the way, I did search, but im a linux newb and this isnt like ad/remove programs or just dragging the aplication to the trash can on OSX...
Thanks,
Kenny

---

### Post by bodhi.zazen on 2008-12-01
dpkg -r virtualbox

---

### Post by hitmankb on 2008-12-02
> **bodhi.zazen said:**
> dpkg -r virtualbox

Thanks GURU!

---

### Post by hitmankb on 2008-12-02
> **bodhi.zazen said:**
> dpkg -r virtualbox

When I use the "dpkg -r virtualbox" command, I get "dpkg - warning: ignoring request to remove virtualbox which isnt installed"

Now what do I do?

Thanks,
Kenny

---

### Post by handydan918 on 2008-12-02
How did you install the virtual box that you are trying to remove?

---

### Post by bodhi.zazen on 2008-12-03
sudo dpkg -r VirtualBox

??

---

### Post by hitmankb on 2008-12-03
> **handydan918 said:**
> How did you install the virtual box that you are trying to remove?

I downloaded the "Ubuntu 8.10 ("Intrepid Ibex")" .deb file and installed it using the Debian installer/package manager that's built into ubuntu!

Any ideas?

---

### Post by hitmankb on 2008-12-03
> **bodhi.zazen said:**
> sudo dpkg -r VirtualBox

??

Same thing :(

---

### Post by bodhi.zazen on 2008-12-03
Well, if you installed the VirtualBox deb it has to be listed on your system somewhere somehow.

I suggest you use synaptic. Search for virtualbox and Virtualbox and VitrualBox etc, or show all packages and scroll down to the "V" section. Remove it from Synaptic.

You can also 

dpkg -l > packages.txt

then open packages.txt

---

