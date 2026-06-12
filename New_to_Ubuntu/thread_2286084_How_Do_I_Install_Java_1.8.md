---
title: "How Do I Install Java 1.8?"
date: 2015-07-09
forum: New to Ubuntu
---

### Post by richramik on 2015-07-09
Relatively speaking, I'm still new to Ubuntu.  Now, I'm learning how to work with a package named JMRI.  It is used for, among other things programming model train locomotives equipped with Digital Command Control decoders.  In order to get the JMRI package to function, I need to load the 1.8 package of Java.  And this is where the wheels sort of come off the track.  I checked several online sources.  But the more I read, the more confused I got.  Using JMRI will speed up the programming process, i.e., JMRI provides screens that allow the direct control of the Configuration Variables for each locomotive.  I've used the hand held controller to do this and the programming/setting the variables is tedious at best.  

Back to the issue.  Any assistance would be greatly appreciated.

Thanks,
Rich Ramik

---

### Post by QIII on 2015-07-09
Hello!

The easiest way is to use the method found at [webupd8.org]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html"):

```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
```

This will keep you up to date as Oracle releases updates.

Cheers!

---

### Post by Vladlenin5000 on 2015-07-09
[http://jmri.sourceforge.net/install/Linux.html](http://jmri.sourceforge.net/install/Linux.html)

Clearly they recommend Java from Oracle which is quite easy to install: [http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html](http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html)

---

### Post by richramik on 2015-07-11
Thanks guys.  Worked like a charm.  I appreciate the assistance.

Rich Ramik

---

### Post by QIII on 2015-07-11
No problem.  That's what we're here for.

To help the next person find this solution, would you please mark the thread as "Solved" by using the "Thread Tools" drop down at the top?

Thanks.

---

