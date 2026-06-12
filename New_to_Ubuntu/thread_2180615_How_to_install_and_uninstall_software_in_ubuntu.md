---
title: "How to install and uninstall software in ubuntu"
date: 2013-10-13
forum: New to Ubuntu
---

### Post by Aeront on 2013-10-13
I am just new here, and a totally beginner in ubuntu. Could you give me some stuff on how to install an uninstall software in ubuntu? Is it possible to install a software in a specified directory in ubuntu? Thank you.

---

### Post by Bashing-om on 2013-10-13
Aeront; Hi ! Welcome to the forum .

Installing software for ubuntu is a simple as selecting what you want in the "Software Center" and selecting install.(there are 35,000 + packages available there) The package management system will take care of ALL details. Once you have progressed past "new user" stage there are other means to install software. Mainly then through a PPA (Personal Package Archive). Even then the package manager takes care of the installation. You will rarely have to be concerned with what file is installed where. Lastly is for the very advanced user, to compile from source and install .. even then the package manager will take care of the majority of the details.

and:
> 
Is it possible to install a software in a specified directory in ubuntu?

Nope, Once you are familiar with the file system, you will understand why. It has to do with shared resources and the system has to know what is installed where. There are checks and balances in place to insure all files are installed properly and in the correct place.

(Un-)install: if installed via the Software Center, then - simply - remove from that resource. PPA removal is a different procedure, as well a manual installation to remove takes an intimate knowledge of "dpkg" and "apt-get" to affect that removal from the system.

Coming to ubuntu (linux) from another operating system to become comfortable is a steep learning curve, once you are beyond the "point click" stage. There is a different mind set ! With time and patience you will come to agree this is the greatest operating system the world has ever seen ! Now is the time it is spreading wings and preparing to fly !

Hang in there, ask and seek -> here there is no such thing as a dumb question.
Above all; great documentation but;:: this is a constantly evolving operating system, what was yesterday may no longer apply !

[INDENT][INDENT]seek earnestly and you will find
[/INDENT][/INDENT]

[INDENT][/INDENT]

---

### Post by harrypotter7 on 2013-10-14
**synaptic packet manager** for uninstalling its the best out there and** software center** for installing never ever add unknown PPA............

---

### Post by oldos2er on 2013-10-14
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

[https://wiki.ubuntu.com/SoftwareCenter](https://wiki.ubuntu.com/SoftwareCenter)

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by whitesmith on 2013-10-14
If you write your own code, then you **can** put it wherever you want. I have a ~/bin directory for scripts and other stuff I've written..

---

### Post by moshefeit on 2013-10-14
You can use terminal with:

> sudo apt-get purge #Software Name, with directory if needed#

---

### Post by angelsimon on 2013-10-14
Hi, I always use **Ubuntu Software Center **to install/uninstall software. Another way to do that is using commands in the Terminal. For example you can install software by writting:
[FONT=courier new]sudo apt-get install <package-name>[/FONT]

You can uninstall software by writting:
[FONT=courier new]sudo apt-get remove <package-name>[/FONT]

---

### Post by Queram_Onog on 2013-10-14
If I may join in; this 'all over the place' and 'wherever you want' is actually even more confusing than stating 'it needs to go to /bin'.
Say at work we have a linux cluster, all software executables (and some/many more files) are neatly stored/installed in /apps/software/version; every user can go there, have a look, and point his personal alias to the right location/file.
If in Ubuntu installed files go into various places where am I supposed to look? How can I set up my own alias?
Sure, with software installed manually I can do as I please but those installed through soft centre....

---

### Post by ian-weisser on 2013-10-14
Why would you need your own alias? Simply use the executable.

If you *really* want to know where the executable is installed, dpkg will tell you.
For example, the *hello* package installs the executable to /usr/bin/hello
```
~$ dpkg -L hello
/.
/usr
/usr/bin
/usr/bin/hello
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/hello.1.gz
/usr/share/info
/usr/share/info/hello.info.gz
/usr/share/doc
/usr/share/doc/hello
/usr/share/doc/hello/NEWS
/usr/share/doc/hello/copyright
/usr/share/doc/hello/changelog.Debian.gz

```

---

### Post by Impavidus on 2013-10-15
The applications themselves usually go into /usr/bin. This directory is automatically searched whenever you try to run a command. Sometimes they're somewhere else, but in that case the installation script/package should leave a symbolic link or a script in /usr/bin, pointing to the place where the binary is installed.

Libraries specific to the application are usually in /usr/lib/applicationname. Libraries are stored together because this makes it easier to share libraries amongst several applications. Data files common to all users usually are in /usr/share/applicationname. This way, the shared data files can be for example on a network drive used by several computers, which all have their own libraries and executables, because some may be 32 bit, others 64 bit and others not Linux systems at all. The application should know where to look for them, so don't bother.

User files are somewhere in (a subdirectory of) the user's home directory, in which case the user should know where to find them, or in ~/.applicationname or ~/.config/share/applicationname, in which case the application should know where to look. This is the only place where the user has write access and it makes it easier to move the data to network storage, independent of the machine.

---

### Post by Queram_Onog on 2013-10-15
ian-weisser:
well, there may be several versions of the same software, all having the same executable name.... or may get fed up with typing 'starccm -server -load testcaseA' 50x a day... and modifying .bashrc beforehand to use the right version....
but thanks for that dpkg tip, did not know it.

impavidus:
thanks for this, it does support what I thought but in some cases the logic did not hold true... cann't verfy that right now, but after the big reinstall...

---

### Post by ian-weisser on 2013-10-15
apt-based systems like Debian and Ubuntu generally don't play well with multiple versions of the same package.
It's not a supported apt use case. Apt assumes that your needs are simple enough to require only one version of the package.
You can immediately see why: Each package has specific paths to install to. Multiple packages will overwrite each other. That's deliberate, to make upgrading easy.

I suspect you have already discovered that. If you need to install multiple versions of software, you will need to install them -and many of their versioned dependencies- manually.

---

