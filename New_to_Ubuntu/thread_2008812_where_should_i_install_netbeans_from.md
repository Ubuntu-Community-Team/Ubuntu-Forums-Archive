---
title: "where should i install netbeans from?"
date: 2012-06-23
forum: New to Ubuntu
---

### Post by werty2010 on 2012-06-23
i beginning to learn java and thinking to start with netbeans
i noticed that its available through the software center and through the official site(in which case has the latest version). 
i tend towards the second but im not sure if ill have any problems...?

---

### Post by werty2010 on 2012-06-23
also is there a ppa having the latest version?

---

### Post by le_phoceen on 2012-06-23
Hi,

for most software, the best practice is to use apt-get or the Ubuntu Software Center, however, in the case of NetBeans, I prefer do a manual install by running the installer I download from the NetBeans web site.

To integrate it nicely with my Ubuntu installation, I add the NETBEANS_HOME variable in the ~/.bashrc file and I add the $NETBEANS_HOME/bin folder in the PATH variable, still in the ~/.bashrc file. As NetBeans is shipped with Maven 3, I also add the corresonding variables and folder in the path, as this :

```

export NETBEANS_HOME=~/lib/netbeans-7.1.2
export MAVEN_HOME=$NETBEANS_HOME/java/maven

export PATH=$NETBEANS_HOME/bin:$MAVEN_HOME/bin:$PATH
```However, note that you'll get the last NetBeans version, but you lose the opportunity to get the automatic update by Ubuntu Update Manager.

Welcome in the world of Java programming !

---

