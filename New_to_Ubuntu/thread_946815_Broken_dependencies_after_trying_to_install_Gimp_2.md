---
title: "Broken dependencies after trying to install Gimp 2.6"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by RedRat on 2008-10-13
I downloaded a package from Get-deb and tried to install the updated version of Gimp. When I "installed" one of the packages, libgimp2.0_2.6.1-1~getdeb1_i386.deb, the installation failed and the dependencies were broken. It was suggested that I run:
sudo apt-get -f
which I did but that command calls for an argument. What argument do I pass to that command.

Attempt to use Synaptic tells me that there are broken dependencies and they are all associated with Gimp. When I try to re-install gimp from the normal repos, I get a chance to look over the list of programs to be un-installed. Among these is Ubuntu-Desktop. If I do this, what do I get after the operation, no GUI?? Now I am a GUI type guy and would hate to try to re-install the GUI from the command line. When I try to just re-install the ubuntu-desktop, I get an error about locking down folders. 

Any advice here before I proceed would be greatly appreciated.

---

### Post by Ryadt on 2008-10-13
```
sudo apt-get install -f
```

---

### Post by Keen101 on 2008-10-13
your command is not complete...

sudo apt-get (argument goes here) -f

try this, but i don't know if this is the proper command.

```
sudo apt-get install --fix-broken
```

alternatively synaptic package manger should have an option to fix them too....

**[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)**

---

### Post by RedRat on 2008-10-13
> **Ryadt said:**
> ```
sudo apt-get install -f
```

Ok ran this but I am at a stopped stage waiting for input. I note that it will remove the ubuntu-desktop. What happens then? How do I reinstall ubuntu-desktop??

---

### Post by RedRat on 2008-10-13
> **Keen101 said:**
> your command is not complete...

sudo apt-get (argument goes here) -f

try this, but i don't know if this is the proper command.

```
sudo apt-get install --fix-broken
```

alternatively synaptic package manger should have an option to fix them too....

**[https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages](https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages)**
synaptic doesn't help. It still wants to remove ubuntu-desktop. How do I get that back??

---

### Post by Ryadt on 2008-10-13
```
sudo apt-get install ubuntu-desktop
``` will install the desktop if the other command doesn't install it back.

---

### Post by Keen101 on 2008-10-13
> **RedRat said:**
> synaptic doesn't help. It still wants to remove ubuntu-desktop. How do I get that back??

we'll i don't know why it wants to remove ubuntu-desktop, but if it does get removed, you can always re-install it from the recovery console option when GRUB appears.

---

### Post by philinux on 2008-10-13
The advice for this was to remove the old version of gimp first then install the latest.

---

### Post by RedRat on 2008-10-13
OK thanks to those that wrote in. This got kind of messy but luckily I didn't lose the desktop.

I did indeed have to reinstall the desktop but had problems in that my attempt to install the GIMP update brought in a libgimp2.0 package from the update and completely fouled up Gimp and the desktop. Once I eliminated that library, I was then able to reinstall the old gimp that is in the repos.  Many thanks to those who wrote.

---

### Post by RedRat on 2008-10-13
> **philinux said:**
> The advice for this was to remove the old version of gimp first then install the latest.

Thanks, I should have read far more closely. I will wait until Gimp shows up in Synaptic. I still do not understand why GIMP and the the desktop are closely tied together in this way. Really odd. I would have thought that the desktop is independent of a drawing program.

---

### Post by Ryadt on 2008-10-13
> **RedRat said:**
> Thanks, I should have read far more closely. I will wait until Gimp shows up in Synaptic. I still do not understand why GIMP and the the desktop are closely tied together in this way. Really odd. I would have thought that the desktop is independent of a drawing program.
The ubuntu-desktop is a package that contains all the programs that came default when you do a clean install.

---

