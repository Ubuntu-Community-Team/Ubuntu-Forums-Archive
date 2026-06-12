---
title: "saving installed packages"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by schmidtbag on 2008-10-03
I was wondering if theres an easy way to pick specific packages already installed on the computer along with other downloaded packages that may not be installed yet but would be practical to for the average user.  I want to make a CD full of .deb packages, and other decompiled installers that I can easily add on to with a program like K3b.

Before yelling at me, I am aware of the program AptOnCD.  I tried the program and just didn't like it.  There are nice features to it but it isn't good with adding to a CD, you pretty much just have to start over, and for some reason, it doesn't detect every package I have installed (including ones from the repositories).

So is there any other application or terminal code?

---

### Post by nowshining on 2008-10-04
for already installed programs or any uninstalled but kept, just backup the folder /var/cache/apt/

---

### Post by schmidtbag on 2008-10-04
oh wow cool, thanks

---

### Post by schmidtbag on 2008-10-04
Actually I'd like to know if theres a way to clear some of the uninstalled packages, or do they do that over time?

---

### Post by buixuanduong1983 on 2008-10-04
I also have small problem when I upgrade some package then the old one is still in cache, and if I backup cache for next fresh install then I have to manually delete the old package.
I found that /var/lib/dpkg/status lists all packages that we installed, that would be a place to look, I guess. Then somehow to compare it with the file in cache...

---

### Post by terry_gardener on 2008-10-04
to remove the deb packages for installed and uninstalled programs you can use. 

sudo apt-get autoclean 

there is also command "sudo apt-get autoremove" this removes any packages that where installed with another program that you have now uninstalled. for example not needed dependencies. 

if you use command "sudo apt-get --help" it will give a nice list of what command there is and what they do.

---

### Post by schmidtbag on 2008-10-04
i was actually looking for a function like that, thanks

---

### Post by buixuanduong1983 on 2008-10-04
Thanks Terry for pointing me out that command.

But when I tried autoremove and autoclean, it removed some packages but not all the old one: eg I installed lirc, then removed it, autoclean, autoremove, but lirc...deb package is still there in cache.
(Sorry, I don't try to find errors, but as I read in apt-get --help, it should work as Terry mentions. Correct me if I'm wrong).

---

### Post by schmidtbag on 2008-10-04
none of the packages in /var/cache/apt/archives/ are necessary.  You can delete all of them and it won't hurt you at all, its just if you want to reinstall something, the package has to be downloaded again.

if you want to delete all of them run "sudo nautilus /var/cache/apt/archives" and just select all .deb files and delete them.  I'm not really sure why your problem acts the way it does, if you wait long enough for ubuntu 8.10 then the problem may be fixed.

---

### Post by buixuanduong1983 on 2008-10-05
Thanks and have a good Ubuntu!

---

