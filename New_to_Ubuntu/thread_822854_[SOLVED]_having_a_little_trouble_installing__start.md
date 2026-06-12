---
title: "[SOLVED] having a little trouble installing  startupmanager"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Kronie on 2008-06-08
i want to install the startupmanager so i can change the splash screen, but when i do 
```
sudo apt-get install startupmanager
```
but it outputs with the error
```
The following packages have unmet dependencies:
  startupmanager: Depends: yelp but it is not going to be installed
E: Broken packages

```
then i try
```
sudo apt-get yelp
```
and it comes up with
```
The following packages have unmet dependencies:
  yelp: Depends: xulrunner-1.9 but it is not going to be installed
E: Broken packages

```
then i try 
```
sudo apt-get install xulrunner-1.9
```
and...
```
xulrunner-1.9 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
0_o so, if i have xulrunner 1.9 why wont yelp install?!

---

### Post by drs305 on 2008-06-08
Try going into synaptic > Edit > Fix Broken Packages, then try it again.

---

### Post by Kronie on 2008-06-08
:( didnt help

---

### Post by oldos2er on 2008-06-08
Go to System, Administration, Software Sources, and make sure all repositories are enabled.

---

### Post by Kronie on 2008-06-09
ok, its fixed now after 8.04.19 update :D

---

