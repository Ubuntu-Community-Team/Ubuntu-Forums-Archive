---
title: "list all installed software packages ??"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by JBA2337 on 2008-08-14
I wanted to make a list of all the software packages that are installed on my computer. Synaptic package manager tells me that I have 1,248 packages installed.

Several notices that I have read on this forum told me to use either of  the following terminal commands to get a list of all packages installed on my computer.

dpkg -l > installed_apps

dpkg --get-selections > installed_apps

Both of these commands supposedly lists all the packages installed on my computer. Using either one of these commands I got a list of exactly 499 packages installed, but Synaptic package manager says that I have 1,248 packages installed.

Why are the numbers not the same? Which one is correct?

JBA2337

---

### Post by f37u5g0d on 2008-08-14
An "app" short for the word "application" can be made up (and almost always is) of more than 1 package.  If you open synaptic and look at "installed" under the status tab (lower left) it will list every PACKAGE that is installed.  If you go to add/remove, choose all categories, and select installed apps from the drop down menu you will see all of the apps that your terminal command outputed.

---

### Post by Sorivenul on 2008-08-14
dpkg -l (Probably pipe this through less - for example dpkg -l | less)
dpkg- l | awk '{print $2}' > installed_packages.txt (This would print the package names to a text file nammed installed_packages.txt)

Good luck!

Edit - note that "applications" and "packages" are very different things.

---

### Post by iaculallad on 2008-08-14
> dpkg -l > installed_apps

- This command list all applications installed in your system with a bit of description.

> dpkg --get-selections > installed_apps
- This only list the packages installed.

Synaptics has larger package count because it's just telling you the number of packages that can be installed, not actually saying that it had installed those number of packages.

---

### Post by JBA2337 on 2008-08-15
I am still a bit confused.

In Synaptic package manager, if I click on Status>Installed, the last line says "1253 packages listed, 1253 installed". That seems pretty clear. Synaptic package manager reports that there are 1253 packages actually installed.

But when I use sudo dpkg -l > installed_apps, I get a list of 499 applications.

If I understand correctly, applications and packages are not the same thing.
If the above numbers are correct, it took 1253 packages to install the 499 applications. To be fully installed, each application may require several packages. Is this correct?

JBA2337

---

### Post by Sorivenul on 2008-08-15
OP, you are correct.  It may take many packages to install an actual application due to dependencies.  For example (though not the greatest), the Lazarus IDE fro FreePascal requires many FreePascal libs, and thus packages to be installed before the IDE itself will install.  Hope this helps.

---

### Post by JBA2337 on 2008-08-16
Everyone reading this post should note that the terminal commands:

dpkg -l  
produces a list of packages, showing the package name, version and
description.  

dpkg --get-selections 
produces a list of packages showing only the name of the package.

Both of the above terminal commands produce a list of all installed packages, not applications. There may be on your computer many more packages installed than applications, since some applications may require several packages to be installed to do a complete installation.

The number of packages listed by both of the above terminal commands should be the same, and this number should also be the same as the number of packages installed, as listed in the Synaptics Package Manager application.

JBA2337

---

### Post by mojoman on 2008-08-16
> **JBA2337 said:**
> Everyone reading this post should note that the terminal commands:

dpkg -l  
produces a list of packages, showing the package name, version and
description.  

dpkg --get-selections 
produces a list of packages showing only the name of the package.


Indeed. And to clarify yet some more (as this is the absolute beginners forum) for anyone reading the OP this part:
```
dpkg -l > installed_apps
``` will actually create a file named installed_apps in the current directory containing what JBA2337 described. The > is called an output redirect and will, as the name implies in neon letters, redirect from standard output (i.e. screen) to whatever output you specify (in the example, a file called installed_apps)

/mojoman

---

