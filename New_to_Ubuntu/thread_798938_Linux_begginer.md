---
title: "Linux begginer"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-18
Hello all.

   I am new to linux, so I have ALOT o questions.First of all, what are the differences between the linux distributions.For exemple, Ubuntu and Fedora look the same for me (btw, I use Ubuntu).Ubuntu looks great, and runs great and the only thing I use dual boot with windows are games.So, here is my problem...Did you hear something about a program called VirtualBox?What does it do?Can I use it to play windows games?And if yes, how?
   Another problem I have is installing source packeges (those with the extension tar.gz).The problem is... I can't install any of them.I red the post "How to install anything in Ubuntu" and it still doesn't work.I extract the package, switch to that directory and when I type ./configure I get the messenge "no such file or directory".According the that post it doesn't matter, but when I type "make" it says "no make file found.stop".What is the problem?Can someone help me please?
Thx alot and excuse my noob-idity :).

---

### Post by FreewheelinFrank on 2008-05-18
I came across this link which might be useful. It doesn't go into the differences between distros, but into differences between users that might make a particular distro more appropriate, from which of course you can infer some differences between distos. 

[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)

It might help if you mention exactly what you're trying to install, regarding the third part of your question.

---

### Post by spiderbatdad on 2008-05-18
Not all tar packages have configure files. You need to enter the directory you extracted from the package and look for ReadMe and Install files for instructions on how to run or compile the package. Or find instructions from the download location. If possible find packages that are .deb and check synaptic first.

---

### Post by hyper_ch on 2008-05-18
it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by sdennie on 2008-05-18
Virtualbox is virtualization software that allows you install and run guest operating systems within a virtual machine.  So, you can literally install Windows in a virtual box virtual machine but, because it emulates a graphics card, you probably won't be able to play most games.  One thing you may want to check is wine: [http://www.winehq.org/](http://www.winehq.org/).  Using wine, some popular games can run on linux without the need for Windows at all.

---

### Post by RiceMonster on 2008-05-18
The reason why you're getting "no such file or directory" is because you're not in the directory of where you extracted the .tar.gz file. I would avoid compiling from source though. The best way to install is through applications > add/remove (easy) or system administration > synaptic package manager (more advanced). There you'll have tons of software in-which you can click on what you want, then click "apply changes" and it will download and install it for you automatically.

If whatever you want to install is not available in synaptic or add/remove, then try and download a .deb file of what you want to install. All you have to do is double click on it and it will install. Downloading a tar.gz and compling from source should be your last option.

---

### Post by phread59 on 2008-05-18
The big differences between say Ubuntu and Fedora is which branch of Linux they come from.  There are 2 basic branches (I won't get into Gentoo and others) of Linux- Debian and Red Hat.  They are almost the same.  the big differences are the way packages are handled.  Ubuntu a Debian derivative uses Synaptic as it's main package manger.  Fedora uses Yum.  They are different enough that they are inherently not compatible.  You can convert the Red Hat RPM packages to a Debian format.  But it involves translating them.

Basicly it comes down to how software is arranged and handled.  I like Debian for it's ease of use.  RPm packages have a history of being difficult to work with.  The dependancy's (programs that support the one you are installing and allow it to work) are difficult to get right with RPM packages.  Debian really does not have these issues.So there you have it in a nutshell.

Mark Shuman

---

### Post by dasunsrule32 on 2008-05-18
> **phread59 said:**
> The big differences between say Ubuntu and Fedora is which branch of Linux they come from.  There are 2 basic branches (I won't get into Gentoo and others) of Linux- Debian and Red Hat.  They are almost the same.  the big differences are the way packages are handled.  Ubuntu a Debian derivative uses Synaptic as it's main package manger.  Fedora uses Yum.  They are different enough that they are inherently not compatible.  You can convert the Red Hat RPM packages to a Debian format.  But it involves translating them.

Basicly it comes down to how software is arranged and handled.  I like Debian for it's ease of use.  RPm packages have a history of being difficult to work with.  The dependancy's (programs that support the one you are installing and allow it to work) are difficult to get right with RPM packages.  Debian really does not have these issues.So there you have it in a nutshell.

Mark Shuman

You are almost correct, debian is based on *.deb packages and redhat is based on *.rpm, red hat uses yum; however, debian is based on apt for it's package manager that will resolve dependencies, then will call dpkg to actually do the runtime and install. Synaptics is merely a front end for apt, just like aptitude is a front end for apt. Hopefully that helps clear things up.

---

### Post by kubaknopp on 2008-05-18
abouut virtual box - this is my little clip on youtube showing what actually 
Virtual box is for. [**VBox clip**]("http://www.youtube.com/watch?v=xGI5lOOqMEA")

---

### Post by Troll_the_Great on 2008-06-14
1

---

