---
title: "The package system is broken"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by History Teacher on 2014-04-24
I'm running Lubuntu on a Lenovo G470 laptop.  Trying to install software updates with the software updater and I get this message:

[I]The package system is broken
Check if you are using third party repositories. If so disable them, since they are a common source of problems.  Furthermore run the following command in a Terminal: Apt-get install -f[/I]

I've tried to run the above command but failed (I may not be in 'root').  Also how can I find out if I am using third party repositories and how I might be able to disable them?

This is a new phenomena.  In the past I was able to make updates without a problem.

Thanks for all your help!

---

### Post by Ubi_one_2014 on 2014-04-24
pls post the output of, as root, :
apt-get dist-upgrade

---

### Post by ibjsb4 on 2014-04-24
That would be

```
sudo apt-get install -f
```

---

### Post by slickymaster on 2014-04-24
Can you please post between code tags the output you get from running in a terminal window the following command```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by History Teacher on 2014-04-24
Worked perfectly!  Thank you so very much!

---

