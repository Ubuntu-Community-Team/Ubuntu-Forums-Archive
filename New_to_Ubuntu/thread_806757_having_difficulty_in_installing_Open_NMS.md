---
title: "having difficulty in installing Open NMS"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by liaogz on 2008-05-25
Hi all,

I do faced some difficulty in installing the OpenNMS. Please tell me what does these codes is trying to tell me...

> root@laptop:/home/moses# sudo apt-get install apache2-common=2.0.54-5sarge2 apache2-utils=2.0.54-5sarge2 tomcat4 libtomcat4-java libant1.6-java
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  apache2-utils: Depends: libldap2 (>= 2.1.17-1) but it is not installable
                 Depends: libssl0.9.7 but it is not installable
E: Broken packages


---

