---
title: "What will happen if I run 'sudo apt-get autoremove'?"
date: 2014-11-24
forum: New to Ubuntu
---

### Post by flaymond on 2014-11-24
What happen if I run this command


 ```
sudo apt-get autoremove
```


When I hit ***ENTER***, it say 73 packages to remove..what it will remove? All of my softwares? 
 Thanks.


* ***_Do NOT RUN  _***this code because it probably will get your current softwares deleted. I'm here just wanna ask if im right about this.

---

### Post by OrangeCrate on 2014-11-24
> apt-get autoremove

This command removes packages that were installed by other packages and are no longer needed.

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

### Post by Impavidus on 2014-11-24
It will remove all packages that have been installed automatically as a dependency of something else that you installed, but are no longer needed, usually because you already removed the package that depended upon it, or (less likely, but this is the case for kernel upgrades) because you upgraded the packages that depended on it and the new version no longer depends on this package. So, if you installed and removed a lot of software, there may be a lot to autoremove: data packages belonging to specific uninstalled programs, libraries, old kernels. The command is usually safe. It should list the packages it's going to uninstall before you have to approve.

---

### Post by Al1000 on 2014-11-24
```
sudo apt-get -s autoremove
``` ...runs a simulation, so tells you what the command without the -s option will remove, without removing anything.

---

### Post by ian-weisser on 2014-11-24
...and, in the worst case, that autoremove does happen to remove something you miss (because you didn't explicity install it; it was dragged in by something else you since removed), simply install that package again.

---

### Post by flaymond on 2014-11-24
Thanks for help guys! I'm done with this curiosity! :D

---

### Post by mörgæs on 2014-11-24
Please mark the thread 'solved'.

---

