---
title: "Ant 1.7"
date: 2007-06-26
forum: Programming Talk
---

### Post by KeighleHawk on 2007-06-26
Anyone using ant 1.7?  If so, is there an ubuntu  package somewhere or did you have to install from the Apache.org zip file?

---

### Post by Lazarenko on 2007-07-28
I'm trying to find Ant 1.7 for my Fiesty. Looks like the only way is to install from sources :(

---

### Post by Lazarenko on 2007-07-28
> **Lazarenko said:**
> I'm trying to find Ant 1.7 for my Fiesty. Looks like the only way is to install from sources :(

Hey, I did it. Just download Ant 1.7 binary distribution from any of official Apache mirrors, unpack and then copy all JARs from lib directory to your Ant library directory. In my Fiesty it is "/usr/share/ant/lib". 

$ ant -version
Apache Ant version 1.7.0 compiled on December 13 2006

---

### Post by octoberdan on 2007-09-25
[http://packages.ubuntu.com/gutsy/devel/ant](http://packages.ubuntu.com/gutsy/devel/ant)
[http://packages.ubuntu.com/gutsy/devel/ant-optional](http://packages.ubuntu.com/gutsy/devel/ant-optional)

download both of those packages and install with "sudo dpkg -i ..."

$ ant -version
Apache Ant version 1.7.0 compiled on August 29 2007

---

### Post by 2008 on 2008-03-25
Hi there,

i am running Dapper Drake 6.06, sun-java5-sdk and Apache Ant version 1.6.5 compiled on October 26 2005.

Is there any smooth way to update my ant version to the latest?

Thanks!

---

### Post by envis on 2009-07-01
> **Lazarenko said:**
> Hey, I did it. Just download Ant 1.7 binary distribution from any of official Apache mirrors, unpack and then copy all JARs from lib directory to your Ant library directory. In my Fiesty it is "/usr/share/ant/lib". 

$ ant -version
Apache Ant version 1.7.0 compiled on December 13 2006


Success thanks man that was easy, now red5 is installing on my ubuntu 6 (note out of confusion before i try your trick i succesfully upgraded to ubuntu 7 following this guide:
[http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html](http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html)
(Method 2 &#8211; Using apt-get)
)


edit: oh yea, get ant 1.7 here: [http://ant.apache.org/bindownload.cgi](http://ant.apache.org/bindownload.cgi)

---

