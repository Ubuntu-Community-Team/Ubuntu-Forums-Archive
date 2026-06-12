---
title: "E: Package 'sun-java6-jdk' has no installation candidate"
date: 2012-10-31
forum: Packaging and Compiling Programs
---

### Post by unibroker on 2012-10-31
I know this question has been asked a multitude of times and I've read and tried the various suggestions and the frustration continues.  When I tried Open JDK that worked but I am new at this and the tutorial I'm following is specific about using the Sun JDK.  I have added the ppa because I know Ubuntu had some licensing issues but I still get this. ```
sudo apt-get install git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk2.6-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev sun-java6-jdk pngcrush schedtool 
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate
```

Any suggestions?

---

### Post by drmrgd on 2012-10-31
Which PPA did you add?  Was it this one referred by the Community Documentation?

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

### Post by 00negative on 2012-10-31
> **unibroker said:**
> I know this question has been asked a multitude of times and I've read and tried the various suggestions and the frustration continues.  When I tried Open JDK that worked but I am new at this and the tutorial I'm following is specific about using the Sun JDK.  I have added the ppa because I know Ubuntu had some licensing issues but I still get this. ```
sudo apt-get install git-core gnupg flex bison gperf libsdl1.2-dev libesd0-dev libwxgtk2.6-dev squashfs-tools build-essential zip curl libncurses5-dev zlib1g-dev sun-java6-jdk pngcrush schedtool 
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'sun-java6-jdk' has no installation candidate
```

Any suggestions?

Not sure what your using java for but if you google "compile android in Linux" you will find a number of tutorials on setting up java, either by adding a repo or by manually installing the latest from the oracle java website. Xda developers is a great resource for these even if your not using it for android compiling.

---

### Post by unibroker on 2012-10-31
> **drmrgd said:**
> Which PPA did you add?  Was it this one referred by the Community Documentation?

[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

No.  It was this one ```
ppa:ferramroberto/java
``` suggested by someone at the subject tutorial having the same problem.

---

### Post by unibroker on 2012-10-31
> **00negative said:**
> Not sure what your using java for but if you google "compile android in Linux" you will find a number of tutorials on setting up java, either by adding a repo or by manually installing the latest from the oracle java website. Xda developers is a great resource for these even if your not using it for android compiling.
XDA has the tutorial I'm following and as I say setting up the JDK has been super challenging for me.

---

### Post by drmrgd on 2012-10-31
Try that webup8 one then.  It's the one I usually use, and it works quite well.

---

### Post by unibroker on 2012-10-31
> **drmrgd said:**
> Try that webup8 one then.  It's the one I usually use, and it works quite well.
Other than going into the tutorial code and changing to JDK7 everywhere JDK6 is mentioned, no compatibility issues?  Thanks for the response.  I hadn't see that link.

---

### Post by 00negative on 2012-10-31
> **unibroker said:**
> Other than going into the tutorial code and changing to JDK7 everywhere JDK6 is mentioned, no compatibility issues?  Thanks for the response.  I hadn't see that link.

Sounds like you have it working but you could try paranoid androids site for their setup to compile their rom as well. It has a pretty straight forward guide to setting it up manually. Just for future reference. 

If their is a step in particular that is tripping you up feel free to ask.

---

### Post by drmrgd on 2012-10-31
No problem.  I think that changing the install to v6 should work.  I think I actually had to do that a short time ago due to some compatibility issues, although I can't remember if I installed Oracle or Open JDKv6.

---

### Post by unibroker on 2012-10-31
> **00negative said:**
> Sounds like you have it working but you could try paranoid androids site for their setup to compile their rom as well. It has a pretty straight forward guide to setting it up manually. Just for future reference. 

If their is a step in particular that is tripping you up feel free to ask.
I like PA's tutorial (I think by Mateorod).  I actually attempted using both methods and both failed.  I've been following fattire for the last year and will stick with his CM10 tutorial.  But seeing as I can't get through setting up the build environment without falling all over myself..................

---

### Post by 00negative on 2012-10-31
> **unibroker said:**
> I like PA's tutorial (I think by Mateorod).  I actually attempted using both methods and both failed.  I've been following fattire for the last year and will stick with his CM10 tutorial.  But seeing as I can't get through setting up the build environment without falling all over myself..................

Yeah it took me a couple tries to get it working properly but using a compilation of various tutorials finally got it set up and can compile aosp and cm10 successfully on xubuntu 12.10, hopefully you have it worked out now as well.

---

### Post by unibroker on 2012-10-31
Thanks respondents!  I'm repo syncing so the suggestions helped.

---

