---
title: "[SOLVED] How to remove the GUI ?"
date: 2008-10-04
forum: New to Ubuntu
---

### Post by TeknoPhil on 2008-10-04
Hi,
on a ubuntu 8.04 server test box, I installed the GUI 
```
apt-get install ubuntu-desktop
```

It took forever to install all the necessary packages.

Now, I would like to remove everything that was installed from this command. 

The command apt-get remove ubuntu-desktop is removing only one small package (same thing with autoremove).

Thanks for your help.

---

### Post by porchrat on 2008-10-04
I think the command you're looking for is:

```
sudo apt-get autoremove
```

This will remove all dependencies that are no longer required on the system.  *i.e* the packages that depend on these dependencies in order to function have already been removed, therefore these dependencies can be removed too.

You should use one of these to get a list of uses for apt-get.  What you're trying to do is remove all the dependencies no longer required now that ubuntu-desktop is gone.

```
man apt-get
``` for the manual

```
apt-get --help
``` for a list of possible options that can be used with apt-get

hope this helps

---

### Post by bhadotia on 2008-10-04
Do :
```
sudo apt-cache show ubuntu-desktop
```

and that will show you all the dependent, recommened and suggested packages. Then just :
```
sudo apt-get purge <packages in above lists> -s && apt-get autoremove --purge -s
```
That should eliminate everything you don't need and somethings you need:D. Don't forget the '-s' option as that will tell you what you are about to remove and thus you can prepare before hand.

---

### Post by iponeverything on 2008-10-04
Why don't you try:

apt-get install ubuntu-server

---

### Post by TeknoPhil on 2008-10-04
Hi,
the command
```
sudo apt-get autoremove ubuntu-desktop
```
will only remove 1 package (ubuntu-desktop).

and the command
```
sudo apt-get autoremove
```
don't remove anything.


Thanks for your help

---

### Post by Martje_001 on 2008-10-04
Look in the logs of apt to see wich packages were installed and then remove them..

---

