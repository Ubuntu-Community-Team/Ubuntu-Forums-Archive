---
title: "java package broken, unable to remove"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Falc7 on 2008-11-08
I am unable to download new programs because i have a broken package. It tells me to remove it with synaptic package manager. However package manager says the package is in a very inconsistant state. And should be reinstalled before removal.
However it dosen't seem to have an option to reinstall anywhere, so i don't know what to do.

---

### Post by gandaran on 2008-11-08
can you post the errors messages, it would help!
try running these commands
> sudo apt-get clean
sudo apt-get autoclean
sudo apt-get update

question; is this java package from  ubuntu repos or some other java package you downloaded?

---

### Post by Falc7 on 2008-11-08
Here is the error messages, they are the same after running the above commands:
[http://img142.imageshack.us/my.php?image=96862638fy4.jpg](http://img142.imageshack.us/my.php?image=96862638fy4.jpg)

---

### Post by dracayr on 2008-11-08
to reinstall: sudo apt-get install --reinstall sun-java6-bin

dracayr

---

### Post by gandaran on 2008-11-08
you'll have to force remove it then try this command first

sudo apt-get --purge sun-java6-bin

if no work then

sudo dpkg --remove --force-remove-reinstreq sun-java6-bin

---

### Post by Sealbhach on 2008-11-08
You can try to fix broken packages in Synaptic:



To fix broken packages

    *

      Choose Edit > Fix Broken Packages from the menu.
    *

      Choose Apply Marked Changes from the Edit menu or press Ctrl + P.
    *

      Confirm the summary of changes and click Apply. 

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)


.

---

### Post by Falc7 on 2008-11-08
Thanks guys it is fixed now

---

