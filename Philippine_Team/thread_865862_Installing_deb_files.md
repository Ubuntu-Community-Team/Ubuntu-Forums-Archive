---
title: "Installing deb files"
date: 2008-07-21
forum: Philippine Team
---

### Post by patoy on 2008-07-21
I'll post the deb files I installed. Currently tried installing it on version 7.10

Why install using deb?
A: still don't have an active internet connection and it's much easier to install compared to using compile.

To enable mp3 files to play in rhythmbox player: download [gstreamer0.10-fluendo-mp3 (0.10.5.debian-1)]("http://packages.ubuntu.com/gutsy/gstreamer0.10-fluendo-mp3")

in terminal type: **sudo dpkg -i package_file.deb**

[Commands to install deb files]("https://help.ubuntu.com/7.10/add-applications/C/install-file.html#install-deb")

Download deb packages [here]("http://packages.ubuntu.com").

Next to install is wine. If you have some apps that's needed to be installed, i-enter nyo lang. hehe.

---

### Post by loell on 2008-07-21
you have a misconception about deb files. 

far too often, new users think that deb packages are like **exe** installers or **msi** installer files

its a bit long to fully explain, but do try other packages, i'm sure you'll encounter error messages shortly, like **unsatisfiable**. ;)

and actually, you can just double-click the deb file to install it.

---

### Post by echo2knight on 2008-07-21
Actually, DEB (for linux based on debian) or RPM (for red hat based) files are compilations of scripts that make installing software much easier. It minimizes what we call dependency hell.

Para na ring EXE or MSI in windows, but these files act differently.

---

### Post by loell on 2008-07-21
exes and msi do manage dependencies too, bet not as efficient as the linux packaging counterpart,  

so yeah, in way they have similarities with exe and msi installers,  

my previous point was, deb packages are not like self contained exe installers that you could just take home and install it without any problem on a not online machine.

---

### Post by patoy on 2008-07-21
yup. other deb packages will require other dependencies.

---

### Post by kikoman on 2008-07-21
Its the FAQ from Windows users, "where is the .exe files?" so for easy explanation we just call it .deb.

---

### Post by echo2knight on 2008-07-22
You guys got that right!!!!

---

### Post by patoy on 2008-07-30
algthough mahirap talaga pag walang internet. saw an article about [Installing Applications in Ubuntu without Internet]("http://planetoss.com/detail.php?id=13").

---

### Post by sstusick on 2008-07-30
> **loell said:**
> exes and msi do manage dependencies too, bet not as efficient as the linux packaging counterpart,  

so yeah, in way they have similarities with exe and msi installers,  

my previous point was, deb packages are not like self contained exe installers that you could just take home and install it without any problem on a not online machine.A lot of "exe installers" often require other dependencies as well, which aren't included in the installer.

---

### Post by loell on 2008-07-30
> **sstusick said:**
> A lot of "exe installers" often require other dependencies as well, which aren't included in the installer.

true, which is usually included in the CD.

---

