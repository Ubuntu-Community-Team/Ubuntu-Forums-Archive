---
title: "Trouble installing gfortran on windows 10"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by lzucker1 on 2020-06-10
[COLOR=#242729][FONT=Arial]Hi! I am new to using Unbuntu, and I am trying to install gfortran on my pc. I am attempting to do this using the package manager Aptitude, as recommended on the Ubuntu website. However, I am having three problems with this. The first is that there appear to be many other packages that I need to install before I can install gfortran (listed in dependencies), and each of those requires more packages, etc. I am not sure if there is an easier way to install all the necessary packages, or simply to know which ones a need to have. When I try to install without first installing the dependencies, it tells me "no packages are scheduled to be removed, installed or upgraded," and then will not allow me to move forward with the installation.The second issue is that when I do find a package that I can install (one that is listed in the dependencies of gfortran, but does not have any dependencies itself), it appears to install but then still lists as not installed in the dependencies of gfortran. The third issue is that I am not having touble even operating Aptitude, as it will not let me search for the packages I need. I know this is a lot but if anyone could help me with this I would be very grateful. Thanks so much![/FONT][/COLOR]

---

### Post by daniewicz on 2020-06-10
Your thread title says installing on windows 10??

What version of ubuntu?

Best to use the synaptic package manager. If you select gfortran it will select all of the needed dependencies.

---

### Post by Impavidus on 2020-06-11
The whole idea behind package managers is that those dependencies get installed automatically, so if that doesn't work, there's something wrong with your package manager. I don't use aptitude. Synaptic, aptitude and apt are different interfaces to the same package management system, so it shouldn't matter which one you use. What do you get from these commands:```
sudo apt update
sudo apt upgrade
sudo apt install gfortran
```
You can copy the output to your forum post using code tags.

---

