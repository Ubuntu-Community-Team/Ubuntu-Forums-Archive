---
title: "linux source code folder"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by melrokz on 2008-07-05
Hi! I'm melvin from India. May I know where my Linux kernel source code folder is? may i also know how to compile Dazuko?

---

### Post by durand on 2008-07-05
Just a quick google:

[http://www.kernel.org/](http://www.kernel.org/)

I don't have a clue about Dazuko.

---

### Post by prshah on 2008-07-05
> **melrokz said:**
> Hi! I'm melvin from India. May I know where my Linux kernel source code folder is? may i also know how to compile Dazuko?

By default, the linux kernel source is stored in /usr/src/linux*

However, sources are (usually) not installed, but you can install them with a quick command from the terminal (Applications-Accessories-Terminal) ```
sudo apt-get install linux-source
``` This will install the kernel sources for your current running kernel.

For source code for other software, look in synaptic for packagename-source, where packagename is the name of the software whose sources you want.

---

### Post by spiderbatdad on 2008-07-05
/lib/modules

It seems some of dazuko's functionality is no longer supported in the 2.6 kernel. You will have to study the 2.6 readme file in the package. right click to extract the package.

---

### Post by nowshining on 2008-07-05
the linux kernel source files are installed by default to /usr/src/

---

