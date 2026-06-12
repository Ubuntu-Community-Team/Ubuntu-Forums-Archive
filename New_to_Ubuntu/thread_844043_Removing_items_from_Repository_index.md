---
title: "Removing items from Repository index"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by avanrens on 2008-06-29
Hi,
I get this message when using update manager "Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
How do I remove it from the repository index

---

### Post by prshah on 2008-06-29
> **avanrens said:**
> 
"Failed to fetch [http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.gz](http://www.getautomatix.com/apt/dists/feisty/main/binary-amd64/Packages.gz)  404 Not Found
How do I remove it from the repository index

```
sudo gedit /etc/apt/sources.list
```, then find the relevant repository, and comment it out by placing a "#" in front of it.

Don't forget to```
sudo apt-get update
``` for your changes to take effect.

---

### Post by wormser on 2008-06-29
That error is for Automatix which is not [supported and not recommended]("https://help.ubuntu.com/community/Automatix").  You should remove it or comment it out like the directions above.

---

### Post by avanrens on 2008-06-29
Thank you  It's all fixed now.
:guitar:

---

### Post by munkyboy on 2008-06-30
Okay so i have a similar problem now.

I added a different but incorrect source but when i put in that code i get;

russ@russ-desktop:~$ sudo gedit /etc/apt/sources.list
[sudo] password for russ:
sudo: gedit: command not found
russ@russ-desktop:~$

I know im being dumb But what am I doing wrong?
im using kubuntu 8.04

nvm fixed now i didnt realise gedit was a gnome command. I replaced it with kate and it worked. you live and learn

---

