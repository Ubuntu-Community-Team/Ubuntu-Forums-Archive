---
title: "Just installed LibreOffice from USC"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by czgirb on 2012-06-27
Just installed **LibreOffice Base** from **USC** and ended like this:

```

**Package Installation Failed**
The Installation or Removal of a software failed

installArchives() failed: Selecting previously unselected package libservlet2.5-java. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 155025 files and directories currently installed.) 
Unpacking libservlet2.5-java (from .../libservlet2.5-java_6.0.35-1ubuntu3_all.deb) ... 
Selecting previously unselected package libhsqldb-java. 
Unpacking libhsqldb-java (from .../libhsqldb-java_1.8.0.10-9ubuntu2_all.deb) ... 
Selecting previously unselected package libxml-commons-resolver1.1-java. 
Unpacking libxml-commons-resolver1.1-java (from .../libxml-commons-resolver1.1-java_1.2-7_all.deb) ... 
Selecting previously unselected package libxml-commons-external-java. 
Unpacking libxml-commons-external-java (from .../libxml-commons-external-java_1.4.01-2_all.deb) ... 
Selecting previously unselected package libxerces2-java. 
Unpacking libxerces2-java (from .../libxerces2-java_2.11.0-4_all.deb) ... 
Selecting previously unselected package libreoffice-java-common. 
Unpacking libreoffice-java-common (from .../libreoffice-java-common_1%3a3.5.3-0ubuntu1_all.deb) ... 
Selecting previously unselected package libreoffice-base. 
Unpacking libreoffice-base (from .../libreoffice-base_1%3a3.5.3-0ubuntu1_i386.deb) ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-06-27 19:28:29--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 125.160.18.108, 125.160.18.98 
Connecting to download.oracle.com (download.oracle.com)|125.160.18.108|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following] 
--2012-06-27 19:28:30--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: http://download.oracle.com/errors/download-fail-1505220.html [following] 
--2012-06-27 19:28:32--  http://download.oracle.com/errors/download-fail-1505220.html 
Connecting to download.oracle.com (download.oracle.com)|125.160.18.108|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-i586.tar.gz' 
 
     0K .....                                                 100% 17.1K=0.3s 
 
2012-06-27 19:28:33 (17.1 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-i586.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up libservlet2.5-java (6.0.35-1ubuntu3) ... 
dpkg: dependency problems prevent configuration of libhsqldb-java: 
 libhsqldb-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not installed. 
  Package oracle-java7-installer which provides default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package oracle-java7-installer which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libhsqldb-java (--configure): 
 dependency problems - leaving unconfigured 
Setting up libxml-commons-resolver1.1-java (1.2-7) ... 
No apport report written because MaxReports is reached already
Setting up libxml-commons-external-java (1.4.01-2) ... 
Setting up libxerces2-java (2.11.0-4) ... 
Setting up libreoffice-java-common (1:3.5.3-0ubuntu1) ... 
dpkg: dependency problems prevent configuration of libreoffice-base: 
 libreoffice-base depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | openjdk-7-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however: 
  Package default-jre is not installed. 
  Package oracle-java7-installer which provides default-jre is not configured yet. 
  Package gcj-jre is not installed. 
  Package java-gcj-compat is not installed. 
  Package openjdk-6-jre is not installed. 
  Package openjdk-7-jre is not installed. 
  Package sun-java5-jre is not installed. 
  Package sun-java6-jre is not installed. 
  Package java5-runtime is not installed. 
  Package oracle-java7-installer which provides java5-runtime is not configured yet. 
  Package jre is not installed. 
 libreoffice-base depends on libhsqldb-java (>> 1.8.0.10); however: 
  Package libhsqldb-java is not configured yet. 
 libreoffice-base depends on libhsqldb-java (<< 1.8.1~); however: 
  Package libhsqldb-java is not configured yet. 
dpkg: error pNo apport report written because MaxReports is reached already
rocessing libreoffice-base (--configure): 
 dependency problems - leaving unconfigured 
Errors were encountered while processing: 
 oracle-java7-installer 
 libhsqldb-java 
 libreoffice-base 
Error in function:  
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ... 
Downloading... 
--2012-06-27 19:28:35--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz 
Resolving download.oracle.com (download.oracle.com)... 125.160.18.108, 125.160.18.98 
Connecting to download.oracle.com (download.oracle.com)|125.160.18.108|:80... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following] 
--2012-06-27 19:28:36--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz 
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.223.18.174 
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.223.18.174|:443... connected. 
HTTP request sent, awaiting response... 302 Moved Temporarily 
Location: http://download.oracle.com/errors/download-fail-1505220.html [following] 
--2012-06-27 19:28:38--  http://download.oracle.com/errors/download-fail-1505220.html 
Connecting to download.oracle.com (download.oracle.com)|125.160.18.108|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 5307 (5.2K) [text/html] 
Saving to: `./jdk-7u3-linux-i586.tar.gz' 
 
     0K .....                                                 100% 15.4K=0.3s 
 
2012-06-27 19:28:39 (15.4 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307] 
 
Download done. 
sha256sum mismatch jdk-7u3-linux-i586.tar.gz 
Oracle JDK 7 is NOT installed. 
dpkg: error processing oracle-java7-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of libreoffice-base: 
 libreoffice-base depends on default-jre | gcj-jre | java-gcj-compat | openjdk-6-jre | openjdk-7-jre | sun-java5-jre | sun-java6-jre | java5-runtime | jre; however: 
  Package default-jre is not installed. 
  Package oracle-java7-installer which provides default-jre is not configured yet. 
  Package gcj-jre is not installed. 
  Package java-gcj-compat is not installed. 
  Package openjdk-6-jre is not installed. 
  Package openjdk-7-jre is not installed. 
  Package sun-java5-jre is not installed. 
  Package sun-java6-jre is not installed. 
  Package java5-runtime is not installed. 
  Package oracle-java7-installer which provides java5-runtime is not configured yet. 
  Package jre is not installed. 
dpkg: error processing libreoffice-base (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libhsqldb-java: 
 libhsqldb-java depends on default-jre-headless | java2-runtime-headless; however: 
  Package default-jre-headless is not installed. 
  Package oracle-java7-installer which provides default-jre-headless is not configured yet. 
  Package java2-runtime-headless is not installed. 
  Package oracle-java7-installer which provides java2-runtime-headless is not configured yet. 
dpkg: error processing libhsqldb-java (--configure): 
 dependency problems - leaving unconfigured
```

Any solution?
Please help

---

### Post by cortman on 2012-06-27
First run

```
sudo apt-get install -f
```

And post output.

---

### Post by ajgreeny on 2012-06-27
The problem as you can no doubt see, appears to be related to sun-java packages, now actually Oracle-java, so I suggest that you forget about sun/oracle-java and use openjdk packages instead.  There was a time when they did not work as effectively as sun-java but that does not appear to be so any more, as far as I can see.

By all means try the command cortman gave you, but I suspect it will end with the same error as installing did, and if so I would remove sun-java packages, and then install openjdk in their place.

---

