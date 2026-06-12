---
title: "Trying to remove a broken Wine install"
date: 2012-06-30
forum: New to Ubuntu
---

### Post by irishshanna on 2012-06-30
I'm not sure if this is a Wine issue or an Ubuntu issue, so i'll throw it out there and hope for the best. When I try to remove it, it says I don't have it...but I do, its still there. But it won't let me install another version.

I installed the beta 1.5 version of Wine, its making my apps crash. I'm trying to get rid of it and go back to 1.3 or 1.4. This is what happens:

shanna@*************:~$ sudo apt-get remove wine
[sudo] password for shanna: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package wine is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shanna@shanna-NP192AA-ABA-p6140f:~$ rm -f $HOME/.config/menus/applications-merged/wine*

shanna@**************:~$ sudo apt-get install wine1.4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 wine1.4 : Depends: wine1.4-i386 (= 1.4.1-0ubuntu1~precise1~ppa3)
E: Unable to correct problems, you have held broken packages.
shanna@shanna-NP192AA-ABA-p6140f:~$ rm -f $HOME/.config/menus/applications-merged/wine*

---

### Post by daslinkard on 2012-07-27
What about trying
```
sudo apt-get purge wine
```

This will remove all files, settings, and configuration files for you.

---

