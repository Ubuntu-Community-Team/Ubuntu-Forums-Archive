---
title: "run jar file - double-click"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by ALTN on 2012-04-14
Hello,

I'm new to Ubunto i recently installed ubuntu 12.04 beta 2, and my main goal for that is to use it for java development.

I followed [this]("http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7") guide to install jdk7-u3.

The java command line is working properly, i tried it for running a jar file and it worked fine but i would like to execute it by a simple double click just as i used to do under windows.

I googled before posting, and this is what i found:
- use "sudo chmod +x jarfile.jar"
- right-click/properties/open with/sun java x
now the problem is that there's no "sun java x" under the "open with" tab, even after i press the  "show other applications" button.

Is there any way to run a jar file by double-clicking it in ubuntu?

Thanks in advance

---

### Post by raja.genupula on 2012-04-14
[http://superuser.com/questions/78989/configure-ubuntu-to-run-jar-file-by-double-clicking-on-it](http://superuser.com/questions/78989/configure-ubuntu-to-run-jar-file-by-double-clicking-on-it)

---

### Post by woxuxow on 2012-04-14
If you want to use open-jdk to open jar files you should choose the open jdk runtime for default application not sun java

---

### Post by ALTN on 2012-04-14
[@raja.genupula:]("http://ubuntuforums.org/member.php?u=1184528") as i already mentioned i can't find any thing related to java (openjdk, sun java, oracle java ..) under open with, and even when i type java in the search field under dash home, i can't find it neither. However when executing java -version it works fine.

@MustafaJF: i think i followed the wrong guide to install the jdk. It consists of : download the jdk7 pack from the java website- extract it- move it to /usr/lib/jvm/jdk1.7.3- then execute some comands (here's the [COLOR=Cyan]_[link]("http://askubuntu.com/questions/55848/how-do-i-install-oracle-java-jdk-7")_[/COLOR])

I've just found this new [guide]("http://ubuntuguide.net/install-oracle-javajdk-7-in-ubuntu-12-04-precise-11-10-oneiric") and i would like to follow it, but just before i do, how can i remove the installed jdk?

Thank you for the help!
[]("http://ubuntuforums.org/member.php?u=1184528")

---

### Post by ALTN on 2012-04-15
i formatted ubunto partitions and re-installed it in order to install a new clean copy of java following [COLOR=Blue]_[this guide]("http://ubuntuguide.net/install-oracle-javajdk-7-in-ubuntu-12-04-precise-11-10-oneiric")_[/COLOR], but again having troubles :\.

so this is what i typed in the terminal:
```
sudo add-apt-repository ppa:eugenesan/java 
sudo apt-get update 
sudo apt-get install oracle-java7-installer
```and here's the output:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
oracle-java7-installer is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 571 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up oracle-java7-installer (7u3-0~eugenesan~precise4) ...
Downloading...
--2012-04-15 12:14:12--  http://download.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving download.oracle.com (download.oracle.com)... 77.67.21.19, 77.67.21.18
Connecting to download.oracle.com (download.oracle.com)|77.67.21.19|:80... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz [following]
--2012-04-15 12:14:12--  https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz
Resolving edelivery.oracle.com (edelivery.oracle.com)... 2.18.222.174
Connecting to edelivery.oracle.com (edelivery.oracle.com)|2.18.222.174|:443... connected.
HTTP request sent, awaiting response... 302 Moved Temporarily
Location: http://download.oracle.com/errors/download-fail-1505220.html [following]
--2012-04-15 12:14:13--  http://download.oracle.com/errors/download-fail-1505220.html
Connecting to download.oracle.com (download.oracle.com)|77.67.21.19|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5307 (5.2K) [text/html]
Saving to: `./jdk-7u3-linux-i586.tar.gz'

     0K .....                                                 100% 99.6K=0.05s

2012-04-15 12:14:13 (99.6 KB/s) - `./jdk-7u3-linux-i586.tar.gz' saved [5307/5307]

Download done.
sha256sum mismatch jdk-7u3-linux-i586.tar.gz
Oracle JDK 7 is NOT installed.
dpkg: error processing oracle-java7-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing: oracle-java7-installer
```A dialog pops-up asking me for reporting the problem, i accept and it tells me that this is a non official ubuntu release, which is correct since i'm using a beta release; does this mean i won't be able to install java properly under ubuntu 12.04 beta2 ?? or is it just a problem with the repository?.


NB: i tried openSUSE before ubuntu but it doesn't work on my computer ASUS N55SF which has issues  with linux; i did researches over the internet and found out that till now the only release that solved these issues is ubuntu 12.04 beta2, but with no java i just have nothing to do with it.

---

### Post by ALTN on 2012-04-15
it seems that oracle website is denying the access, i copied this link [https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz](https://edelivery.oracle.com/otn-pub/java/jdk/7u3-b04/jdk-7u3-linux-i586.tar.gz) from the shell output and tried to open in my web browser and what i get is Unauthorized Request.

I already have the jdk-7u3-linux-i586.tar.gz pack in my hard drive, is there any way to tell the command line to use the local pack instead of downloading it from oracle server?

---

### Post by ALTN on 2012-04-15
no more time to waist, bye bye ubuntu

---

### Post by stinkeye on 2012-04-15
"He that can have patience can have what he will."
BENJAMIN FRANKLIN

Bye ):P

"Better to waste your time than mine."
STINKEYE

---

### Post by ALTN on 2012-04-15
hhhh ):P

---

### Post by woxuxow on 2012-04-16
I use openJDK 6 and i have no problem with that version (my ubuntu version is 11.10)
i think i installed it from medibuntu repository 
for installing application usually you should copy your package (extracted package in a directory) into the /usr/share/
then create a symbolic or hard link from the executable file into the /usr/sbin or /usr/bin (it depends on -------)
furthermore copy all necessary library into the /usr/lib or into the any lib directory that mentioned in the readme

don't forget ubuntu is one of the easiest distro

---

