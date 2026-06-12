---
title: "I installed Netbeans 8.1. How do I install JavaFX and Scene Builder?"
date: 2016-07-09
forum: Programming Talk
---

### Post by PopsTheSailor on 2016-07-09
I installed Netbeans via synaptic and it's version 8.1 but I noticed that I don't have JavaFX as an option for a new project. How do I install JavaFX and then I will want to install scene builder if it doesn't install with FX.

---

### Post by DaviesX on 2016-07-09
I recommend installing netbeans from the official site. 
[https://netbeans.org/downloads/](https://netbeans.org/downloads/)

---

### Post by PopsTheSailor on 2016-07-09
Are you saying that will fix my problem or just saying I should install from there? I have already installed NetBeans and openjfx (or something) to try and get FX / sceme builder to show up in the IDE. Should I uninstall these first?

---

### Post by DaviesX on 2016-07-10
I have never tried getting netbeans from apt repository, so I don't know what actually cause the issue. But I know for sure installing the package from the official site always works for me. I think you may want to try that :)

---

### Post by PopsTheSailor on 2016-07-10
OK so I went to the link above to install NetBeans and it said I needed JDK 8. I went to these directions but all they say is how to unpack the tar.gz file but not to install java. How do I actually install Java?

[http://docs.oracle.com/javase/8/docs/technotes/guides/install/linux_jdk.html#BJFJJEFG](http://docs.oracle.com/javase/8/docs/technotes/guides/install/linux_jdk.html#BJFJJEFG)

---

### Post by DaviesX on 2016-07-10
You can get openjdk from the apt repository. I think openjdk is a pretty good implementation these days. Or if you prefer oracle, then you can download the package from here: [http://www.oracle.com/technetwork/java/javase/downloads/index.html](http://www.oracle.com/technetwork/java/javase/downloads/index.html)

And if you open the link above, you can get the version of netbeans that is bundled with oracle jdk SE.

---

### Post by QIII on 2016-07-11
OpenJDK is the open source reference implementation of all things Java, including Oracle Java.  This is what Oracle has decreed.  Oracle dedicates a lot of resources to the development of OpenJDK.  "Open Source"?  Maybe.  But open source the way Oracle bends it.

That being the case, the choice between OpenJDK and Oracle Java is six of one or a half dozen of the other.  The big difference is that many developers, unaware of the relationship between OpenJDK and Oracle Java, will check specifically for Oracle Java as a dependency.  It won't matter that you have OpenJDK -- the reference implementation Oracle Java is based on -- their code will choke.

Personally, I just avoid any questions and install Oracle Java.

If you install Oracle Java following [these instructions]("http://www.webupd8.org/2012/09/install-oracle-java-8-in-ubuntu-via-ppa.html") and then download and install a Netbeans package from [here]("https://netbeans.org/downloads/"), you should be well on your way.

I'm not familiar with Scene Builder.

---

### Post by PopsTheSailor on 2016-07-11
Thanks all for the support and help. I have Oracle Java and Netbeans installed. My last challenge is getting scene builder installed but I'll work on that later so I'm marking this as solved. I basically installed Oracle Java from Oracle's site then installed Netbeans from them as well.

---

