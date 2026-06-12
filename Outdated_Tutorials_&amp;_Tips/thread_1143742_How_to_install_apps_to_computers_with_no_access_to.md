---
title: "How to install apps to computers with no access to the internet"
date: 2009-04-30
forum: Outdated Tutorials &amp; Tips
---

### Post by simon.hanna on 2009-04-30
I had some troubles installing apps on a pc without internet access and i did't find any post that describes an easy way to do this, so after some time i figured out how to do this...



This could be kind of messy, since it is the post i write with tipps..

"Machine 1" is the Computer with access to the internet
"Machine 2" is the Computer without Internet access

The First steps are all done on machine 1
First make sure that you empty the cached package files in Synaptic preferences, so that you don't have to search through all your downloaded packages for the one you want to install on machine 2..

Search for the package you want to install...

If you have the package already installed on machine1, you can make sure you get all the packages with the dependencies by marking the package for removal and then selecting all the packages Synaptic would remove and choose to re-install them.

If you don't have the package installed on the machine1, you can just mark it for installation.

After that press Apply and choose "download Package files only" so it wont install or re-install all the packages on machine 1..
Open Nautilus and move to /var/cache/apt/archives and copy all the deb files to a pen-drive....

Then you go to machine 2
There are two ways to continue
1.
Just double-click each .deb and install them 
or
2.
Open Nautilus with administrative rights by typing: "gksudo nautilus" without quotes in the Terminal
Again move to /var/cache/apt/archives
and paste all the deb files in there

Then you just have to open Synaptic and choose the packages you wanted to install

And you're done with installing the packages...

Simon

---

### Post by bodhi.zazen on 2009-05-06
There is also aptoncd :

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

