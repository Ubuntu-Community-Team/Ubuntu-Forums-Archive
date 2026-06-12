---
title: "frostwire isnt working"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by patchido on 2008-08-28
i cant make it work.... if i run in terminal this is output
```

pato@pato-laptop:~$ frostwire
HOSTNAME IS pato-laptop
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: cannot access /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
pato@pato-laptop:~$ 
```


i went into java.com downloaded and installed it, and output is the same

---

### Post by nicedude on 2008-08-28
Did you install frostwire from source you downloaded or a deb package? I installed mine from a deb and I also installed sun-java6-jre and mine works fine.

here is a command to install java
sudo apt-get install sun-java6-jre

Hope this helps

---

### Post by tuxulin on 2008-08-28
after trying nicedude method if its still moaning then do
sudo update-alternatives --config java 
and follow the instructions on changing to sun java.

Tuxulin

---

### Post by Therion on 2008-08-28
Did you install Frostwire from the Repo or did you go to their website and then download and install the latest version?  I believe (Warning: Going by memory here) that the version in the repo has some Java issue.  I'd try going to the Frostwire website and getting the latest version (there's a .deb file you can download).  

Make sure you have a good, clean, Java install as well.


Edit:  [FrostWire v4.17 .deb](http://www.frostwire.com/?id=thanks&dwnlink=http://main3.frostwire.com/frostwire/4.17.0/frostwire-4.17.0.i586.deb&from=) -- Need to update myself it seems!

---

