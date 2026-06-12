---
title: "Git repo for tomcat8-user?"
date: 2017-09-18
forum: Programming Talk
---

### Post by 1clue on 2017-09-18
Hi,

I'm trying to figure out the upstream source (or even Ubuntu source) for the tomcat8-user package on github or some other git repo. I'd like to make some minor changes for my personal use and would like my changes to track future changes to this package.

I've looked at the changelog and copyright notice bundled in the package, but I can't see attribution for upstream and I have no idea how to get the source.  Google has a bunch of tomcat8-user repos but none of them look right.

I just want a read-only clone that can track, either Ubuntu's copy or upstream wherever that is.

Thanks.

---

### Post by &amp;KyT$0P# on 2017-09-18
Does [this link]("http://tomcat.apache.org/svn.html") have what you're looking for?

---

### Post by 1clue on 2017-09-18
If it does I haven't found it.

I'm looking for scripts which, when you have a tomcat8 already installed in Ubuntu via the PPA, it creates a new instance for CATALINA_BASE using the ppa tomcat8 as CATALINA_HOME.

***Edit for clarity:***
The files on tomcat.apache.org place all  files in a single parent directory. The Ubuntu PPA separates the build to put files where they should go with respect to the standard Linux Filesystem Heirarchy [http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html](http://www.tldp.org/LDP/Linux-Filesystem-Hierarchy/html/index.html) .

The tomcat8-user package I want (as opposed to tomcat8 which contains the actual app server) contains scripts to install a minimal instance of tomcat which can then be upgraded via the PPA and get security updates as they become available. Only a few files are necessary in CATALINA_BASE, because most of the files are common to all tomcats of a version.

The tomcat8-user package knows about the linux directory structure and lets us create new instances using ports specified on the command line, making a very easy setup.

---

### Post by norobro on 2017-09-21
Little late, but could this be what you are looking for? [https://anonscm.debian.org/git/pkg-java/tomcat8.git/tree/debian](https://anonscm.debian.org/git/pkg-java/tomcat8.git/tree/debian)

---

### Post by 1clue on 2017-09-21
That's more promising than what I've found so far.  Thanks.

---

