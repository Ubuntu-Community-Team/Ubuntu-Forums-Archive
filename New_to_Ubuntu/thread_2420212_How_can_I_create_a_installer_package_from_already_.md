---
title: "How can I create a installer package from already installed app?"
date: 2019-06-01
forum: New to Ubuntu
---

### Post by roman-sarker on 2019-06-01
Suppose I have installed an app from the store. Now, can I create an offline installer package of that app?

---

### Post by Holger_Gehrke on 2019-06-01
The store hides the fact that there are (at least) two different ways to install programs on Ubuntu: the classic Debian packages and snap.

No need to create anything if you installed the program from a snap package. 'snap' packages get put in '/var/lib/snapd/snaps/' and are run directly from the package-file. They are meant to have little or no dependencies, everything the program needs to run is in the package (unless it needs something really big, like gnome or kde. then there is a separate snap for that and the two snaps are connected through something called slots and plugs). Just copy the file(s) into some directory on the other machine and install it with 'snap install path-and-filename-of-the-package-file' in a terminal. The path is necessary, if you just give a filename snap will assume you want it to download the file from the store. Don't try to copy the file directly to '/var/lib/snapd/snaps/', snap keeps track of what is installed and gets confused if you put files there yourself. 

With .deb-packages the situation is a bit more complicated because an application is often split into multiple packages, especially if it makes use of libraries that other programs use too. Your best bet in that case is to use synaptic on the offline machine because that has an option to generate a script to download all the needed packages and a function to install packages downloaded by such a script. If you don't have synaptic on the offline machine, you can do a simulation of the installation from the command line with 'apt install --dry-run name-of-package'. Among a lot of other information this will print a list of all the packages that would be downloaded and installed. Now you can either copy the packages from the apt cache in '/var/cache/apt/archives' on the machine which has the program installed or run 'apt-get download list-of-all-the-packages' on a machine that is online and copy the packages to the offline machine and install them through 'apt install paths-and-names-of-package-files' (again, the path is necessary, for the same reason as with snap).

Holger

---

