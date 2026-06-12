---
title: "Broken packages error"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by NuclearTide on 2012-03-27
I'm trying to install the libboost-regex-dev package, but I'm getting this error ([http://pastebin.com/mzv2EP1N](http://pastebin.com/mzv2EP1N)). I tried [this topic]("http://ubuntuforums.org/showpost.php?p=5962046&postcount=9")'s solution, but it's still not working. What should I do?

---

### Post by kc1di on 2012-03-27
> **NuclearTide said:**
> I'm trying to install the libboost-regex-dev package, but I'm getting this error ([http://pastebin.com/mzv2EP1N](http://pastebin.com/mzv2EP1N)). I tried [this topic]("http://ubuntuforums.org/showpost.php?p=5962046&postcount=9")'s solution, but it's still not working. What should I do?

Sounds like your trying to install a package that is either old or newer than what is currently in the repository.  

you can try the following if you want to proceed but it will most likely be broken because the package your trying to install has un met dependency issues (that is other packages it needs to function properly.) In a terminal do the following:

```
sudo apt-get install -f <package name> 
```
if that does not work try this again in a terminal:

```
sudo dpkg --configure -a 
```

What program are you trying to use this package with? that may shed some light on why the dependencies are wrong or un -available.

---

### Post by Pand5461 on 2012-03-27
Hi!

Have you changed your update server recently? Such a mess with dependencies can happen if you use one server and then jump to another which has only older version of packages.

So, I suggest you to change the server to the main server, apt-get update, apt-get upgrade and then try to install the package once again.

---

### Post by jerrrys on 2012-03-27
Two good suggestions above.

libboost-regex-dev depends on 1.46 packages. are they getting installed?

[ATTACH]215008[/ATTACH]

and your pastebin link is broke

---

