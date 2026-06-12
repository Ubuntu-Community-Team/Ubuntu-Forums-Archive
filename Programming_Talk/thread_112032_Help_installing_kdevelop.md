---
title: "Help installing kdevelop"
date: 2006-01-03
forum: Programming Talk
---

### Post by the_c on 2006-01-03
Since it's related to prgramming, I'm posting it here.

Hi there.
I'm having problems installing kdevelop, and I'm hoping that someone can help me out. (Oh,- I'm using Kubuntu 5.10 by the way)

I have downloaded the Current stable version (3.3.0), and trying to follow the instructions at [http://www.kdevelop.org/index.html?filename=branches_compiling.html](http://www.kdevelop.org/index.html?filename=branches_compiling.html)

When i type:
make -f admin/Makefile.common cvs-clean

I get this error:
make: *** No rule to make target `cvs-clean'.  Stop




And what about the first section in the instructions:
Checkout SVN module "kdevelop" at svn://anonsvn.kde.org/home/kde/

    * command line for HEAD branch:

          $ svn co svn://anonsvn.kde.org/home/kde/trunk/KDE/kdevelop/ kdevelop

    * command line for KDE/3.5 branch:

          $ svn co svn://anonsvn.kde.org/home/kde/branches/KDE/3.5/kdevelop/ kdevelop

To get another branch, replace KDE/3.5 with the name of the branch you want. 

--> Can somone explain what they are talking about.

---

### Post by the_c on 2006-01-03
Never mind. Installed it using
sudo apt-get install kdevelop3  :)

---

