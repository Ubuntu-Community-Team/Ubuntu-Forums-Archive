---
title: "Package operation failed"
date: 2012-05-23
forum: New to Ubuntu
---

### Post by matiko on 2012-05-23
Hi, I tried installing netbeans on ubuntu 12.04 LTS using the packages I found on apt-web.dahsy.at and this is what I got (The installation or removal of a software package failed.), and now software center wont install or remove any applications and its stuck in a loop cause it keeps on saying The installation or removal of a software package failed. when it tries to repair 


nstallArchives() failed: dpkg: dependency problems prevent configuration of tzdata-java: 
 tzdata-java depends on tzdata (= 2011f-1); however: 
  Version of tzdata on system is 2012b-1. 
dpkg: error processing tzdata-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnss3-1d: 
 libnss3-1d depends on libnss3 (= 3.12.9+ckbi-1.82-0ubuntu2); however: 
  Version of libnss3 on system is 3.13.1.with.ckbi.1.88-1ubuntu6. 
dpkg: error processing libnss3-1d (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jre-headless: 
 openjdk-6-jre-headless depends on tzdata-java; however: 
  Package tzdata-java is not configured yet. 
 openjdk-6-jre-headless depends on libnss3-1d (>= 3.12.3); however: 
  Package libnss3-1d is not configured yet. 
dpkg: error processing openjdk-6-jre-headless (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jre-liNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
b: 
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b17); however: 
  Package openjdk-6-jre-headless is not configured yet. 
dpkg: error processing openjdk-6-jre-lib (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jre: 
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b22-1.10.1-0ubuntu1); however: 
  Package openjdk-6-jre-headless is not configured yet. 
dpkg: error processing openjdk-6-jre (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of default-jre: 
 default-jre depends on openjdk-6-jre (>= 6b14); however: 
  Package openjdk-6-jre is not configured yet. 
dpkg: error processing default-jre (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jdk: 
 openjdk-6-jdk depends on openjdk-6-jre (>= 6b22-1.10.1-0ubuntu1); however: 
  Package openjdk-6-jre is not configured yet. 
dpkg: error processNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
ing openjdk-6-jdk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of default-jdk: 
 default-jdk depends on default-jre (= 1:1.6-40ubuntu1); however: 
  Package default-jre is not configured yet. 
 default-jdk depends on openjdk-6-jdk (>= 6b14); however: 
  Package openjdk-6-jdk is not configured yet. 
dpkg: error processing default-jdk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of javahelp2: 
 javahelp2 depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing javahelp2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of jruby1.1: 
 jruby1.1 depends on default-jre | java5-runtime | java6-runtime; however: 
  Package default-jre is not configured yet. 
  Package java5-runtime is not installed. 
  Package default-jre which provides java5-runtime is not configured yet. 
  Package openjdk-6-jre which provides java5-runtime is not configured yet. 
  Package java6-runtime is not installed. 
  Package default-jre which provides java6-runtime is not configured yet. 
  Package openjdk-6-jre which provides java6-runtime is not configured yet. 
dpkg: error processing jruby1.1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libaccess-bridge-java: 
 libaccess-bridge-java depends on default-jre | openjdk-6-jre | sun-java6-jre; however: 
  Package default-jre is not configured yet. 
  Package openjdk-6-jre is not configured yet. 
  Package sun-java6-jre is not installed. 
dpkg: error processing libaccess-bridge-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libaccess-bridge-java-jni: 
 libaccess-bridge-java-jni depends on libaccess-bridge-java (>= 1.26.2-5); however: 
  Package libaccess-bridge-java is not configured yet. 
dpkg: error processing libaccess-bridge-java-jni (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libswingworker-java: 
 libswingworker-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libswingworker-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libappframework-java: 
 libappframework-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
 libappframework-java depends on libswingworker-java (>= 1.1); however: 
  Package libswingworker-java is not configured yet. 
dpkg: error processing libappframework-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libbeansbinding-java: 
 libbeansbinding-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libbeansbinding-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libjna-java: 
 libjna-java depends on libffi5 (>= 3.0.4); however: 
  Package libffi5 is not installed. 
 libc6-dev (2.15-0ubuntu10) breaks libjna-java (<< 3.2.7-4) and is installed. 
  Version of libjna-java to be configured is 3.2.4-2ubuntu2. 
dpkg: error processing libjna-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libswing-layout-java: 
 libswing-layout-java depends on java-gcj-compat | java1-runtime | java2-runtime; however: 
  Package java-gcj-compat is not installed. 
  Package java1-runtime is not installed. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libswing-layout-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-platform12-java: 
 libnb-platform12-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
 libnb-platform12-java depends on javahelp2; however: 
  Package javahelp2 is not configured yet. 
 libnb-platform12-java depends on libswing-layout-java (>= 1.0.3); however: 
  Package libswing-layout-java is not configured yet. 
 libnb-platform12-java depends on libjna-java (>= 3.1.0); however: 
  Package libjna-java is not configured yet. 
dpkg: error processing libnb-platform12-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-platform-devel-java: 
 libnb-platform-devel-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
 libnb-platform-devel-java depends on javahelp2; however: 
  Package javahelp2 is not configured yet. 
 libnb-platform-devel-java depends on libnb-platform12-java; however: 
  Package libnb-platform12-java is not configured yet. 
dpkg: error processing libnb-platform-devel-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libxml-commons-resolver1.1-java: 
 libxml-commons-resolver1.1-java depends on classpath-common | java1-runtime | java2-runtime; however: 
  Package classpath-common is not installed. 
  Package java1-runtime is not installed. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libxml-commons-resolver1.1-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-ide13-java: 
 libnb-ide13-java depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 libnb-ide13-java depends on libxml-commons-resolver1.1-java (>= 1.2-3); however: 
  Package libxml-commons-resolver1.1-java is not configured yet. 
 libnb-ide13-java depends on jruby1.1; however: 
  Package jruby1.1 is not configured yet. 
dpkg: error processing libnb-ide13-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-java4-java: 
 libnb-java4-java depends on default-jdk | sun-java6-jdk; however: 
  Package default-jdk is not configured yet. 
  Package sun-java6-jdk is not installed. 
 libnb-java4-java depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 libnb-java4-java depends on libnb-ide13-java (= 6.9-0ubuntu2); however: 
  Package libnb-ide13-java is not configured yet. 
 libnb-java4-java depends on libappframework-java; however: 
  Package libappframework-java is not configured yet. 
 libnb-java4-java depends on libbeansbinding-java; however: 
  Package libbeansbinding-java is not configured yet. 
 libnb-java4-java depends on libswingworker-java; however: 
  Package libswingworker-java is not configured yet. 
dpkg: error processing libnb-java4-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-apisupport2-java: 
 libnb-apisupport2-java depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 libnb-apisupport2-java depends on libnb-platform-devel-java (>= 6.9); however: 
  Package libnb-platform-devel-java is not configured yet. 
 libnb-apisupport2-java depends on libnb-ide13-java (= 6.9-0ubuntu2); however: 
  Package libnb-ide13-java is not configured yet. 
 libnb-apisupport2-java depends on libnb-java4-java (= 6.9-0ubuntu2); however: 
  Package libnb-java4-java is not configured yet. 
dpkg: error processing libnb-apisupport2-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of netbeans: 
 netbeans depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 netbeans depends on libnb-ide13-java (= 6.9-0ubuntu2); however: 
  Package libnb-ide13-java is not configured yet. 
 netbeans depends on libnb-java4-java (= 6.9-0ubuntu2); however: 
  Package libnb-java4-java is not configured yet. 
 netbeans depends on libnb-apisupport2-java (= 6.9-0ubuntu2); however: 
  Package libnb-apisupport2-java is not configured yet. 
dpkg: error processing netbeans (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao: 
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b24-1.11.1-4ubuntu3); however: 
  Version of openjdk-6-jre-headless on system is 6b22-1.10.1-0ubuntu1. 
dpkg: error processing icedtea-6-jre-cacaoNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm: 
 icedtea-6-jre-jamvm depends on openjdk-6-jre-headless (= 6b24-1.11.1-4ubuntu3); however: 
  Version of openjdk-6-jre-headless on system is 6b22-1.10.1-0ubuntu1. 
dpkg: error processing icedtea-6-jre-jamvm (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of default-jre-headless: 
 default-jre-headless depends on openjdk-6-jre-headless (>= 6b14); however: 
  Package openjdk-6-jre-headless is not configured yet. 
dpkg: error processing default-jre-headless (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ca-certificates-java: 
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however: 
  Package openjdk-6-jre-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
k-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
dpkg: error processing ca-certificates-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libxerces2-java: 
 libxerces2-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libxerces2-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ant: 
 ant depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
 ant depends on libxerces2-java; however: 
  Package libxerces2-java is not configured yet. 
dpkg: error processing ant (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ant-optional: 
 ant-optional depends on ant (= 1.8.1-1); however: 
  Package ant is not configured yet. 
dpkg: error processing ant-optional (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of junit: 
 junit depends on default-jre (>= 1.4) | default-jre-headless (>= 1.4) | java2-runtime | java2-runtime-headless; however: 
  Package default-jre is not configured yet. 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing junit (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of junit4: 
 junit4 depends on default-jre-headless | java5-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
dpkg: error processing junit4 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libasm3-java: 
 libasm3-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libasm3-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libbindex-java: 
 libbindex-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libbindex-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liboro-java: 
 liboro-java depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
dpkg: error processing liboro-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcobertura-java: 
 libcobertura-java depends on ant (>= 1.7.0-6); however: 
  Package ant is not configured yet. 
 libcobertura-java depends on liboro-java (>= 2.0.8a-4); however: 
  Package liboro-java is not configured yet. 
 libcobertura-java depends on libasm3-java (>= 3.1-2); however: 
  Package libasm3-java is not configured yet. 
dpkg: error processing libcobertura-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcommons-logging-java: 
 libcommons-logging-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libcommons-logging-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcommons-net-java: 
 libcommons-net-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
 libcommons-net-java depends on liboro-java (>= 2.0.8); however: 
  Package liboro-java is not configured yet. 
dpkg: error processing libcommons-net-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfelix-framework-java: 
 libfelix-framework-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libfelix-framework-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfelix-main-java: 
 libfelix-main-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
 libfelix-main-java depends on libfelix-framework-java; however: 
  Package libfelix-framework-java is not configured yet. 
dpkg: error processing libfelix-main-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfreemarker-java: 
 libfreemarker-java depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configureNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
d yet. 
dpkg: error processing libfreemarker-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libini4j-java: 
 libini4j-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libini4j-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libjzlib-java: 
 libjzlib-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libjzlib-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liblucene2-java: 
 liblucene2-java depends on openjdk-6-jre-headless | java5-runtime-headless; however: 
  Package openjdk-6-jre-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
dpkg: error processing liblucene2-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libsvn-java: 
 libsvn-java depends on default-jre-headless | java5-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
dpkg: error processing libsvn-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-svnclientadapter-java: 
 libnb-svnclientadapter-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
 libnb-svnclientadapter-java depends on libsvn-java; however: 
  Package libsvn-java is not configured yet. 
dpkg: error processing libnb-svnclientadapter-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libservlet2.3-java: 
 libservlet2.3-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libservlet2.3-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-javaparser-java: 
 libnb-javaparser-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libnb-javaparser-java (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 tzdata-java 
 libnss3-1d 
 openjdk-6-jre-headless 
 openjdk-6-jre-lib 
 openjdk-6-jre 
 default-jre 
 openjdk-6-jdk 
 default-jdk 
 javahelp2 
 jruby1.1 
 libaccess-bridge-java 
 libaccess-bridge-java-jni 
 libswingworker-java 
 libappframework-java 
 libbeansbinding-java 
 libjna-java 
 libswing-layout-java 
 libnb-platform12-java 
 libnb-platform-devel-java 
 libxml-commons-resolver1.1-java 
 libnb-ide13-java 
 libnb-java4-java 
 libnb-apisupport2-java 
 netbeans 
 icedtea-6-jre-cacao 
 icedtea-6-jre-jamvm 
 default-jre-headless 
 ca-certificates-java 
 libxerces2-java 
 ant 
 ant-optional 
 junit 
 junit4 
 libasm3-java 
 libbindex-java 
 liboro-java 
 libcobertura-java 
 libcommons-logging-java 
 libcommons-net-java 
 libfelix-framework-java 
 libfelix-main-java 
 libfreemarker-java 
dpkg: dependency problems prevent configuration of libjna-java: 
 libjna-java depends on libffi5 (>= 3.0.4); however: 
  Package libffi5 is not installed. 
 libc6-dev (2.15-0ubuntu10) breaks libjna-java (<< 3.2.7-4) and is installed. 
  Version of libjna-java to be configured is 3.2.4-2ubuntu2. 
dpkg: error processing libjna-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of tzdata-java: 
 tzdata-java depends on tzdata (= 2011f-1); however: 
  Version of tzdata on system is 2012b-1. 
dpkg: error processing tzdata-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of icedtea-6-jre-jamvm: 
 icedtea-6-jre-jamvm depends on openjdk-6-jre-headless (= 6b24-1.11.1-4ubuntu3); however: 
  Version of openjdk-6-jre-headless on system is 6b22-1.10.1-0ubuntu1. 
dpkg: error processing icedtea-6-jre-jamvm (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnss3-1d: 
 libnss3-1d depends on libnss3 (= 3.12.9+ckbi-1.82-0ubuntu2); however: 
  Version of libnss3 on system is 3.13.1.with.ckbi.1.88-1ubuntu6. 
dpkg: error processing libnss3-1d (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jre-headless: 
 openjdk-6-jre-headless depends on tzdata-java; however: 
  Package tzdata-java is not configured yet. 
 openjdk-6-jre-headless depends on libnss3-1d (>= 3.12.3); however: 
  Package libnss3-1d is not configured yet. 
dpkg: error processing openjdk-6-jre-headless (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jre: 
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b22-1.10.1-0ubuntu1); however: 
  Package openjdk-6-jre-headless is not configured yet. 
dpkg: error processing openjdk-6-jre (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jre-lib: 
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b17); however: 
  Package openjdk-6-jre-headless is not configured yet. 
dpkg: error processing openjdk-6-jre-lib (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of default-jre: 
 default-jre depends on openjdk-6-jre (>= 6b14); however: 
  Package openjdk-6-jre is not configured yet. 
dpkg: error processing default-jre (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-platform12-java: 
 libnb-platform12-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
 libnb-platform12-java depends on libjna-java (>= 3.1.0); however: 
  Package libjna-java is not configured yet. 
dpkg: error processing libnb-platform12-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of icedtea-6-jre-cacao: 
 icedtea-6-jre-cacao depends on openjdk-6-jre-headless (= 6b24-1.11.1-4ubuntu3); however: 
  Version of openjdk-6-jre-headless on system is 6b22-1.10.1-0ubuntu1. 
dpkg: error processing icedtea-6-jre-cacao (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-platform-devel-java: 
 libnb-platform-devel-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
 libnb-platform-devel-java depends on libnb-platform12-java; however: 
  Package libnb-platform12-java is not configured yet. 
dpkg: error processing libnb-platform-devel-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of jruby1.1: 
 jruby1.1 depends on default-jre | java5-runtime | java6-runtime; however: 
  Package default-jre is not configured yet. 
  Package java5-runtime is not installed. 
  Package default-jre which provides java5-runtime is not configured yet. 
  Package openjdk-6-jre which provides java5-runtime is not configured yet. 
  Package java6-runtime is not installed. 
  Package default-jre which provides java6-runtime is not configured yet. 
  Package openjdk-6-jre which provides java6-runtime is not configured yet. 
dpkg: error processing jruby1.1 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libxml-commons-resolver1.1-java: 
 libxml-commons-resolver1.1-java depends on classpath-common | java1-runtime | java2-runtime; however: 
  Package classpath-common is not installed. 
  Package java1-runtime is not installed. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libxml-commons-resolver1.1-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libappframework-java: 
 libappframework-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libappframework-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-java4-java: 
 libnb-java4-java depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 libnb-java4-java depends on libappframework-java; however: 
  Package libappframework-java is not configured yet. 
dpkg: error processing libnb-java4-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libswingworker-java: 
 libswingworker-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libswingworker-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of openjdk-6-jdk: 
 openjdk-6-jdk depends on openjdk-6-jre (>= 6b22-1.10.1-0ubuntu1); however: 
  Package openjdk-6-jre is not configured yet. 
dpkg: error processing openjdk-6-jdk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of javahelp2: 
 javahelp2 depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing javahelp2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-apisupport2-java: 
 libnb-apisupport2-java depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 libnb-apisupport2-java depends on libnb-platform-devel-java (>= 6.9); however: 
  Package libnb-platform-devel-java is not configured yet. 
 libnb-apisupport2-java depends on libnb-java4-java (= 6.9-0ubuntu2); however: 
  Package libnb-java4-java is not configured yet. 
dpkg: error processing libnb-apisupport2-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libswing-layout-java: 
 libswing-layout-java depends on java-gcj-compat | java1-runtime | java2-runtime; however: 
  Package java-gcj-compat is not installed. 
  Package java1-runtime is not installed. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libswing-layout-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of default-jre-headless: 
 default-jre-headless depends on openjdk-6-jre-headless (>= 6b14); however: 
  Package openjdk-6-jre-headless is not configured yet. 
dpkg: error processing default-jre-headless (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of default-jdk: 
 default-jdk depends on default-jre (= 1:1.6-40ubuntu1); however: 
  Package default-jre is not configured yet. 
 default-jdk depends on openjdk-6-jdk (>= 6b14); however: 
  Package openjdk-6-jdk is not configured yet. 
dpkg: error processing default-jdk (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ca-certificates-java: 
 ca-certificates-java depends on openjdk-6-jre-headless (>= 6b16-1.6.1-2) | java6-runtime-headless; however: 
  Package openjdk-6-jre-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
dpkg: error processing ca-certificates-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libbeansbinding-java: 
 libbeansbinding-java depends on default-jre | java2-runtime; however: 
  Package default-jre is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
dpkg: error processing libbeansbinding-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-javaparser-java: 
 libnb-javaparser-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libnb-javaparser-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of junit4: 
 junit4 depends on default-jre-headless | java5-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
dpkg: error processing junit4 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of netbeans: 
 netbeans depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 netbeans depends on libnb-java4-java (= 6.9-0ubuntu2); however: 
  Package libnb-java4-java is not configured yet. 
 netbeans depends on libnb-apisupport2-java (= 6.9-0ubuntu2); however: 
  Package libnb-apisupport2-java is not configured yet. 
dpkg: error processing netbeans (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfreemarker-java: 
 libfreemarker-java depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
dpkg: error processing libfreemarker-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfelix-main-java: 
 libfelix-main-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libfelix-main-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-ide13-java: 
 libnb-ide13-java depends on libnb-platform12-java (>= 6.9); however: 
  Package libnb-platform12-java is not configured yet. 
 libnb-ide13-java depends on libfreemarker-java; however: 
  Package libfreemarker-java is not configured yet. 
 libnb-ide13-java depends on libxml-commons-resolver1.1-java (>= 1.2-3); however: 
  Package libxml-commons-resolver1.1-java is not configured yet. 
 libnb-ide13-java depends on jruby1.1; however: 
  Package jruby1.1 is not configured yet. 
dpkg: error processing libnb-ide13-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcommons-logging-java: 
 libcommons-logging-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libcommons-logging-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libaccess-bridge-java: 
 libaccess-bridge-java depends on default-jre | openjdk-6-jre | sun-java6-jre; however: 
  Package default-jre is not configured yet. 
  Package openjdk-6-jre is not configured yet. 
  Package sun-java6-jre is not installed. 
dpkg: error processing libaccess-bridge-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcommons-net-java: 
 libcommons-net-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libcommons-net-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libfelix-framework-java: 
 libfelix-framework-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libfelix-framework-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libjzlib-java: 
 libjzlib-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libjzlib-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libbindex-java: 
 libbindex-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libbindex-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libini4j-java: 
 libini4j-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libini4j-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ant: 
 ant depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
dpkg: error processing ant (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liblucene2-java: 
 liblucene2-java depends on openjdk-6-jre-headless | java5-runtime-headless; however: 
  Package openjdk-6-jre-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
dpkg: error processing liblucene2-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of liboro-java: 
 liboro-java depends on default-jre-headless | java2-runtime-headless | java5-runtime-headless | java6-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package java6-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java6-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java6-runtime-headless is not configured yet. 
dpkg: error processing liboro-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libservlet2.3-java: 
 libservlet2.3-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libservlet2.3-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libnb-svnclientadapter-java: 
 libnb-svnclientadapter-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libnb-svnclientadapter-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of junit: 
 junit depends on default-jre (>= 1.4) | default-jre-headless (>= 1.4) | java2-runtime | java2-runtime-headless; however: 
  Package default-jre is not configured yet. 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime is not installed. 
  Package default-jre which provides java2-runtime is not configured yet. 
  Package openjdk-6-jre which provides java2-runtime is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing junit (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libsvn-java: 
 libsvn-java depends on default-jre-headless | java5-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java5-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java5-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java5-runtime-headless is not configured yet. 
dpkg: error processing libsvn-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libxerces2-java: 
 libxerces2-java depends on default-jre-headless | java1-runtime-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java1-runtime-headless is not installed. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libxerces2-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libasm3-java: 
 libasm3-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package openjdk-6-jre-headless which provides java2-runtime-headless is not configured yet. 
  Package default-jre-headless which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libasm3-java (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libaccess-bridge-java-jni: 
 libaccess-bridge-java-jni depends on libaccess-bridge-java (>= 1.26.2-5); however: 
  Package libaccess-bridge-java is not configured yet. 
dpkg: error processing libaccess-bridge-java-jni (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ant-optional: 
 ant-optional depends on ant (= 1.8.1-1); however: 
  Package ant is not configured yet. 
dpkg: error processing ant-optional (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libcobertura-java: 
 libcobertura-java depends on ant (>= 1.7.0-6); however: 
  Package ant is not configured yet. 
 libcobertura-java depends on liboro-java (>= 2.0.8a-4); however: 
  Package liboro-java is not configured yet. 
 libcobertura-java depends on libasm3-java (>= 3.1-2); however: 
  Package libasm3-java is not configured yet. 
dpkg: error processing libcobertura-java (--configure): 
 dependency problems - leaving unconfigured

---

### Post by Enigmapond on 2012-05-23
No solutions but can you please edit you post and use the CODE tags?

---

### Post by diesch on 2012-05-23
There are no packages for Ubuntu 12.04 but only for older version of Ubuntu at apt-web.dahsy.at. 

At least some packages you installed from there are not compatible with Ubuntu12.04 and lead to the errors you see.

Run
```
sudo apt-get -f install
```
That should remove the incompatible packages. Then try to find another source for netbeans packages that has packages made for Ubuntu 12.04

---

