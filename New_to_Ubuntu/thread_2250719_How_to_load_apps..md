---
title: "How to load apps."
date: 2014-10-30
forum: New to Ubuntu
---

### Post by David_C._Hallam on 2014-10-30
I am a complete novice to linux.  I have looked at the list of installed applications and see are a large number.  I have no idea to access them to use.  How do I do it?

---

### Post by slickymaster on 2014-10-30
Hey David_C._Hallam, welcome to the forums.

I strongly advise you to start by having a read at the [Ubuntu Desktop Guide]("https://help.ubuntu.com/14.04/ubuntu-help/index.html"). This guide is designed to answer your questions about using Unity and your Ubuntu desktop.

---

### Post by nerdtron on 2014-10-30
If you want to launch an application, you can click on the icon on the side bar of Ubuntu. If the application is not there, you can press the Start button (the windows key on the keyboard) and type the name of the application, then double click it to launch.

If you want to search and install new application for your computer, Open the Ubuntu Software Center and start searching/installing apps.

---

### Post by adj3 on 2014-10-30
Hi David,

If you click on the Ubuntu icon on the top left and search for a software name you can find it there.

A bit off topic but useful commands:

To search the repositories for a particular package -----> sudo apt-cache search [package name]
If you find any package to your liking run the following to install it -----> sudo apt-get install [package name]
To list all packages installed on your machine ------> dpkg -l 

Regards

---

### Post by David_C._Hallam on 2014-10-30
> **adj3 said:**
> Hi David,

If you click on the Ubuntu icon on the top left and search for a software name you can find it there.

A bit off topic but useful commands:

To search the repositories for a particular package -----> sudo apt-cache search [package name]
If you find any package to your liking run the following to install it -----> sudo apt-get install [package name]
To list all packages installed on your machine ------> dpkg -l 

Regards

OK  That solved my problem.  Thanks

---

### Post by oldos2er on 2014-10-30
> **adj3 said:**
> Hi David,

If you click on the Ubuntu icon on the top left and search for a software name you can find it there.

A bit off topic but useful commands:

To search the repositories for a particular package -----> sudo apt-cache search [package name]
If you find any package to your liking run the following to install it -----> sudo apt-get install [package name]
To list all packages installed on your machine ------> dpkg -l 

Regards

Just FYI, apt-cache commands do not require sudo.

---

