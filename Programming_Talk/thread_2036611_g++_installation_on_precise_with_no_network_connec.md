---
title: "g++ installation on precise with no network connection"
date: 2012-08-02
forum: Programming Talk
---

### Post by rb00012 on 2012-08-02
Hi all,

I'm currently trying to install cmake on a fresh 12.04 Ubuntu install, and I have no network connection. I've followed the list of dependencies through and what I need (amongst other things) is g++ and gawk. I currently have errors with both of these installs, however.

For gawk, I download the source package, untar and execute
```
./configure
make
make install
```and run into the error `no rule to make '../doc/gawk.texi' needed by 'stamp-eg''

I have tried installing texi2html (with success) and texinfo to resolve this, however texinfo fails with several undefined reference failures, such as tgoto, tputs, tgetnum (sorry I don't have the exact error message, I cant get this off the computer at work). I've read that these may be caused by a lack of ncurses, which requires g++. 

When trying to install g++ from source, [https://launchpad.net/ubuntu/precise/+package/g++](https://launchpad.net/ubuntu/precise/+package/g++) suggests that I need gcc-defaults, however when I extract that packageI don't know how to build it?

How should I proceed?

Thanks in advance for your help,

Rich

---

### Post by SevenMachines on 2012-08-02
Unless you've got your heart set on compiling everything from source I'd recommend instead that you look into apt-offline. It'll generate the needed package list, including dependencies, on your offline computer, which you can then download on a networked machine and transfer across

---

### Post by Bachstelze on 2012-08-02
Last time I checked (a while ago, though), the package build-essential (and all its dependencies) where included on all Ubuntu CDs. Also, I'm pretty sure awk is installed by default.

---

### Post by rb00012 on 2012-08-02
Bachstelze - I've tried installing from the DVD and checked it manually, build-essential is no longer included. I'll double check if awk is already there though.

SevenMachines - Thanks for that, looks like it could solve my problems. Out of interest though, do you (or does anyone) know how to install gcc-defaults from source?

---

### Post by pellyhawk on 2012-08-10
> **rb00012 said:**
> Bachstelze - I've tried installing from the DVD and checked it manually, build-essential is no longer included. I'll double check if awk is already there though.

SevenMachines - Thanks for that, looks like it could solve my problems. Out of interest though, do you (or does anyone) know how to install gcc-defaults from source?

gcc is not installed by default on Ubuntu?

---

### Post by Bachstelze on 2012-08-10
> **pellyhawk said:**
> gcc is not installed by default on Ubuntu?

Who said it was?

---

### Post by pellyhawk on 2012-08-10
> **Bachstelze said:**
> Who said it was?

sorry, I make a mistake.```
sudo apt-get install build-essential 
```

---

