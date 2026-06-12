---
title: "Installing Anjuta-2.30"
date: 2010-09-04
forum: Programming Talk
---

### Post by Searock on 2010-09-04
I have recently downloaded anjuta-2.30.2.1 form [http://anjuta.org/downloads.html](http://anjuta.org/downloads.html).

I don't know how to install it. I have tried running install-sh from the installation folder, but it says no input file specified..

So how do I install anjuta?

Thanks

---

### Post by madverb on 2010-09-04
sudo aptitude install anjuta

---

### Post by Searock on 2010-09-04
> **madverb said:**
> sudo aptitude install anjuta

But what about the installation files I have downloaded ? How do I install it from the installation files?

and what does aptitude mean ? I have installed applications using sudo app get application. Actually I am not much familiar with Ubuntu

**EDIT : **Ok I have tried running sudo aptitude install anjuta

It gives me an error.

> searock@searock-desktop:~$ sudo aptitude install anjuta
Reading package lists... Done
Segmentation faulty tree... 50%
searock@searock-desktop:~$What does this error mean ?

**EDIT 1 :**  When I try to run ./autogen.sh file from the directory, it gives me an error.

> searock@searock-desktop:~/Downloads/anjunta/anjuta-2.30.2.1$ ./autogen.sh 
You need to install gnome-common from the GNOME CVS
searock@searock-desktop:~/Downloads/anjunta/anjuta-2.30.2.1$ 

Now how do I install  gnome-common and what is  gnome-common?

---

### Post by madverb on 2010-09-05
If you want to install anything on Ubuntu you do it using the package manager. You can use a GUI like Synaptic which you can find under System > Administration.
There are a few command line programs to use. Most common is apt-get and then there is aptitude that I said. Doesn't really matter which client you use they all do the same thing.
You just need to do a small amount of reading into installing software on Ubuntu.
I think you have damaged something somewhere in trying to install Anjuta manually.
You should only need to install something manually if you can't find it by searching in Synaptic or using the commands:
```
sudo apt-cache search <search terms>
sudo aptitude search <search terms>
```

---

