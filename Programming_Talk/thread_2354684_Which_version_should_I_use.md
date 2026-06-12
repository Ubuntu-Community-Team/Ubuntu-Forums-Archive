---
title: "Which version should I use?"
date: 2017-03-05
forum: Programming Talk
---

### Post by fedora-refugee2 on 2017-03-05
I've been using Ubuntu Gnome for some months now but I think it is the wrong version for me. I am trying to learn programming but cannot install some libraries. When installing Enet, I get an error that tells me Cmake is not installed and something Cmake needs may not be installed as well. I don't want to install one program, then run all over the internet looking for something it needs ad nauseum. Which version of Ubuntu has the development programs bundled in, or gives an option to install them during set up? My computer uses UEFI, and I left Fedora because I couldn't get Fedora to work on UEFI, so I need a version which will install on UEFI without a problem. Thanks.

---

### Post by ajgreeny on 2017-03-05
I suspect your problem is nothing to do with the DE (Gnome) that you chose but possibly more that you are missing some of the required packages needed if you want to install from source code, though I'm not totally sure exactly what you are trying to do.

Start by installing the build-essential package which may be all that is needed.

---

### Post by ajgreeny on 2017-03-05
*Thread moved to **Programming Talk**.* which is more appropriate and a better fit.

---

### Post by vasa1 on 2017-03-05
> **fedora-refugee2 said:**
> ... When installing Enet, ...
How are you installing "Enet"? What is the source?

---

### Post by fedora-refugee2 on 2017-03-05
I tried installing build essentials but get these errors:
E: Failed to fetch [http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu/dists/yakkety/main/binary-i386/Packages](http://ppa.launchpad.net/damien-moore/codeblocks-stable/ubuntu/dists/yakkety/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
bob@Bobs-Desktop:~$ sudo apt-get install build-essentials
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials

As to enet, I got it from the enet webpage. I tried ./configure, make and make install but got errors. I don't have the errors right now. I am trying to get the development files working first.

---

### Post by ajgreeny on 2017-03-05
That ppa repository is not available for yakkety but stops at xenial, so you need to disable it from software-sources and then try again.
[https://launchpad.net/~damien-moore/+archive/ubuntu/codeblocks-stable](https://launchpad.net/~damien-moore/+archive/ubuntu/codeblocks-stable)

I assume you are running yakkety (16.10)?

---

### Post by fedora-refugee2 on 2017-03-05
I am using yakkety. It looks like you are also assuming I am using code::blocks. I was hoping to use enet from the console screen, does that make a difference? And will the ppa be available for yakkety someday?

---

### Post by ajgreeny on 2017-03-06
No idea about that I'm afraid.

I do not know either codeblocks or enet, but whatever you should disable that ppa at the moment as it is useless to you.

---

### Post by norobro on 2017-03-06
> **fedora-refugee2 said:**
> I tried installing build essentials but get these errors:
...
bob@Bobs-Desktop:~$ sudo apt-get install build-essential[COLOR=#ff0000]s[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essential[COLOR=#ff0000]s[/COLOR]
The package name is "build-essential", no "s".

---

### Post by Rocket2DMn on 2017-03-08
Also, I don't think cmake is included with build-essential (though not sure why not).  It is in the repos, but you you may need to install it separately.

---

