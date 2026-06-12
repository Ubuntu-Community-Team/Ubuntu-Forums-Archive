---
title: "remove broken vmware?"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-04-27
i installed vmware a couple of hours ago and obviously did something wrong because it doesn't work:lolflag: there are icons for it in the menu but it wont launch so i just want to completely remove it can anyone tell me how?

---

### Post by Cypher on 2008-04-27
If you installed it using APT, then you can do
```

sudo apt-get remove <package>

```
Where <package> is the name you used to install..

---

### Post by SuperSon!c on 2008-04-27
also, if you haven't tried it yet, try [virtualbox]("http://www.virtualbox.org/").

---

### Post by bodhi.zazen on 2008-04-27
How did you install VMWare and what problems are you having ?

---

### Post by kamitsukai on 2008-04-27
i dl the tar.gzp archive from the vmware website (it was vmware workstation 6.0) and then i think i installed with this [http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/](http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/)

---

### Post by bodhi.zazen on 2008-04-27
[FONT=Verdana]> **kamitsukai said:**
> i dl the tar.gzp archive from the vmware website (it was vmware workstation 6.0) and then i think i installed with this [http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/](http://ubuntu-tutorials.com/2007/11/17/install-vmware-server-on-ubuntu-710-gutsy-gibbon-updated/)


There is an uninstallation script, vmware-uninstall.pl

use these commands to find it : 
[/FONT]
```
sudo updatedb
sudo locate vmware-uninstall
```

It may be in the extracted directory , in /usr/bin/ or elsewhere.

```
sudo sh /path_to/[FONT=Verdana]vmware-uninstall.pl
```

After removing it, you can search your system for orphaned files with :

```
sudo locate vmware
```

delete those files as well.
[/FONT]

---

