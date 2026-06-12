---
title: "Strange errors installing GnuPG"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by EccentricCircle on 2012-02-04
I'm utterly new to Linux and Ubuntu. To give you some idea, I needed YouTube to show me how to find the terminal. I'm running Ubuntu inside a virtual box on Windows 7, and trying to install GnuPG for work. 

So I figured out installing all the necessary libraries, but I'm still getting an error message running the "make" command on the original GnuPG package. The error message is 

make[2]: *** [gpg2] Error 1
make[2]: Leaving directory `/home/davi/Downloads/gnupg-2.0.18/g10'

I'm at a loss. On top of that the Ubuntu Software Center says GnuPG is already installed, only I can't find it or figure out how to run it. It doesn't come up in an application search. Does anyone know either how to resolve that error message, or how I access GnuPG if it is already installed?

Appreciate it.

---

### Post by kevdog on 2012-02-04
Couple of things

Gpg comes in two flavors -- version 1 (gpg) and version 2 (gpg2).  Unless you are working with key based authentication mechanisms, I'm betting you actually want to use plain old gpg (gpg or version 1).  I have no idea what your error is with gpg2 compilation based on what you posted -- but it has likely to do with po files which are internationalization -- which always give me errors as well.  

You can see if gpg is installed de facto by just typing gpg --version at the command line.  You get something back -- its installed.  If not install it -- sudo apt-get install gnupg   
or if you really want version two -- sudo apt-get install gnupg2

---

### Post by ikt on 2012-02-05
> **kevdog said:**
> If not install it -- sudo apt-get install gnupg

Just in case the OP sees this.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

> Most Windows users who migrate to Ubuntu end up confused about software installation. They go to a website, download a .tar.gz file, double-click it, and don't see a Next-Next-Next-Finish wizard. This tutorial is intended to introduce you to the preferred methods of software installation in Ubuntu.

---

### Post by EccentricCircle on 2012-02-06
> **kevdog said:**
> Couple of things
You can see if gpg is installed de facto by just typing gpg --version at the command line.  You get something back -- its installed.  If not install it -- sudo apt-get install gnupg   
or if you really want version two -- sudo apt-get install gnupg2

I think I understand, but I just want to double check before I break something. By "command line" do you mean the terminal? My understanding is that commands need to be given in a specific directory. Is that just a general command from the root directory?

Are you saying that entering "sudo apt-get install gnupg" as a command in the root directory will install the whole thing?

---

### Post by EccentricCircle on 2012-02-07
They changed my name from MuslimAgorist to EccentricCircle because MuslimAgorist was offensive I guess. But it's still me, and I'm still having the same problem.

I entered "gnupg" in the "command line" which I'm assuming is the terminal and it came back:

[INDENT]No command 'gnupg' found, did you mean:
Command 'gnubg' from package 'gnubg' (universe)
gnupg: command not found
[/INDENT]
I tried entering "sudo apt-get install gnupg" and it came back:

[INDENT]sudo: apt: command not found[/INDENT]

Does anyone have any other suggestions? I've about exhausted all my options at this point. Is there someone here who actually uses this program?

---

### Post by EccentricCircle on 2012-02-07
> **ikt said:**
> Just in case the OP sees this.

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

I've already followed these instructions, which is why I'm confused. When I go the Software Center and search for GnuPG it comes up as already installed, which is strange because I never successfully installed the package I downloaded using the terminal. However, when I go to the "Dash Home" in the top left and search for the installed program nothing comes up. So, I have no indication of where the program is installed, or how to run it if it is actually installed.

---

### Post by oldos2er on 2012-02-08
The gnupg package contains four programs meant to be run in a terminal; gpg, lspgpot, gpgsplit, and gpg-zip. CLI (command line interface) programs will not have a menu entry.

If you're looking for a GUI front-end to gnupg, there's a package in the repositories called **seahorse** that may fit your needs.

---

