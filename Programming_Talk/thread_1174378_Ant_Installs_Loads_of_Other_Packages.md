---
title: "Ant Installs Loads of Other Packages"
date: 2009-05-30
forum: Programming Talk
---

### Post by opticyclic on 2009-05-30
I just tried to apt-get ant and it wants to download 101MB of other packages!
Why are 2 different JREs and JDKs seemingly being included?
Why are any JREs/JDKs being installed for that matter?
```
user@myPC ~ $ sudo apt-get install ant
[sudo] password for user: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  ant-gcj ant-optional ant-optional-gcj ca-certificates-java default-jdk
  default-jre default-jre-headless gcj-4.3-base icedtea-6-jre-cacao
  libaccess-bridge-java libgcj-bc libgcj-common libgcj9-0 libgcj9-jar
  libice-dev libjaxp1.3-java libjaxp1.3-java-gcj libpthread-stubs0
  libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxerces2-java-gcj libxt-dev openjdk-6-jdk
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib rhino ttf-baekmuk
  ttf-bengali-fonts ttf-indic-fonts-core ttf-kannada-fonts ttf-kochi-mincho
  ttf-oriya-fonts ttf-sazanami-mincho ttf-telugu-fonts ttf-wqy-zenhei
  tzdata-java x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
Suggested packages:
  ant-doc libbsf-java liboro-java libxalan2-java junit liblog4j1.2-java
  libregexp-java jython antlr libbcel-java libcommons-logging-java
  libjdepend-java libgnumail-java libxml-commons-resolver1.1-java
  libcommons-net-java libjsch-java javacc libgcj9-dbg libgcj9-0-awt
  libxerces2-java-doc openjdk-6-demo openjdk-6-source visualvm icedtea6-plugin
  sun-java6-fonts rhino-doc ttf-kochi-gothic ttf-kochi-gothic-naga10
The following NEW packages will be installed
  ant ant-gcj ant-optional ant-optional-gcj ca-certificates-java default-jdk
  default-jre default-jre-headless gcj-4.3-base icedtea-6-jre-cacao
  libaccess-bridge-java libgcj-bc libgcj-common libgcj9-0 libgcj9-jar
  libice-dev libjaxp1.3-java libjaxp1.3-java-gcj libpthread-stubs0
  libpthread-stubs0-dev libsm-dev libx11-dev libxau-dev libxcb1-dev
  libxdmcp-dev libxerces2-java libxerces2-java-gcj libxt-dev openjdk-6-jdk
  openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib rhino ttf-baekmuk
  ttf-bengali-fonts ttf-indic-fonts-core ttf-kannada-fonts ttf-kochi-mincho
  ttf-oriya-fonts ttf-sazanami-mincho ttf-telugu-fonts ttf-wqy-zenhei
  tzdata-java x11proto-core-dev x11proto-input-dev x11proto-kb-dev xtrans-dev
0 upgraded, 47 newly installed, 0 to remove and 0 not upgraded.
Need to get 101MB of archives.
After this operation, 260MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
user@myPC ~ $ java -version
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) Server VM (build 11.3-b02, mixed mode)
user@myPC ~ $ 

```
As you can see from the command at the bottom, I already have Java installed.
I also have a separate JDK1.5 that I downloaded from the sun site that I use for my programming.
So why is apt installing all this extra rubbish?

---

