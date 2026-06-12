---
title: "sslvpn connection problem"
date: 2012-07-30
forum: New to Ubuntu
---

### Post by bekirs on 2012-07-30
[FONT=Arial][SIZE=2]Hi,

I'm an absolute beginner and have Xubuntu 12.04 installed on my [/SIZE][/FONT][FONT=Arial][SIZE=2]HP 635 (A1E51EA)[/SIZE][/FONT][FONT=Arial][SIZE=2] Laptop.

I want to connect to my work data from home via _**sslvpn**_ but after I log in, I get the following error message:

[/SIZE][/FONT][B]JRE not installed/Java is disabled.

[/B]Do you have any solution for that?

Thanks in advance,

---

### Post by levlaz on 2012-07-30
> **bekirs said:**
> [FONT=Arial][SIZE=2]Hi,

I'm an absolute beginner and have Xubuntu 12.04 installed on my [/SIZE][/FONT][FONT=Arial][SIZE=2]HP 635 (A1E51EA)[/SIZE][/FONT][FONT=Arial][SIZE=2] Laptop.

I want to connect to my work data from home via _**sslvpn**_ but after I log in, I get the following error message:

[/SIZE][/FONT][B]JRE not installed/Java is disabled.

[/B]Do you have any solution for that?

Thanks in advance,

Does your company use the Juniper Networking client? If so I had the same issue when connecting to the school network. 

First thing you want to do is install Java 7, I had trouble getting this to work with OpenJDK so go ahead and install the Oracle version of Java. You can see[ instructions here. ]("http://www.duinsoft.nl/packages.php?t=en")

Are you running 32 bit Ubuntu ?? I had a lot of trouble getting this to work in 64 bit even with the 32bit libraries installed. 

If you are running 32 bit ... then after you install java restart firefox and you should be able to connect after that. 

Best, 

Lev

---

### Post by bekirs on 2012-07-30
Yes,we are using Juniper Networking Client and my computer is 64-bit.
I was not successful to install with the methods described in your [link]("http://www.duinsoft.nl/packages.php?t=en").
I first tried installation from repository but I couldn't reach to the following address:

 /etc/apt/sources.list

Then, I tried the manual installation and this is what I got:

sh update-sun-jre.bin
sh: 0: Can't open update-sun-jre.bin

---

### Post by levlaz on 2012-07-30
> **bekirs said:**
> Yes,we are using Juniper Networking Client and my computer is 64-bit.
I was not successful to install with the methods described in your [link]("http://www.duinsoft.nl/packages.php?t=en").
I first tried installation from repository but I couldn't reach to the following address:

 /etc/apt/sources.list

Then, I tried the manual installation and this is what I got:

sh update-sun-jre.bin
sh: 0: Can't open update-sun-jre.bin


The problem is that this method in the link will not install 32 bit java, it will install the version that is suited for your computer. 

I would download Java Directly from oracle and run the installation script. 

1. Download the following file -- [32 Bit Java 7 JRE ]("http://download.oracle.com/otn-pub/java/jdk/7u5-b06/jre-7u5-linux-i586.tar.gz")from the official Oracle site. 

2. Follow the instructions on[ this website]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux") for command line install. (Look on the right column).. .this should work for you. 

If everything goes through alright you will see the Java Plugin in Firefox if you go to tools --> addons --> plugins. Afterwards you can navigate to the VPN site and the Juniper app will launch automatically. 

Also for future reference ... /etc/apt/sources.list is nothing more than a text file with collection of repos from which you can install various software. In order to access and edit this list all you have to do is open a terminal, and then type ... sudo gedit /etc/apt/sources.list 

-- You use sudo because you must be root to access this file. 
-- gedit is a text editor on Ubuntu 


Best, 

Lev

---

### Post by bekirs on 2012-08-02
> **levlaz said:**
> The problem is that this method in the link will not install 32 bit java, it will install the version that is suited for your computer. 

I would download Java Directly from oracle and run the installation script. 

1. Download the following file -- [32 Bit Java 7 JRE ]("http://download.oracle.com/otn-pub/java/jdk/7u5-b06/jre-7u5-linux-i586.tar.gz")from the official Oracle site. 

2. Follow the instructions on[ this website]("http://www.wikihow.com/Install-Oracle-Java-on-Ubuntu-Linux") for command line install. (Look on the right column).. .this should work for you. 

If everything goes through alright you will see the Java Plugin in Firefox if you go to tools --> addons --> plugins. Afterwards you can navigate to the VPN site and the Juniper app will launch automatically. 


