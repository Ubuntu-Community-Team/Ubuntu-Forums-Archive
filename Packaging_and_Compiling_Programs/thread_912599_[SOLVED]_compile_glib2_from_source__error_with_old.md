---
title: "[SOLVED] compile glib2 from source / error with old glib"
date: 2008-09-06
forum: Packaging and Compiling Programs
---

### Post by Claus7 on 2008-09-06
Hello,

Reading psychocats web site about installing a new program in ubuntu, it sais that the best way to do so, is to use synaptic. It also refers to compiling a program from source, yet more or less suggests that it's better to receive some help while doing this task.

I compiled glib2.16.3 with the :
./configure
make
make install
process, yet when I try to install the pygobject-2.14.2 library I get this :

checking for GLIB - version >= 2.8.0...
*** 'pkg-config --modversion glib-2.0' returned 2.16.3, but GLIB (2.10.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: maybe you want the pygobject-2-4 branch?

Searching the net and ubuntu forums I get no specific process of avoiding this error. Either someone can resolve this by going to synaptic or just setting the /usr/local/lib in /etc/ld.so.conf and running ldconfig.

The problem in Dapper is that such kind of file doesn't exist and that I cannot use synaptic to install any of the aforementioned libraries. 

What I do care about, is to learn how such a library can be updated (upgraded-install the new version and unistall the old one-just install the new version in another folder-install the new version exactly as I have done and somehow inform the system about the new version!) without any problem. 
I think that the unistallment of the previous version is not the best one, as in synaptic a lot of programs depend on that. Is there any way of solving this issue without having to upgrade to another version of ubuntu or damaging my system?

Thank you, 
Regards!

---

### Post by InfinityCircuit on 2008-09-09
Running a blind make install on a brand new version of glibc that is 6 versions newer than your current version was a gigantic mistake.  It is basically impossible to backport a newer glibc to older releases.

If it installed the new libraries in /usr/local, then it's possible that the old glibc is on your system still and being used because /usr is before /usr/local in your $PATH.

---

### Post by Claus7 on 2008-09-10
Hello,

> **InfinityCircuit said:**
> Running a blind make install on a brand new version of glibc that is 6 versions newer than your current version was a gigantic mistake.  It is basically impossible to backport a newer glibc to older releases.

So what you suggest here is just go and upgrade the version of ubuntu? Yup, that should be reasonable. Yet, I haven't faced any other dependency issue (at least the installation goes ok) and I wish not to make a fresh install yet. I would like to experiment a little. 
Now, its better to install the newer version of glib above the old one or in a brand new folder? My intention was that with ubuntu I can "play" with the kernel. And I do not do much (at least this is what I think) by just upgrading a library in the end. How with the intallation of a brand new glib, all the other programs will realise that :"Hey, a new version exists, just pick it up"?

> **InfinityCircuit said:**
> If it installed the new libraries in /usr/local, then it's possible that the old glibc is on your system still and being used because /usr is before /usr/local in your $PATH.

If this is the case then I would imagine that the version of glib that a program finds first via the $PATH library, should be the one being used (if I do not give a path via configure). At least this is the case, when a command is invoced. Why it finds both versions and that way I get a conflict?

Thank you,
Regards!

---

### Post by Claus7 on 2008-09-19
Hello,

I downloaded the latest glib2 from here :
[http://ftp.acc.umu.se/pub/GNOME/sources/glib/](http://ftp.acc.umu.se/pub/GNOME/sources/glib/)

I compiled it with :
./configure
sudo make
sudo checkinstall

Now in order to avoid the afforementioned problem with pkg-config I read this :
[http://www.linuxquestions.org/questions/linux-software-2/pkgconfigpath-230545/](http://www.linuxquestions.org/questions/linux-software-2/pkgconfigpath-230545/)

and what worked for me was to do this :
export LD_LIBRARY_PATH=/usr/local/lib

Regards!

---

### Post by InfinityCircuit on 2008-09-19
```
My intention was that with ubuntu I can "play" with the kernel. And I do not do much (at least this is what I think) by just upgrading a library in the end. How with the intallation of a brand new glib, all the other programs will realise that :"Hey, a new version exists, just pick it up"?
```

Your version of libc6 has very very very little, if anything, to do with playing with the kernel.  Upgrading versions of core system libraries isn't as simple as you think, especially if they are hand-compiled.  If there is a new change in the latest version of the library, older programs have NO idea how to "just pick it up."  The general rule of thumb is to never hand compile gcc or glib (even OpenBSD recommends rebasing against a new snapshot instead).  You should just upgrade to Intrepid if you want to "play with the newest glibc" or install it in a chroot jail.

Also, don't run sudo make--you don't need root privileges to do this.

---

### Post by Claus7 on 2008-09-20
Hello,

> **InfinityCircuit said:**
> 

Your version of libc6 has very very very little, if anything, to do with playing with the kernel.  Upgrading versions of core system libraries isn't as simple as you think, especially if they are hand-compiled.  If there is a new change in the latest version of the library, older programs have NO idea how to "just pick it up." 

I think that there is a tool where you can inform libraries when something like this happens.


> **InfinityCircuit said:**
> The general rule of thumb is to never hand compile gcc or glib (even OpenBSD recommends rebasing against a new snapshot instead).  You should just upgrade to Intrepid if you want to "play with the newest glibc" or install it in a chroot jail.

I didn't care so much, because I was already thinking to upgrade. Yet, just before doing so, I wanted to experiment a little. I found out about export for example... Why intrepid (the new version of ubuntu) will enable me to play better with the kernel?

> **InfinityCircuit said:**
> Also, don't run sudo make--you don't need root privileges to do this.
Yup, sometimes I did it the one way and sometimes with the other. I think that without root priviledges, in some folders you cannot install a new library. What I undersand from what you are saying is that changing or installing manualy these libraries, just do it in another location from the "original" one.

NOTICE: above I give a command with export. In order for it to work you go to the folder you want to install the new packadge and before configure you type that command. 

Regards!

---

