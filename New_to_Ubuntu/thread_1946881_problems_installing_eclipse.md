---
title: "problems installing eclipse"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by rohanag on 2012-03-25
Hi

I'm trying to install eclipse on ubuntu 11.10 installed on my virtualbox, but I get the following error message:


```
saasbook@saasbook:~$ sudo apt-get install eclipse-platform
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ant ant-optional default-jdk eclipse-jdt eclipse-pde eclipse-platform-data
  eclipse-rcp fastjar gcj-4.6-base gcj-4.6-jre-lib jarwrapper junit junit4
  libart-2.0-2 libasm3-java libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libcommons-beanutils-java libcommons-codec-java
  libcommons-collections3-java libcommons-compress-java
  libcommons-digester-java libcommons-el-java libcommons-httpclient-java
  libcommons-logging-java libdb-java libdb-je-java libdb5.1-java
  libdb5.1-java-gcj libecj-java libequinox-osgi-java libgcj-bc libgcj-common
  libgcj12 libglade2-0 libgnome2-0 libgnomecanvas2-0 libgnomecanvas2-common
  libgnomeui-0 libgnomeui-common libhamcrest-java libice-dev libicu4j-4.4-java
  libicu4j-java libjasper-java libjaxp1.3-java libjetty-java libjline-java
  libjsch-java libjtidy-java liblucene2-java libpthread-stubs0
  libpthread-stubs0-dev libregexp-java libservlet2.4-java libservlet2.5-java
  libslf4j-java libsm-dev libx11-dev libxau-dev libxcb1-dev libxdmcp-dev
  libxerces2-java libxt-dev openjdk-6-jdk sat4j x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  ant-gcj ant-doc libbsf-java liboro-java libxalan2-java liblog4j1.2-java
  jython antlr libbcel-java libjdepend-java libgnumail-java
  libxml-commons-resolver1.1-java libcommons-net-java javacc ant-optional-gcj
  eclipse eclipse-plugin-cvs junit-doc libbonobo2-bin
  libcommons-beanutils-java-doc libcommons-collections3-java-doc
  java-virtual-machine libcommons-digester-java-doc
  libcommons-httpclient-java-doc libexcalibur-logkit-java
  libavalon-framework-java libcommons-logging-java-doc ecj libecj-java-gcj
  libgcj12-dbg libgcj12-awt libjaxp1.3-java-gcj jetty libjetty-java-doc
  libjline-java-doc libjtidy-java-doc libservlet2.4-java-gcj libjavassist-java
  libxerces2-java-doc libxerces2-java-gcj openjdk-6-demo openjdk-6-source
  visualvm
The following NEW packages will be installed:
  ant ant-optional default-jdk eclipse-jdt eclipse-pde eclipse-platform
  eclipse-platform-data eclipse-rcp fastjar gcj-4.6-base gcj-4.6-jre-lib
  jarwrapper junit junit4 libart-2.0-2 libasm3-java libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libcommons-beanutils-java libcommons-codec-java libcommons-collections3-java
  libcommons-compress-java libcommons-digester-java libcommons-el-java
  libcommons-httpclient-java libcommons-logging-java libdb-java libdb-je-java
  libdb5.1-java libdb5.1-java-gcj libecj-java libequinox-osgi-java libgcj-bc
  libgcj-common libgcj12 libglade2-0 libgnome2-0 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libhamcrest-java
  libice-dev libicu4j-4.4-java libicu4j-java libjasper-java libjaxp1.3-java
  libjetty-java libjline-java libjsch-java libjtidy-java liblucene2-java
  libpthread-stubs0 libpthread-stubs0-dev libregexp-java libservlet2.4-java
  libservlet2.5-java libslf4j-java libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxt-dev openjdk-6-jdk sat4j x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 74 newly installed, 0 to remove and 279 not upgraded.
Need to get 11.2 MB/206 MB of archives.
After this operation, 311 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main openjdk-6-jdk i386 6b23~pre11-0ubuntu1.11.10
  404  Not Found [IP: 91.189.92.177 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main openjdk-6-jdk i386 6b23~pre11-0ubuntu1.11.10
  404  Not Found [IP: 91.189.92.167 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main libservlet2.5-java all 6.0.32-5ubuntu1.1
  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jdk_6b23~pre11-0ubuntu1.11.10_i386.deb  404  Not Found [IP: 91.189.92.167 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.32-5ubuntu1.1_all.deb  404  Not Found [IP: 91.189.92.167 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
saasbook@saasbook:~$ sudo apt-get install eclipse eclipse-jdt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ant ant-optional default-jdk eclipse-pde eclipse-platform
  eclipse-platform-data eclipse-rcp fastjar gcj-4.6-base gcj-4.6-jre-lib
  jarwrapper junit junit4 libart-2.0-2 libasm3-java libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libcommons-beanutils-java libcommons-codec-java libcommons-collections3-java
  libcommons-compress-java libcommons-digester-java libcommons-el-java
  libcommons-httpclient-java libcommons-logging-java libdb-java libdb-je-java
  libdb5.1-java libdb5.1-java-gcj libecj-java libequinox-osgi-java libgcj-bc
  libgcj-common libgcj12 libglade2-0 libgnome2-0 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libhamcrest-java
  libice-dev libicu4j-4.4-java libicu4j-java libjasper-java libjaxp1.3-java
  libjetty-java libjline-java libjsch-java libjtidy-java liblucene2-java
  libpthread-stubs0 libpthread-stubs0-dev libregexp-java libservlet2.4-java
  libservlet2.5-java libslf4j-java libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxt-dev openjdk-6-jdk sat4j x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  ant-gcj ant-doc libbsf-java liboro-java libxalan2-java liblog4j1.2-java
  jython antlr libbcel-java libjdepend-java libgnumail-java
  libxml-commons-resolver1.1-java libcommons-net-java javacc ant-optional-gcj
  eclipse-plugin-cvs junit-doc libbonobo2-bin libcommons-beanutils-java-doc
  libcommons-collections3-java-doc java-virtual-machine
  libcommons-digester-java-doc libcommons-httpclient-java-doc
  libexcalibur-logkit-java libavalon-framework-java
  libcommons-logging-java-doc ecj libecj-java-gcj libgcj12-dbg libgcj12-awt
  libjaxp1.3-java-gcj jetty libjetty-java-doc libjline-java-doc
  libjtidy-java-doc libservlet2.4-java-gcj libjavassist-java
  libxerces2-java-doc libxerces2-java-gcj openjdk-6-demo openjdk-6-source
  visualvm
The following NEW packages will be installed:
  ant ant-optional default-jdk eclipse eclipse-jdt eclipse-pde
  eclipse-platform eclipse-platform-data eclipse-rcp fastjar gcj-4.6-base
  gcj-4.6-jre-lib jarwrapper junit junit4 libart-2.0-2 libasm3-java
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libcommons-beanutils-java libcommons-codec-java libcommons-collections3-java
  libcommons-compress-java libcommons-digester-java libcommons-el-java
  libcommons-httpclient-java libcommons-logging-java libdb-java libdb-je-java
  libdb5.1-java libdb5.1-java-gcj libecj-java libequinox-osgi-java libgcj-bc
  libgcj-common libgcj12 libglade2-0 libgnome2-0 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libhamcrest-java
  libice-dev libicu4j-4.4-java libicu4j-java libjasper-java libjaxp1.3-java
  libjetty-java libjline-java libjsch-java libjtidy-java liblucene2-java
  libpthread-stubs0 libpthread-stubs0-dev libregexp-java libservlet2.4-java
  libservlet2.5-java libslf4j-java libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxt-dev openjdk-6-jdk sat4j x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 75 newly installed, 0 to remove and 279 not upgraded.
Need to get 11.2 MB/206 MB of archives.
After this operation, 311 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main openjdk-6-jdk i386 6b23~pre11-0ubuntu1.11.10
  404  Not Found [IP: 91.189.92.176 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main openjdk-6-jdk i386 6b23~pre11-0ubuntu1.11.10
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main libservlet2.5-java all 6.0.32-5ubuntu1.1
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jdk_6b23~pre11-0ubuntu1.11.10_i386.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.32-5ubuntu1.1_all.deb  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
saasbook@saasbook:~$ ubuntu
ubuntu: command not found
saasbook@saasbook:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
saasbook@saasbook:~$ sudo apt-get install eclipse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ant ant-optional default-jdk eclipse-jdt eclipse-pde eclipse-platform
  eclipse-platform-data eclipse-rcp fastjar gcj-4.6-base gcj-4.6-jre-lib
  jarwrapper junit junit4 libart-2.0-2 libasm3-java libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libcommons-beanutils-java libcommons-codec-java libcommons-collections3-java
  libcommons-compress-java libcommons-digester-java libcommons-el-java
  libcommons-httpclient-java libcommons-logging-java libdb-java libdb-je-java
  libdb5.1-java libdb5.1-java-gcj libecj-java libequinox-osgi-java libgcj-bc
  libgcj-common libgcj12 libglade2-0 libgnome2-0 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libhamcrest-java
  libice-dev libicu4j-4.4-java libicu4j-java libjasper-java libjaxp1.3-java
  libjetty-java libjline-java libjsch-java libjtidy-java liblucene2-java
  libpthread-stubs0 libpthread-stubs0-dev libregexp-java libservlet2.4-java
  libservlet2.5-java libslf4j-java libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxt-dev openjdk-6-jdk sat4j x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  ant-gcj ant-doc libbsf-java liboro-java libxalan2-java liblog4j1.2-java
  jython antlr libbcel-java libjdepend-java libgnumail-java
  libxml-commons-resolver1.1-java libcommons-net-java javacc ant-optional-gcj
  eclipse-plugin-cvs junit-doc libbonobo2-bin libcommons-beanutils-java-doc
  libcommons-collections3-java-doc java-virtual-machine
  libcommons-digester-java-doc libcommons-httpclient-java-doc
  libexcalibur-logkit-java libavalon-framework-java
  libcommons-logging-java-doc ecj libecj-java-gcj libgcj12-dbg libgcj12-awt
  libjaxp1.3-java-gcj jetty libjetty-java-doc libjline-java-doc
  libjtidy-java-doc libservlet2.4-java-gcj libjavassist-java
  libxerces2-java-doc libxerces2-java-gcj openjdk-6-demo openjdk-6-source
  visualvm
The following NEW packages will be installed:
  ant ant-optional default-jdk eclipse eclipse-jdt eclipse-pde
  eclipse-platform eclipse-platform-data eclipse-rcp fastjar gcj-4.6-base
  gcj-4.6-jre-lib jarwrapper junit junit4 libart-2.0-2 libasm3-java
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common
  libcommons-beanutils-java libcommons-codec-java libcommons-collections3-java
  libcommons-compress-java libcommons-digester-java libcommons-el-java
  libcommons-httpclient-java libcommons-logging-java libdb-java libdb-je-java
  libdb5.1-java libdb5.1-java-gcj libecj-java libequinox-osgi-java libgcj-bc
  libgcj-common libgcj12 libglade2-0 libgnome2-0 libgnomecanvas2-0
  libgnomecanvas2-common libgnomeui-0 libgnomeui-common libhamcrest-java
  libice-dev libicu4j-4.4-java libicu4j-java libjasper-java libjaxp1.3-java
  libjetty-java libjline-java libjsch-java libjtidy-java liblucene2-java
  libpthread-stubs0 libpthread-stubs0-dev libregexp-java libservlet2.4-java
  libservlet2.5-java libslf4j-java libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxt-dev openjdk-6-jdk sat4j x11proto-core-dev
  x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools xtrans-dev
0 upgraded, 75 newly installed, 0 to remove and 279 not upgraded.
Need to get 11.2 MB/206 MB of archives.
After this operation, 311 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Err http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main openjdk-6-jdk i386 6b23~pre11-0ubuntu1.11.10
  404  Not Found [IP: 91.189.92.184 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main openjdk-6-jdk i386 6b23~pre11-0ubuntu1.11.10
  404  Not Found [IP: 91.189.92.166 80]
Err http://security.ubuntu.com/ubuntu/ oneiric-security/main libservlet2.5-java all 6.0.32-5ubuntu1.1
  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/o/openjdk-6/openjdk-6-jdk_6b23~pre11-0ubuntu1.11.10_i386.deb  404  Not Found [IP: 91.189.92.166 80]
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/t/tomcat6/libservlet2.5-java_6.0.32-5ubuntu1.1_all.deb  404  Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
```

Any idea how I can install eclipse? Thanks.

---

### Post by rohanag on 2012-03-25
resolved, sorry :)
I just needed to run sudo apt-get update

---

