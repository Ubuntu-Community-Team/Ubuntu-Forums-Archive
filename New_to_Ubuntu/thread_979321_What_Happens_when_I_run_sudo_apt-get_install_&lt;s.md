---
title: "What Happens when I run sudo apt-get install &lt;software&gt; ??"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by pietrop on 2008-11-11
Hello everybody.

I have a curiosity about what happens when I run a ***sudo apt-get install <software>*** command.

For instance I ran ```
sudo apt-get install nedit
``` and Ubuntu downloaded it and installed it, and now if I run nedit in a shell it works fine and all.

What I'd like to know is where does Ubuntu specifies that the command nedit is going to run that specific software(in the .bashrc???), where all the install files go and stuff like that.

Is there a page that I could read about it?? 

Any help or explanation is much appreciated!!

Thanks,

pietro

---

### Post by Living2007 on 2008-11-11
I'm not entire sure i know everything that your asking but, Ubuntu know what software you want when you type the command because when the 'apt' or Software Manager searches for software on a set of site provided, and updates it everytime you open "Add/Remove Programs" or type the command "sudo apt-get ..."

---

### Post by jimmy the saint on 2008-11-11
The software "Apt" pulls the software from the repositories (which are like free warehouses of software) and installs it.  It also tracks it so that when you want to remove or upgrade the software, it can do it automatically.  Think of it as a buddy that finds, downloads, installs, upgrades, tracks, uninstalls and tracks all of your software for you whenever you ask him to.

---

### Post by SunnyRabbiera on 2008-11-11
apt-get install is actually the standard graphical and command line way of installing applications in ubuntu.
Add/remove and synaptic are front ends to apt, they provide a grapical interface to work with.
Apt just installs things more directly

---

### Post by -Zeus- on 2008-11-11
most files are installed to /usr/bin.  To see a list of all folders that have installed items, you can type this:
```
echo $PATH
```
This will tell you everywhere that the shell interpreter (dash) looks for to start a program

---

### Post by pietrop on 2008-11-11
Thanks All!!

It's becoming more clear...

@-Zeus-
Is it then correct to say that whatever software I install (put) in one of the folders listed in the $PATH variable gets automatically picked up by the shell interpreter??
By the way what is this shell interpreter (dash)??

Thanks a lot for the quick answers!!

Cheers

pietro

---

### Post by drs305 on 2008-11-11
> **pietrop said:**
> ... *where all the install files go and stuff like that.*

You can see where a packages files are installed by running the following:
```
whereis *packagename*
```
For example, "whereis gimp" returns:
gimp: /usr/bin/gimp /etc/gimp /usr/lib/gimp /usr/share/gimp /usr/share/man/man1/gimp.1.gz

You can learn the run command with:
```
which *packagename*
```
Example: which gimp
/usr/bin/gimp

You can also see a package's files by opening synaptic, highlighting the package, right clicking, "Properties", Installed Files.

---

### Post by zvacet on 2008-11-11
If you want to know how apt works go [here]("http://www.debian.org/doc/user-manuals") and you will find manual.All about where are instaled packages and other things you can find [here.]("http://www.pathname.com/fhs/")

---

### Post by pietrop on 2008-11-11
Thanks a lot for all these answers, they are really useful!!

I'll get my head around now, and read through the docs Zvacet suggested!!

Cheers guys 

pietro

---

