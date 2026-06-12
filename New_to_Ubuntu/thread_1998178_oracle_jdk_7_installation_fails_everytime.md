---
title: "oracle jdk 7 installation fails everytime"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by stonecoldjha on 2012-06-06
i am trying to install oracle jdk 7 on ubuntu 12.04. But the instalation failed with the folowing:
E: Sub-process /usr/bin/dpkg returned an error code (1)


i followed the instructions here 
[http://ubuntuforums.org/showthread.php?t=1956559&page=2]("http://ubuntuforums.org/showthread.php?t=1956559&page=2")

But, it fails with the same error message. What do i do?

---

### Post by Curtis6767 on 2012-06-06
Look over both of the following sites first before doing anything. These instructions worked for me but they did not work for another person who tried them a few days ago. Hopefully they will work for you.

1.) [https://launchpad.net/~webupd8team/+archive/java](https://launchpad.net/~webupd8team/+archive/java)

2.) [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

Easy way to install PPA: [http://www.wmlcloud.com/linux/how-to-add-ppa-to-software-sources-in-ubuntu-linux-from-ubuntu-software-center/](http://www.wmlcloud.com/linux/how-to-add-ppa-to-software-sources-in-ubuntu-linux-from-ubuntu-software-center/)

Hope this helps.

---

### Post by d4m1r on 2012-06-06
You are using sudo during the install correct? That message tends to be related to permissions issue as far as I remember....

---

### Post by stonecoldjha on 2012-06-14
i followed the instructions given on the second website:
[http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

it still fails:

sonu@sonu-Vostro-1550:~$ sudo apt-get install oracle-java7-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  binfmt-support visualvm ttf-baekmuk ttf-unfonts ttf-unfonts-core
  ttf-kochi-gothic ttf-sazanami-gothic ttf-kochi-mincho ttf-sazanami-mincho
  ttf-arphic-uming
The following packages will be upgraded:
  oracle-java7-installer
1 upgraded, 0 newly installed, 0 to remove and 50 not upgraded.
1 not fully installed or removed.
Need to get 14.9 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Get:1 [http://ppa.launchpad.net/webupd8team/java/ubuntu/](http://ppa.launchpad.net/webupd8team/java/ubuntu/) precise/main oracle-java7-installer all 7u5-0~webupd8~3 [14.9 kB]
Fetched 14.9 kB in 1s (14.2 kB/s)               
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-06-14 19:24:53--  [http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving download.oracle.com (download.oracle.com)... 58.26.1.35, 58.26.1.64
Connecting to download.oracle.com (download.oracle.com)|58.26.1.35|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz) [following]
--2012-06-14 19:24:54--  [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-x64.tar.gz)
Resolving edelivery.oracle.com (edelivery.oracle.com)... 173.222.154.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|173.222.154.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html) [following]
--2012-06-14 19:24:57--  [http://download.oracle.com/errors/download-fail-1505220.html](http://download.oracle.com/errors/download-fail-1505220.html)
Connecting to download.oracle.com (download.oracle.com)|58.26.1.35|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-x64.tar.gz'

     0K .....                                                 100%  753K=0.007s

2012-06-14 19:24:57 (753 KB/s) - `./jdk-7u3-linux-x64.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-x64.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 oracle-java7-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)
sonu@sonu-Vostro-1550:~$

---

### Post by Cheesemill on 2012-06-14
It looks like a problem with the Oracle website, the jdk-7u3-linux-x64.tar.gz file that the script downloads is around 80MB whereas your machine is only downloading a 753KB file (this is why the hash doesn't match, you don't have the correct file).

I would leave it a while and try later when the website is fixed, the WebUpd8 team PPA has always worked fine for me to install Java.

---

