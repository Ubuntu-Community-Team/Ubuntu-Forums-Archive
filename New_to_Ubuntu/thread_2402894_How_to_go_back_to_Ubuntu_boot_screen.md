---
title: "How to go back to Ubuntu boot screen?"
date: 2018-10-05
forum: New to Ubuntu
---

### Post by bscruggs99 on 2018-10-05
Hello everybody. I am new to Ubuntu but have been windows free for several days now. 
Yesterday I installed several different desktop environments to see which I liked best. I installed kubuntu, lubuntu, xubuntu etc. The usual suspects. I can choose my environment and everything works fine. My only issue is when I turn on my laptop, the boot loader screen is black where it was purple (default Ubuntu I guess) and the splash screen when loading is Kubuntu now. It's just a matter of cosmetics but I prefer the purple boot options and the Ubuntu splash screen so how do I revert back to them?

Thank you kindly for any help!

---

### Post by ajgreeny on 2018-10-05
You probably need to reinstall the **pymouth-theme-ubuntu-text** and **plymouth-theme-ubuntu-logo** packages and remove the similarly named packages for kubuntu, lubuntu and xubuntu, leaving just the ubuntu versions.  This is possibly easiest done using synaptic package-manager which may already be installed if you have added lubuntu-desktop.

You may also need either to reinstall gdm3 which provides the login screen, or if it's still installed run ```
sudo dpkg-reconfigure gdm3
``` which will ask you which display manager you wish to use if more than one is installed.

---

### Post by bscruggs99 on 2018-10-05
Awesome, thank you. I will try to reconfigure gdm on my lunch break and,go from there!

---

