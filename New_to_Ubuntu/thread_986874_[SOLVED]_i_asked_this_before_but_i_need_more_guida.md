---
title: "[SOLVED] i asked this before but i need more guidance with more step by step"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by aszxcv on 2008-11-19
how do i get 
1.java  virtual machine installed
2.java sdk 6 update 10
3.netbeans 6.5

ubuntu 8.04

---

### Post by rzrgenesys187 on 2008-11-19
```
sudo apt-get install sun-java6-jdk netbeans
```

Just type this into the terminal and it will get you jdk 6, as well as all the other dependencies (including java virtual machine I would suspect) and it will install netbeans

---

### Post by aszxcv on 2008-11-19
this is what i see but no where netbeans 6.5 or jvm

```
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ant ant-optional java-common javahelp2 junit junit4 libaccess-bridge-java
  libappframework-java libapr1 libaprutil1 libbeansbinding-java
  libcommons-beanutils-java libcommons-collections3-java
  libcommons-digester-java libcommons-logging-java libdb4.5-java
  libfreemarker-java libgif4 libini4j-java libjaxp1.3-java libjline-java
  libjsch-java libjtidy-java liblucene2-java libnb-apisupport1-java
  libnb-ide8-java libnb-java1-java libnb-javaparser-java
  libnb-platform7-devel-java libnb-platform7-java libnb-svnclientadapter-java
  libpq5 libregexp-java libservlet2.3-java libsvn1 libswing-layout-java
  libswingworker-java libxerces2-java libxml-commons-resolver1.1-java
  odbcinst1debian1 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  rhino subversion sun-java6-bin sun-java6-jre unixodbc
Suggested packages:
  ant-doc libbsf-java liboro-java libxalan2-java liblog4j1.2-java jython antlr
  libbcel-java libjdepend-java libgnumail-java libcommons-net-java javacc
  equivs javahelp2-doc junit-doc libappframework-java-doc
  libswingworker-java-doc libcommons-beanutils-java-doc
  libcommons-collections3-java-doc liblogkit-java libavalon-framework-java
  libjline-java-doc libjtidy-java-doc libswing-layout-java-doc
  libxerces2-java-doc libxml-commons-resolver1.1-java-doc icedtea-gcjwebplugin
  sun-java6-fonts rhino-doc db4.6-util patch subversion-tools binfmt-support
  sun-java6-demo sun-java6-doc sun-java6-source sun-java6-plugin
  ia32-sun-java6-plugin libct1 libmyodbc odbc-postgresql
Recommended packages:
  ant-gcj ant-optional-gcj libdb4.5-java-gcj jetty libservlet2.4-java
  libjaxp1.3-java-gcj libxerces2-java-gcj ttf-bengali-fonts ttf-kannada-fonts
  ttf-oriya-fonts ttf-telugu-fonts ttf-wqy-zenhei ca-certificates-java
  tzdata-java gsfonts-x11
The following NEW packages will be installed:
  ant ant-optional java-common javahelp2 junit junit4 libaccess-bridge-java
  libappframework-java libapr1 libaprutil1 libbeansbinding-java
  libcommons-beanutils-java libcommons-collections3-java
  libcommons-digester-java libcommons-logging-java libdb4.5-java
  libfreemarker-java libgif4 libini4j-java libjaxp1.3-java libjline-java
  libjsch-java libjtidy-java liblucene2-java libnb-apisupport1-java
  libnb-ide8-java libnb-java1-java libnb-javaparser-java
  libnb-platform7-devel-java libnb-platform7-java libnb-svnclientadapter-java
  libpq5 libregexp-java libservlet2.3-java libsvn1 libswing-layout-java
  libswingworker-java libxerces2-java libxml-commons-resolver1.1-java netbeans
  odbcinst1debian1 openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib
  rhino subversion sun-java6-bin sun-java6-jdk sun-java6-jre unixodbc
0 upgraded, 50 newly installed, 0 to remove and 0 not upgraded.
Need to get 113MB of archives.
After this operation, 332MB of additional disk space will be used.
```

---

### Post by rzrgenesys187 on 2008-11-19
If you hit Ctrl+F in firefox and type netbeans (searching what you copied and pasted) you will see it is listed under the new packages that will be installed section.  Also listed here is sun-java6-jre which contains jvm.

---

### Post by aszxcv on 2008-11-19
ok thanks

i am @ the point where i must Configuring sun-java6-jre and&#9474;                                                                                                        
accept the licensing

but i press enter to accept but nothings happens

---

### Post by rzrgenesys187 on 2008-11-19
Press right to highlight OK or whatever and then press enter

---

### Post by aszxcv on 2008-11-19
i am   pressing and right clicking  but it wont accepted it

---

### Post by aszxcv on 2008-11-19
thanks for the help i got it to accept

---

