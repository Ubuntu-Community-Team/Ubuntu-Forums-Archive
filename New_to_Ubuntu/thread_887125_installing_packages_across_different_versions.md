---
title: "installing packages across different versions"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by hbetx9 on 2008-08-11
I'm working with feisty and am working on a personal project which requires libraries only included as packages for later versions. I can't imagine the kernel updates from version to version would have a limiting factor on these packages. Specifically, I'm looking at freetype2 package libfreetype6-dev which is version 2.3.5-1ubuntu4 on hardy but is 2.2.1-5ubuntu1.1 on feisty. How does one go about installing a hardy package on a feisty install, if its even possible. If not, why not? If one offers long term support for a version of an OS, how come libraries can't be updated to versions included in later installs of the OS? 

Before anyone asks or suggests, of course the simple solution is just update to hardy and go. Yes I've thought of this, and for ( mostly lazy ) reasons, I've not done so yet. However, I'm puzzled in general why ubuntu or any linux distro would appear so limited.  

All the best,
hbetx9

---

### Post by pytheas22 on 2008-08-11
You can always download packages for different versions of Ubuntu from [http://packages.ubuntu.com](http://packages.ubuntu.com) and install them individually.  This can get messy if your packages have a lot of dependency issues, but most of the time it works pretty painlessly.

Another option, of course, is to compile the libraries you want from source.

A third solution is to switch to the Hardy repositories by adding them to your /etc/apt/sources.list file, then running "apt-get update." After that, you can find the packages that you want to update in Synaptic, and update them there.  Once you've updated the packages you need, you can revert to the Feisty repositories (if the update manager tries to force you to downgrade to earlier versions of the packages in question, you can use the "force version" option in Synaptic to tell it not to worry about this anymore).

Hope it helps.

---

### Post by hbetx9 on 2008-08-11
That seems to have worked, thanks!

---

