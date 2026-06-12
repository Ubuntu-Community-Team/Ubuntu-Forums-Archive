---
title: "Loading Java on 12.04"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by Timmoore001 on 2014-01-06
I've got confused as to which version I need to download and how to install it.

I've downloaded:-

jre-7u45-linux-x64.rpm

Any thoughts very very welcome !

A very puzzled,

Tim

---

### Post by claracc on 2014-01-06
The easier way to install java in ubuntu and get the security updates is through the webup8 ppa.

Please, see this link: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

All the steps to add the repository and install the last oracle java package are provided in the link.

---

### Post by mörgæs on 2014-01-06
An .rpm package does not work on Buntu. 
If it has to be Oracle's java then the approach mentioned above is fine.

---

### Post by Timmoore001 on 2014-01-06
> **claracc said:**
> The easier way to install java in ubuntu and get the security updates is through the webup8 ppa.

Please, see this link: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

All the steps to add the repository and install the last oracle java package are provided in the link.



Many many thanks to both members !  I've been driving myself crackers for a couple of days and getting nowhere on my own !

A tribute to this forum !

:  )))

Tim

---

### Post by claracc on 2014-01-06
You are very welcome. 

If the problem has been solved, please mark the thread as solved with "thread tools" in order to find the information easily.

Thanks

---

### Post by Timmoore001 on 2014-01-06
tim@tim-A880G:~$ sudo add-apt-repository ppa:webupd88team/java
[sudo] password for tim: 
Cannot add PPA: 'ppa:webupd88team/java'.
Please check that the PPA name or format is correct.
 tim@tim-A880G:~$ 

doesn't work....  ???

trying some else in the article

Tim

---

### Post by Timmoore001 on 2014-01-06
typo ... had too many '8'  *LOL*  Whoops.....

---

### Post by Timmoore001 on 2014-01-06
It worked a treat and now my 'A Drive' 50GB Cloud storage and upload directories !  (Its also free ! )

Many many thanks !

---

### Post by mörgæs on 2014-01-06
You're welcome. Now it's your turn to help people :-)

---

