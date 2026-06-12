---
title: "Advice on how to enable the proposed repositories to get access to report any bugs."
date: 2011-09-14
forum: New to Ubuntu
---

### Post by mikodo on 2011-09-14
I have been asked to test a proprosed bug fix for duplicity, by the maintainer of Deja-dup, that I have had a problem with. I have never done any bug testing or reporting. Taken from here:  [https://wiki.ubuntu.com/Testing/EnableProposed](https://wiki.ubuntu.com/Testing/EnableProposed) I don't know how to do the following:

**Selected upgrading from -proposed**

After  enabling the -proposed archive as shown above, you can configure apt to  allow selective installs of packages from it instead of upgrading all  of your packages to the -proposed versions. 
Create the file /etc/apt/preferences with this content: 
Package: * Pin: release a=*-security Pin-Priority: 990  Package: * Pin: release a=*-updates Pin-Priority: 900  Package: * Pin: release a=*-proposed Pin-Priority: 400With  this preference file in place, Update Manager, Synaptic and Aptitude  won't ask for upgrades from the -proposed repositories. 
If you want to see the natty-proposed packages under the 'Upgradable Packages' listing, run Aptitude as follows 

sudo aptitude -t natty-proposedIn  aptitude, you should first update the package listings ('u' key), mark  any of the packages you want to upgrade ('+' key), and finally install  them ('g' key). After this, if you run Aptitude without options again,  the rest of natty-proposed upgradable packages will remain hidden. 
Alternatively, you can install a package from -proposed by using 

sudo aptitude install packagename/natty-proposedThis method uses a higher priority to install packages. 
If you use another release of Ubuntu, replace natty by your release name everywhere. 


In Software Sources, I have enabled Pre-released updates (lucid-proposed) and Unsupported Updates (lucid-backports) in preparation for this. I am assuming I need to run: nano somehow to edit the file in /etc/apt/preferences with the following content above, but I need some hand holding, please.

Thanks.

Edit: Here is the link to the duplicity package:

[http://lists.gnu.org/archive/html/duplicity-talk/2011-09/msg00016.html](http://lists.gnu.org/archive/html/duplicity-talk/2011-09/msg00016.html)

---

### Post by mikodo on 2011-09-14
Never mind.

I used 
```
sudo aptitude install duplicity/lucid-proposed
```That seemed to do the trick. I then disabled in Software Sources the Pre-released updates (lucid-proposed). I didn't want all the other apps updating to proposed.

Thanks.

---

