---
title: "c++ ( and geany ) compile problem ( missing g++ )"
date: 2013-01-14
forum: Packaging and Compiling Programs
---

### Post by pieprzmak on 2013-01-14
Hello.
I've got realy huge problem. I left my home for winter break and I installed ubuntu on pen drive. I tried to compile any program in geany or using terminal, but geany says there is no g++ and same in terminal. I borrowed a modem for a time I'll spend here and here comes main problem. I can only use it on windows, because I don't know user or password to connect and windows doesn't require it to connect, but on ubuntu it asks for a user etc. It wouldn't be a problem if I could download .deb package and install it on ubuntu. But I can't, because when I try to install it, it says that I have to install it from a trusted source or something ( I don't remember exactly). So, is there any possible way to install missing programs? Because I wanted to read my c++ book and time runs fast.

Thanks for help, pieprzmak.

---

### Post by linuxonbute on 2013-01-15
Are you sure you cannot install it.
As far as I know it says you should only install from trusted sources. It does not say you are not allowed to.

---

### Post by TheFu on 2013-01-15
> **pieprzmak said:**
> Hello.
I've got realy huge problem. I left my home for winter break and I installed ubuntu on pen drive. I tried to compile any program in geany or using terminal, but geany says there is no g++ and same in terminal. I borrowed a modem for a time I'll spend here and here comes main problem. I can only use it on windows, because I don't know user or password to connect and windows doesn't require it to connect, but on ubuntu it asks for a user etc. It wouldn't be a problem if I could download .deb package and install it on ubuntu. But I can't, because when I try to install it, it says that I have to install it from a trusted source or something ( I don't remember exactly). So, is there any possible way to install missing programs? Because I wanted to read my c++ book and time runs fast.

Thanks for help, pieprzmak.

So you have 2 issues (at least).

[LIST=1]
[*]internet connectivity under Ubuntu
[*]how to load a C++ development environment under Ubuntu
[/LIST]
We can't help solve #1 with the data provided. We need to know how you are trying to connect, since most of us have a small network at home and connect to a router which manages the entire internet connection. Any device that can plug into the router is on the internet. Could you be trying to connect to a router using wifi and just not know the SSID and passphrase? 



As to #2, setting up a C++ development environment, that will be difficult without an internet connection. There are many dependencies that Ubuntu will automatically resolve.  You'll want more than just the compiler. You need build tools, standard libraries, any additional libraries that your specific book wants, plus lots of knowledge.


I'd start with these packages:

[LIST]
[*]g++
[*]libstdc++6
[*]build-essential
[*]automake
[*]make
[/LIST]
You'll need to find those .DEB package files from the repository for your specific version of Ubuntu, plus any dependencies.  If your book teaches GUI programming, you'll want those GUI tool as well.


Another option is to use Windows and a development environment on that platform. There are a number of all-in-one C++ environments based on the GNU tools available for MS-Windows. This isn't really the place to ask for help on that, but here are some options:

* [http://www.codecutter.net/tools/quincy/](http://www.codecutter.net/tools/quincy/) 

* [http://codeblocks.codecutter.org/](http://codeblocks.codecutter.org/)


I've never used either. Both are free and meant for students.

---

### Post by pieprzmak on 2013-01-15
Ok, thanks guys for help.

On windows I just connect modem to usb port and it connects automatically ( phone web or sth ) without giving it any authorization. But I won't try to do same on linux. I've known about codeblocks and I will use it. Thanks again :)

---

