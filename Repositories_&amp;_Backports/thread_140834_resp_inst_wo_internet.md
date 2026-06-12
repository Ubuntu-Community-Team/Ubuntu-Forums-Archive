---
title: "resp inst w/o internet"
date: 2006-03-07
forum: Repositories &amp; Backports
---

### Post by anandam on 2006-03-07
Hi everyone,

I am using Ubuntu 5.10.
I want to install the  universal repository but don't have internet on my computer.How should I go about?

---

### Post by aysiu on 2006-03-07
The Universe repository is huge. It would take a *very* long time to download the entire repository, and then that would not fit on a CD.

This may help you:
[https://wiki.ubuntu.com/AptMoveHowto](https://wiki.ubuntu.com/AptMoveHowto)

Out of curiosity, why doesn't your Ubuntu computer have an internet connection? Maybe that should be your primary concern.

---

### Post by alamba on 2006-03-07
Uhhh...download the packages (.deb) you want on another PC...transfer to your PC....dpkg -i <package_name>

A

---

### Post by aysiu on 2006-03-07
[QUOTE=alamba]Uhhh...download the packages (.deb) you want on another PC...transfer to your PC....dpkg -i <package_name>

A[/QUOTE] Don't forget their dependencies, too.

---

### Post by anandam on 2006-03-07
Thanks aysiu and alamba.

Let me reframe my question.How should I add repositories in Synaptic Package Manager (w/o internet).
Now, please answer.

---

### Post by aysiu on 2006-03-07
[QUOTE=anandam]Thanks aysiu and alamba.

Let me reframe my question.How should I add repositories in Synaptic Package Manager (w/o internet).
Now, please answer.[/QUOTE] All the repositories right now are on the internet, so there's almost no point in adding them. Right now, [I'm working with some other folks on the forum to get an add-on CD](http://www.ubuntuforums.org/showthread.php?t=136955) for Ubuntu.

In the meantime, you have these options:
1. Get your internet working on Ubuntu
2. Download individual .deb files (and their dependencies) on another computer and then install them manually
3. Do the AptMove HowTo and create your own Add-On CD.

---

### Post by aysiu on 2006-03-07
Someone just pointed out that there's an Italian add-on CD. Some of the packages are for Italian localization, but others are just extras.

The translated page (along with instructions for how to use it) can be found [here](http://translate.google.com/translate?u=http%3A%2F%2Fwww.zipman.it%2FUbuntuPiu%2F&langpair=it%7Cen&hl=en&safe=off&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools).

The .ISO of the extras CD can be found [here](http://www.zipman.it/UbuntuPiu/ubuntupiu5.10-3.iso).

---

### Post by anandam on 2006-03-08
Thanks aysiu.

"2. Download individual .deb files (and their dependencies) on another computer and then install them manually."

But suppose I want to install Totem xine, how and from where should I get the required .deb files along with all its dependencies.That also when I don't know on which other files it depends!! 

Yes, what's it?

---

