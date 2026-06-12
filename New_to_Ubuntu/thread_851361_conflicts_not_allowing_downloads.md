---
title: "conflicts not allowing downloads"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by rixtr66 on 2008-07-06
iwas trying to build blender from svn but when it came time to install
python2.5dev i got a conflict error and it said to use the package mgr.
but i get the same conflict thing,i also get this trying to down load alien arena and other games.i didnt have this problem with 7.10 so it must be 8.04
can any one suggest a workaround or do i have to wait for the right upgrade?
icant be more specific with the error because the message is vauge itself.
any help would be appreciated.
rick:confused:

---

### Post by kbuel on 2008-07-06
So when you do this: 

```
sudo apt-get install python2.5-dev
```

What is the error?

---

### Post by rixtr66 on 2008-07-06
The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is to be installed
E: Broken packages:(

---

### Post by rixtr66 on 2008-07-07
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  python2.5-dev: Depends: python2.5 (= 2.5.2-2ubuntu4) but 2.5.2-2ubuntu5 is to be installed
E: Broken packages
rick@rick-laptop:~$ 
:mad:

---

### Post by hyper_ch on 2008-07-07
do you have universe and multiverse repos enabled?

---

### Post by rixtr66 on 2008-07-07
how do you do that?

---

### Post by rixtr66 on 2008-07-07
oh yes they are checked,i also updated the repository and i get the same
message.this happens with alot  of stuff i try to download.
rick

---

### Post by kbuel on 2008-07-07
I'm grasping at straws here... but this has fixed a few things for me in the past:

```
sudo apt-get dist-upgrade
```

does anything happen when you do this...

---

### Post by rixtr66 on 2008-07-08
rick@rick-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rick@rick-laptop:~$

---

