---
title: "Sun-Java-JDK Installation in Ubuntu 10.04 LTS problem"
date: 2012-04-09
forum: New to Ubuntu
---

### Post by xptional on 2012-04-09
I have installed a program VanetMobiSim-1.1 that I need for NS-2 simulation for vehicular traffic analysis. But it needs Sun JVM for better utilisation. [vanet.eurecom.fr]("vanet.eurecom.fr")
What I have in my system, is as follows,
Java Version, 
```
khan@khan:~$ java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)

```
Java Compiler output is as follows,
```
khan@khan:~$ javac -version
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>

```
Installing openjdk-6-jdk, the output is as follows,
```
khan@khan:~$ sudo apt-get install openjdk-6-jdk 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  openjdk-6-jdk: Depends: openjdk-6-jre (>= 6b18-1.8.3-0ubuntu1~8.04.2) but it is not going to be installed
E: Broken packages

```
I have download from [http://www.java.com]("http://www.java.com") a file for Linux but could not install it or may be it was corrupted. 
Then I took help from ubuntuforums as well searching different thread but could not arrive to solve my problem. 
Some information,
about sun-java6-jre
```
khan@khan:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```
and about sun-java6-bin
```
khan@khan:~$ sudo apt-get install sun-java6-bin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
```
About sun-java6-plugin
```
khan@khan:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-plugin is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-plugin has no installation candidate
```
About  sun-java6-jdk
```
khan@khan:~$ sudo apt-get install sun-java6-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate
```

I got help as well from [https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java") for **JDK** installation but i could not open the .bin file. And also help from [https://sites.google.com/site/easylinuxtipsproject/java]("https://sites.google.com/site/easylinuxtipsproject/java") but it only explains for **JRE** installation. 
I think jdk is much important to install by external resources, but don't know where to find it? 
How I could solve this problem ? 
Thanks for cooperation to solve it.

---

### Post by QIII on 2012-04-09
You can install the Sun JDK much as you installed the JRE as instructed in that tutorial.

Since you have already created your directory, simply download the JDK .bin from Oracle/Sun, move it to the directory already created (probably /opt/java/64), navigate to the directory, make the .bin executable, run the .bin.

You already have the Java plugin, so no need to go further.

Edit:  Just so you know, the Sun Java in the repositories is old and insecure.  There will be no updates because Oracle has withdrawn licensing for Java to be maintained in everyone's repositories.

Even though OpenJDK 7 is the reference implementation for Java 7, much of the world does not recognize OpenJDK.  That will change, at which point I will stop recommending the easy linux tips site and just say to install OpenJDK.

---

### Post by xptional on 2012-04-10
Thanks for your cooperation. 
What is in my system exist before downloading & installing,
```
root@khan:/opt/java/32# ls
jre1.6.0_31

```
And now after downloading from Oracle Sun site, I installed JRE 1.7 to be compatible with JDK 1.7 version. 
JDK 1.7 and JRE 1.7 version, 
```
root@khan:/opt/java/32# ls
jdk1.7.0_03                jre1.6.0_31  jre-7u3-linux-i586.tar.gz
jdk-7u3-linux-i586.tar.gz  jre1.7.0_03

```

Then I run the command for update to recent version of java, it was executed with out any problem, 
```
root@khan:/opt/java/32# sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.7.0_03//bin/java" 1
root@khan:/opt/java/32#

root@khan:/opt/java/32# sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jdk1.7.0_03/" 1
root@khan:/opt/java/32# 

```
Then I got the **ERROR** when I executed the below one,
```
root@khan:/opt/java/32# sudo update-alternatives --set java /opt/java/32/jre1.7.0_03/bin/java
update-alternatives: error: alternative /opt/java/32/jre1.7.0_03/bin/java for java not registered, not setting.
root@khan:/opt/java/32# sudo update-alternatives --set java /opt/java/32/jdk1.7.0_03/bin/java
update-alternatives: error: alternative /opt/java/32/jdk1.7.0_03/bin/java for java not registered, not setting.
root@khan:/opt/java/32#
```

Before
what exits in /usr/lib/jvm/ 
```
root@khan:/usr/lib/jvm# ls
java-1.5.0-gcj-4.4  java-6-sun  java-6-sun-1.6.0.24

```
After, 
I installed jdk1.7 version in /usr/lib/jvm/, So,
```
root@khan:/usr/lib/jvm# ls
java-1.5.0-gcj-4.4  java-6-sun-1.6.0.24  jdk-7u3-linux-i586.tar.gz
java-6-sun          jdk1.7.0_03

```

Please tell me should I need to remove the already existing file for java , in /opt/java/32/  File : jre1.6.0_31, 
and in  /usr/lib/jvm/ File: java-1.5.0-gcj-4.4 ,  java-6-sun-1.6.0.24 , java-6-sun , ..
Just for Information, 
java and javac version now, are same as before,
```
root@khan:/# java -version
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) Client VM (build 19.1-b02, mixed mode, sharing)
root@khan:/# javac -version
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: apt-get install <selected package>
root@khan:/# 

```
Please guide me what should I do next ? Thanks a lot !

---

### Post by xptional on 2012-04-10
Again What I did, I thought to configure it, and then updates, 
For configuation, I make choice 1 to select JDK1.7 version, ```
root@khan:/# sudo update-alternatives --config java
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                  Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-sun/jre/bin/java   63        auto mode
  1            /opt/java/32/jdk1.7.0_03/              1         manual mode
  2            /opt/java/32/jre1.7.0_03//bin/java     1         manual mode
* 3            /usr/lib/jvm/java-6-sun/jre/bin/java   63        manual mode

Press enter to keep the current choice[*], or type selection number: 1
update-alternatives: using /opt/java/32/jdk1.7.0_03/ to provide /usr/bin/java (java) in manual mode.

```
Then, 
I did, ```
root@khan:/# sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jdk1.7.0_03/bin/java" 1
root@khan:/#
```
What I got about JAVA version and JAVAC version,```
root@khan:/# java -version
bash: /usr/bin/java: is a directory
root@khan:/# javac -version
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: apt-get install <selected package>
root@khan:/# 
```

Now I am more worried, what I did , because of ```
root@khan:/# java -version
bash: /usr/bin/java: is a directory
root@khan:/#
```

---

### Post by xptional on 2012-04-11
Please could anybody respond to help me ? 
Im thankful to you ! :)

---

### Post by xptional on 2012-04-11
YES, it is solved, 
I removed all the directories from
```
sudo /usr/lib/jvm
```
and
```
sudo /opt/java/32
```
Then do update as well, 
```
sudo apt-get update
```
After that I download the 32 bit version " jdk-7u3-linux-i586.tar.gz", from [http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u3-download-1501626.html]("http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u3-download-1501626.html")
Then I put this .tar.gz file into /usr/lib/jvm/  and /opt/java/32/
I extracted it using the command, 
```
tar zxvf jdk-7u3-linux-i586.tar.gz
``` in both the directoried, and **the extracted directory should be renamed as "java-7-oracle"**
Then I took help from [http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html]("http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html")
Here it does not explain the work for the directory /opt/java/32/ but you should do that please. 
Then by using the following commands as per order, 
```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install update-java
sudo update-java

```
Here it will prompt to select the java version, please choice "/usr/lib/jvm/java-7-oracle"

Hope you will get success. 
For confirmation, do 
```
java -version

javac -version
```
Its all:)

---

