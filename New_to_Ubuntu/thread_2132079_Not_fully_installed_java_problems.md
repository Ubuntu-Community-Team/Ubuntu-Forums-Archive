---
title: "Not fully installed java problems"
date: 2013-04-03
forum: New to Ubuntu
---

### Post by SchrodingerCat on 2013-04-03
Hi, i tried to install Java7 and something went wrong..the problem is that now i can't neither install it again or delete it, it just says end operation with exit code 1.
this is my code after trying to instal it again.

```
 eading package lists... DoneBuilding dependency tree       
Reading state information... Done
Suggested packages:
  visualvm ttf-baekmuk ttf-unfonts ttf-unfonts-core ttf-kochi-gothic
  ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho ttf-arphic-uming
The following NEW packages will be installed:
  oracle-java7-installer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/17.6 kB of archives.
After this operation, 193 kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously unselected package oracle-java7-installer.
(Reading database ... 156848 files and directories currently installed.)
Unpacking oracle-java7-installer (from .../oracle-java7-installer_7u17-0~webupd8~2_all.deb) ...
oracle-license-v1-1 license has already been accepted
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Setting up oracle-java7-installer (7u17-0~webupd8~2) ...
Downloading Oracle Java 7...
--2013-04-03 23:43:49--  http://download.oracle.com/otn-pub/java/jdk/7u17-b02/jdk-7u17-linux-x64.tar.gz
Resolving download.oracle.com (download.oracle.com)... 195.215.37.46, 195.215.37.8
Connecting to download.oracle.com (download.oracle.com)|195.215.37.46|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u17-b02/jdk-7u17-linux-x64.tar.gz [following]
--2013-04-03 23:43:50--  https://edelivery.oracle.com/otn-pub/java/jdk/7u17-b02/jdk-7u17-linux-x64.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 23.50.214.140
Connecting to edelivery.oracle.com (edelivery.oracle.com)|23.50.214.140|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/otn-pub/java/jdk/7u17-b02/jdk-7u17-linux-x64.tar.gz?AuthParam=1365025551_52ef0391cc147a3603abdc2d4ca7bd6a [following]
--2013-04-03 23:43:51--  http://download.oracle.com/otn-pub/java/jdk/7u17-b02/jdk-7u17-linux-x64.tar.gz?AuthParam=1365025551_52ef0391cc147a3603abdc2d4ca7bd6a
Connecting to download.oracle.com (download.oracle.com)|195.215.37.46|:80... connected.
HTTP request sent, awaiting response... 200 OK


    The file is already fully retrieved; nothing to do.


Download done.
Removing outdated cached downloads...
sha256sum mismatch jdk-7u17-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

How can i solve it?

---

### Post by slickymaster on 2013-04-03
Run the following commands in a terminal window, one at a time:
```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
sudo apt-get update
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by SchrodingerCat on 2013-04-03
I get exactly the same error :(

---

### Post by slickymaster on 2013-04-03
Ok, let's try another approach.

This time just run the the commands that will purge your system from that bad installation. At the terminal run:
```
sudo rm /var/lib/dpkg/info/oracle-java7-installer*
sudo apt-get purge oracle-java7-installer*
sudo rm /etc/apt/sources.list.d/*java*
```

After that been done lets get Java JRE and JDK installed. Run one by one these commands at the terminal:
```
sudo mkdir -p /usr/local/java
wget -O jdk-64bit.tar.gz http://goo.gl/MSzBj
wget -O jre-64bit.tar.gz http://goo.gl/yZgjI
sudo -s cp -r jre-64bit.tar.gz /usr/local/java
sudo -s cp -r jdk-64bit.tar.gz /usr/local/java
cd /usr/local/java
sudo -s chmod a+x jre-64bit.tar.gz
sudo -s chmod a+x jdk-64bit.tar.gz
sudo -s tar xvzf jre-64bit.tar.gz
sudo -s tar xvzf jdk-64bit.tar.gz
```

After that, open** /etc/profile** with your installed text pad:
```
gksudo geany /etc/profile
```
and add the following lines at the end of file:
```
JAVA_HOME=/usr/local/java/jdk*
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
JRE_HOME=/usr/local/java/jre*
PATH=$PATH:$HOME/bin:$JRE_HOME/bin
export JAVA_HOME
export JRE_HOME
export PATH
```

Finally just run the following commands one by one in terminal:
```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jre1.7.0_12/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_12/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jre1.7.0_12/bin/javaws" 1
sudo update-alternatives --set java /usr/local/java/jre1.7.0_12/bin/java
sudo update-alternatives --set javac /usr/local/java/jdk1.7.0_12/bin/javac
sudo update-alternatives --set javaws /usr/local/java/jre1.7.0_12/bin/javaws
. /etc/profile
```

Edit: Let us know how it went.

---

### Post by SchrodingerCat on 2013-04-03
Well..everything went fine..i didn t get any errors..but i still don't have my java working..just one question...after all those lines should i try to install it again or should it be installed?

---

### Post by slickymaster on 2013-04-03
If you didn't get any errors, it's installed.

To be sure, run the following at terminal (This command displays the version of java running on your system):
```
java -version
```
You should receive a message which displays something similar to this (this is mine's):
[B]java version "1.7.0_17"
Java(TM) SE Runtime Environment (build 1.7.0_17-b21)
Java HotSpot(TM) 64-Bit Server VM (build 23.6-b04, mixed mode)[/B]

This command lets you know your java compiler installed:
```
javac -version
```
You should receive a message which displays:
**javac 1.7.0_17**

---

### Post by SchrodingerCat on 2013-04-03
Everything seems fine then...but..when i go on a website i am interested in it says..java(TM) is required to display this content..

---

### Post by slickymaster on 2013-04-03
Glad you got it working.

> **SchrodingerCat said:**
> Everything seems fine then...but..when i go on a website i am interested in it says..java(TM) is required to display this content..

That's a completely different issue. As we proved with my previous post, you do have java installed, what you don't have is java enabled in your browser. if you look at [Java website]("http://java.com/en/download/manual.jsp") you will notice next to the Linux distributions on the right it says: > "After installing Java, you will need to enable Java in your browser.".

---

### Post by SchrodingerCat on 2013-04-03
ah ok..i will start then a new Thread for enabling java cause the way i found on the we is not working. But your solution worked perfectly thank you very much!!

---

### Post by slickymaster on 2013-04-03
Glad to help you.

Don't forget to mark this thread as solved so other people searching the forums know that this thread provides a working solution for their problem.

See my signature on how to do it if you have doubts.

EDIT: My bad, you beat me to it.

---

