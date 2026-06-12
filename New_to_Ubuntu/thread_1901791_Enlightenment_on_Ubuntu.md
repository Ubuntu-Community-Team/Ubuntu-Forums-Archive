---
title: "Enlightenment on Ubuntu?"
date: 2011-12-29
forum: New to Ubuntu
---

### Post by doppel.ganger on 2011-12-29
Is there any way I can run the Enlightenment desktop on my Ubuntu 11.10 setup?

---

### Post by Elfy on 2011-12-29
Apparently - not done it myself though.

[https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn](https://launchpad.net/~hannes-janetzek/+archive/enlightenment-svn)
[http://www.enlightenment.org/p.php?p=download&l=en](http://www.enlightenment.org/p.php?p=download&l=en)

---

### Post by JOHNNYG713 on 2011-12-29
Yes, open synaptic and search e17 ! after install, log out and in the drop down box choose enlightenment and log back in ! :D

---

### Post by tomski on 2011-12-29
i tried it via synaptic & got hundreds of module load errors so i then used easy_E17 which syncs to cvs, compiles & installs all of it under /opt/e17

this way gave me the best results but took a while to to compile

[http://omicron.homeip.net/svn/easy_e17/easy_e17.sh](http://omicron.homeip.net/svn/easy_e17/easy_e17.sh)

---

### Post by doppel.ganger on 2011-12-29
Just did:
```
sudo apt-get install e17
```
Worked for me.

---

### Post by Frogs Hair on 2011-12-29
Currently typing this on E17 . I chose to use the PPA below because the core packages in the software center have some limitations and the PPA is updated regularly .

```
sudo add-apt-repository ppa:hannes-janetzek/enlightenment-svn
```
```
sudo apt-get update
```  
```
sudo apt-get install e17
```
After installation logout or restart and choose Enlightenment from the session list at login .

---

### Post by doppel.ganger on 2011-12-29
By the way, are there any distros that still come with Enlightenment as their default desktop? I know MoonOS used to, but now uses gnome.

---

### Post by Frogs Hair on 2011-12-29
This is Ubuntu based and I believe there are others . [http://bodhilinux.com/](http://bodhilinux.com/)

---

### Post by Elfy on 2011-12-29
> **doppel.ganger said:**
> By the way, are there any distros that still come with Enlightenment as their default desktop? I know MoonOS used to, but now uses gnome.

There is a list of some at the bottom of the download page I gave earlier

---

### Post by doppel.ganger on 2011-12-30
Thanks!

---

