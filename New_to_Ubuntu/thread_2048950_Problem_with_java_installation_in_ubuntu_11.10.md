---
title: "Problem with java installation in ubuntu 11.10"
date: 2012-08-27
forum: New to Ubuntu
---

### Post by Rajeshwar Patra on 2012-08-27
Hi all,

I  am new to ubuntu.I tried to install jdk 7 using the command 

 sudo apt-get install openjdk-7-jdk


But I am getting the following error :

Errors were encountered while processing:
 oracle-java7-installer
 libaccess-bridge-java
 libaccess-bridge-java-jni
 openjdk-7-jre
 openjdk-7-jdk
E: Sub-process /usr/bin/dpkg returned an error code (1)


How to rectify the above error 


Thanks in advance 

Regards,
Rajeshwar

---

### Post by lechien73 on 2012-08-27
Hi and welcome to the forums,

Could you please try running:

```
sudo apt-get install -f
```

Then try your installation again. This command tries to repair the error that's preventing you from installing the package.

---

