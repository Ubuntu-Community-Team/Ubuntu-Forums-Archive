---
title: "How do I create a deb package with basic dependencies?"
date: 2010-06-07
forum: Packaging and Compiling Programs
---

### Post by Sam Liu on 2010-06-07
Hi so I am trying to create a deb package for a web application written in Java (it uses Apache Tomcat). My eventual goal is to start a repository that people can add to apt-get the software, but

   1. How do I make it so that the package knows to look for dependencies like tomcat, sun-java6-bin, and ant?

   2. How do I write an installer script to place the files and folders in the right place?

I know this is a pretty basic question but I've scoured the web for answers and I'm just confused as a completely new package maintainer as to whether my software should have makefiles or whatever. It's Java, so it isn't compiled -- there isn't really anything to make. All that is needed is for tomcat, java, ant to be installed and then my program needs to tie in with those softwares. Kind of how like if you do

sudo apt-get install phpmyadmin

It just installs apache2, php, etc and then you can browse to localhost/phpmyadmin and have a working install of this software.

I'm not even looking as far as making a repository yet -- I just need to know how to make a debian package that will do what it needs to do when I install it. I just need it to tie in with tomcat and stuff like that :D

Thanks for your help
Sam

---

### Post by SevenMachines on 2010-06-08
hi there. it sounds like you need information on general packaging first and then java packaging second (which i am pretty much completely in the dark on!). 
The [ubuntu packaging guide]("https://wiki.ubuntu.com/PackagingGuide/Complete") will cover the general aspects of how to put your dependencies in your debian/control file, as far as i remember it also covers how to use debhelper in debian/rules and using a debian/<mypackage>.install file to install files to where they need to be.
For java packaging (heres where i get a bit hazy :) ). i'm guessing that installing javahelper and then having a look through [debian's java packaging guide]("http://wiki.debian.org/Java/Packaging") might be what you want, but i'm sure others out there will know more and better.
Its often also a good idea to get the packaging source of a similar package to yours (though i dont know which one that would be, again, others will know better) and see how other packages have done it
$ apt-get source <package>
or
$ bzr branch lp:ubuntu/<package> <package>

---