I followed the instructions  of the webpage you suggested. In the 1st step, I get the following:
```
/sbin/init: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0x029d6e45c81ad4eee2627f676b7580c9ed5fde47, stripped

```At the 2nd step:
```
java -version
The program 'java' can be found in the following packages:
 * default-jre
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>

```and 3rd step:
```
sudo apt-get purge openjdk-\* 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'openjdk-7-dbg' for regex 'openjdk-*'
Note, selecting 'openjdk7-jdk' for regex 'openjdk-*'
Note, selecting 'openjdk-7-doc' for regex 'openjdk-*'
Note, selecting 'openjdk-jre' for regex 'openjdk-*'
Note, selecting 'openjdk-6-demo' for regex 'openjdk-*'
Note, selecting 'openjdk-7-jdk' for regex 'openjdk-*'
Note, selecting 'openjdk-7-jre' for regex 'openjdk-*'
Note, selecting 'uwsgi-plugin-jvm-openjdk-6' for regex 'openjdk-*'
Note, selecting 'openjdk-6-source' for regex 'openjdk-*'
Note, selecting 'openjdk-6-jre-lib' for regex 'openjdk-*'
Note, selecting 'uwsgi-plugin-jwsgi-openjdk-6' for regex 'openjdk-*'
Note, selecting 'openjdk-6-jre-headless' for regex 'openjdk-*'
Note, selecting 'openjdk-7-jre-zero' for regex 'openjdk-*'
Note, selecting 'openjdk-7-source' for regex 'openjdk-*'
Note, selecting 'openjdk-7-demo' for regex 'openjdk-*'
Note, selecting 'openjdk-6-jre-zero' for regex 'openjdk-*'
Note, selecting 'openjdk-7-jre-lib' for regex 'openjdk-*'
Note, selecting 'openjdk-6-dbg' for regex 'openjdk-*'
Note, selecting 'openjdk-6-doc' for regex 'openjdk-*'
Note, selecting 'openjdk-6-jdk' for regex 'openjdk-*'
Note, selecting 'openjdk-6-jre' for regex 'openjdk-*'
Note, selecting 'openjdk-7-jre-headless' for regex 'openjdk-*'
Package openjdk-6-dbg is not installed, so not removed
Package openjdk-6-demo is not installed, so not removed
Package openjdk-6-doc is not installed, so not removed
Package openjdk-6-jdk is not installed, so not removed
Package openjdk-6-jre is not installed, so not removed
Package openjdk-6-jre-headless is not installed, so not removed
Package openjdk-6-jre-lib is not installed, so not removed
Package openjdk-6-source is not installed, so not removed
Package openjdk-6-jre-zero is not installed, so not removed
Package openjdk-7-dbg is not installed, so not removed
Package openjdk-7-demo is not installed, so not removed
Package openjdk-7-doc is not installed, so not removed
Package openjdk-7-jdk is not installed, so not removed
Package openjdk-7-jre is not installed, so not removed
Package openjdk-7-jre-headless is not installed, so not removed
Package openjdk-7-jre-lib is not installed, so not removed
Package openjdk-7-jre-zero is not installed, so not removed
Package openjdk-7-source is not installed, so not removed
Package uwsgi-plugin-jvm-openjdk-6 is not installed, so not removed
Package uwsgi-plugin-jwsgi-openjdk-6 is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```I wanted to continue by downloading but I'm not sure whether **Linux x86** or **Linux x64** is the appropriate one for my system???

---

### Post by levlaz on 2012-08-05
Since we are trying to install a 32 bit version you want to select the x86 ... the x64 is the 64 bit version. 

The "appropriate" version for your computer ***is ***the 64 bit version, however from my own experience I have been unable to make the Juniper client work in 64 bit java because it relies on 32 bit libraries.

---

### Post by bekirs on 2012-08-06
> **levlaz said:**
> Since we are trying to install a 32 bit version you want to select the x86 ... the x64 is the 64 bit version. 

The "appropriate" version for your computer ***is ***the 64 bit version, however from my own experience I have been unable to make the Juniper client work in 64 bit java because it relies on 32 bit libraries.

Hi, I just tried to install x64 and I think it worked. I don't get the following anymore:
[B]JRE not installed/Java is disabled.

[/B]and this is what I get after typing Java version command:```
java -version
java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b06)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)

```However, it is not working as it does in Windows. For example, there are some websites to which I have only access if I establish the **sslvpn** connection to my institute. I reach them when I establish my **sslvpn** from **Windows** but not from **xubuntu**...

Could it be related with the 32- / 64- bit conflict you've mentioned?

---

### Post by bekirs on 2012-08-09
> **bekirs said:**
> Hi, I just tried to install x64 and I think it worked. I don't get the following anymore:
[B]JRE not installed/Java is disabled.

[/B]and this is what I get after typing Java version command:```
java -version
java version "1.7.0_05"
Java(TM) SE Runtime Environment (build 1.7.0_05-b06)
Java HotSpot(TM) 64-Bit Server VM (build 23.1-b03, mixed mode)

```However, it is not working as it does in Windows. For example, there are some websites to which I have only access if I establish the **sslvpn** connection to my institute. I reach them when I establish my **sslvpn** from **Windows** but not from **xubuntu**...

Could it be related with the 32- / 64- bit conflict you've mentioned?
Hi,
I want to report the final status... When 64-bit Java is installed, VPN connection doesn't work with Mozilla. With 32-bit installation, it's fine...
Thanks for the help...

---

