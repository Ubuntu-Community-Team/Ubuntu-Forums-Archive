---
title: "installing a software."
date: 2006-05-04
forum: Repositories &amp; Backports
---

### Post by lindos on 2006-05-04
I downloaded the  "nmap"(software) package from the ubuntu site. Now this package is in my home directory, how do I go about installing it. I can't figure out how apt-get is used since I am new to Ubuntu. I think rpm(Red Hat) is easier to use.

---

### Post by oscar on 2006-05-04
apt-get is a lot easier to use than downloading packages like rpms manually.
To use it go Applications > Accessories > Terminal
Now enter:
```
sudo apt-get install nmap
```
The password will be your user's password
It should automatically download and install nmap for you.

---

### Post by neouser99 on 2006-05-04
[QUOTE=oscar]apt-get is a lot easier to use than downloading packages like rpms manually.
To use it go Applications > Accessories > Terminal
Now enter:
```
sudo apt-get install nmap
```
The password will be your user's password
It should automatically download and install nmap for you.[/QUOTE]

will work like a charm. you could also try the graphical Synaptic which is in the Administration menu if you are in Gnome. (correct me if im wrong, im on a winblows machine in a lab right now)

also, on debian systems dpkg = rpm, and IMHO dpkg (which apt uses) is much better.

---

### Post by aysiu on 2006-05-04
[QUOTE=lindos]I think rpm(Red Hat) is easier to use.[/QUOTE] [I beg to differ](http://monkeyblog.org/ubuntu/installing.html).

---

