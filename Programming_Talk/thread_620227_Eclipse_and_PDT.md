---
title: "Eclipse and PDT"
date: 2007-11-22
forum: Programming Talk
---

### Post by raxz on 2007-11-22
Hi all, 

I want to install PDT on my Eclipse 3.2 and I am running on Gutsy.

I tried following [http://www.thierryb.net/pdtwiki/index.php?title=Using_PDT_:_Installation_:_Installing_PDT](http://www.thierryb.net/pdtwiki/index.php?title=Using_PDT_:_Installation_:_Installing_PDT)

I used the "automated" approach but I get this error:

"PDT Feature (1.0.1.v20071001-79-78E7QYGHEPGGP) requires feature "org.eclipse.wst (2.0.0)", or compatible"

I checking my Eclipse Project SDK I found this configuration:


Included feature "Eclipse Platform" version "3.2.2.r322_v20070119-CXMbUe9K_WF26uA" contains problems.

Included feature "Eclipse Platform Plug-in Developer Resources" version "3.2.2.r322_v20070119-CXMbUe9K_WF26uA" contains problems.

Included feature "Eclipse Java Development Tools" version "3.2.2.r322_v20070104-R4CR0Znkvtfjv9-" contains problems.

Included feature "Eclipse JDT Plug-in Developer Resources" version "3.2.2.r322_v20070104-R4CR0Znkvtfjv9-" contains problems.

Included feature "Eclipse Plug-in Development Environment" version "3.2.1.r321_v20060823-6vYLLdQ3Nk8DrFG" contains problems.


Is there a particular SDK that Eclipse does not like?

help?

--edit--

after some searching in the forums I found a similar problem: [http://ubuntuforums.org/showthread.p...ht=eclipse+PDT](http://ubuntuforums.org/showthread.p...ht=eclipse+PDT)

unfortunately the issue was not resolved....any help?

---

### Post by TSP on 2007-11-23
I have the same issue in my opensuse notebook...we need to wait for a proper fix from the guys doing this project i think.

---

### Post by raxz on 2007-11-23
Any alternatives that we can do for now?

Why isn't the latest release of eclipse(3.3) in the repository?  It still shows 3.2?

---

### Post by jespdj on 2007-11-26
Make sure you are using Sun Java 5 or 6 instead of GNU or Sun Java 1.4.
```
sudo apt-get install sun-java6-jdk sun-java6-plugin
sudo update-alternatives --config java
```

---

