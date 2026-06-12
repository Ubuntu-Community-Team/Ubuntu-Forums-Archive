---
title: "Netbeans: could not mark all packages for installation or upgrade"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by pstiady on 2008-11-24
Dear Experts,

I'm living in Indonesia and using Ubuntu 8.04 - the Hardy Heron.  I'm trying to install netbeans using Synaptic from mirror repository in Indonesia, but I get the following error:

Could not mark all packages for installation or upgrade

netbeans:
 Depends: libnb-apisupport1-java but it is not going to be installed
 Depends: libnb-ide8-java but it is not going to be installed
 Depends: libnb-java1-java but it is not going to be installed

Could someone suggest how to deal with this error?  Will changing software source help?  I'm using dial-up connection, so that I cannot try too many sites.  If I download netbeans from [http://www.netbeans.org/downloads/index.html](http://www.netbeans.org/downloads/index.html), how can I install the package to my Ubuntu?  

Thank you for your help.
Patrick

---

### Post by azafaraht on 2008-11-24
Hey there.  I just installed it a few hours ago, though I can't really explain why you are not able to, this is what I did and so far it works:

Install JDK 6:
> sudo apt-get install sun-java6-jdk

Download and install netbeans:
Which version are you trying to install?  I installed 6.5 on this machine.

Hope this helps.

---

### Post by pstiady on 2008-11-25
I just enabled everything, except the source code on the first tab of Software Sources and select server from Indonesia and it works.  Thank you.

---

