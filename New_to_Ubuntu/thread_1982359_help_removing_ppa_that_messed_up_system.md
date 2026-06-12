---
title: "help removing ppa that messed up system"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by rburkartjo on 2012-05-18
i will list the link for the ppa below

note after i installed got this error

E: Type 'hpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

cant get into spm to navigate to reps
cant open ubuntu software center to nav to ppa
how can i completely remove from command line or other way tks

link NOTE DONT TRY TO INSTALL
[http://www.noobslab.com/2012/05/install-wine-154-in-ubuntulinux-mint.html](http://www.noobslab.com/2012/05/install-wine-154-in-ubuntulinux-mint.html)

---

### Post by idoitprone on 2012-05-18
> **rburkartjo said:**
> i will list the link for the ppa below

note after i installed got this error

E: Type 'hpad.net/ubuntu-wine/ppa/ubuntu' is not known on line 2 in source list /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

cant get into spm to navigate to reps
cant open ubuntu software center to nav to ppa
how can i completely remove from command line or other way tks

link NOTE DONT TRY TO INSTALL
[http://www.noobslab.com/2012/05/install-wine-154-in-ubuntulinux-mint.html](http://www.noobslab.com/2012/05/install-wine-154-in-ubuntulinux-mint.html)

```
cat /etc/apt/sources.list.d/ubuntu-wine-ppa-precise.list 
```

??

---

### Post by drs305 on 2012-05-18
You can remove the repository via the Edit >Settings option of the menu in Ubuntu Software Center you can open a file browser as root and delete the repository file from it's folder. In Update Manager, click Settings lower left, or you can (as asked):
```
gksu nautilus /etc/apt/sources.list.d/
```
Remove ubuntu-wine-ppa-precise.list then:
```
sudo apt-get update
```

---

### Post by rburkartjo on 2012-05-18
drs tks that did the trick. new that there was another way but has been a long time since i had to use that command and forgot, spm and software center working fine, really appreciate the fast answer

---

