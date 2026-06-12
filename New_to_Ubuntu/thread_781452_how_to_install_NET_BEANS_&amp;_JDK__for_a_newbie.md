---
title: "how to install NET BEANS &amp; JDK  for a newbie"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by ashtn on 2008-05-04
can any1 tell me how to get netbeans working i keep getting an error like jdk is not installed and i have only jre on the system.this is ma third day into using ubuntu so please detailed instructions would be appreciated

---

### Post by Monicker on 2008-05-04
Have you read this?

[https://help.ubuntu.com/community/Netbeans]("https://help.ubuntu.com/community/Netbeans")

---

### Post by Biggy on 2008-05-04
Download [NetBeans IDE 6.1]("http://download.netbeans.org/netbeans/6.1/final/")

or Download [JDK 6u6 with NetBeans 6.1]("http://java.sun.com/javase/downloads/netbeans.html")

---

### Post by Maybe_Factor on 2008-05-04
make sure you have enabled all of the software sources in System > Administration > Software Sources then do these:

sudo apt-get install sun-java6-jdk
sudo apt-get install netbeans

Im also a bit of newb to linux but I believe that should install them both.....if not, open synaptic(near software sources) and find sun-java6-jdk and netbeans and install them from there

Hope that gets you set up,
Maybe_Factor

---

### Post by hebatgila on 2008-06-11
at last, i manage to install latest jdk6u6 and netbeans6.1 manually
_How to install JDK correctly in UBuntu_
1 Download the Latest JDK on sun website (make sure it's the file for linux or debian)

2 Put the jdk installer into your desktop

3 create a folder for JVM  at usr/lib/jvm (command : sudo mkdir /usr/lib/jvm)

4 Extract the installer on the desktop
	cd Desktop
	sudo chmod +x jdk*.bin
	sudo sh ./jdk*.bin

5 move the jdk folder to usr/lib/jvm
	ex: jdk folder on desktop is jdk1.6.0_06
		command : sudo mv jdk1.6.0_06 /usr/lib/jvm
		(note jdk1.6.0_06 must be at /usr/lib/jvm/jdk1.6.0_06)

6 if moving does not working you can use copy command then erase jdk on the desktop after copy completed
	command: sudo mkdir /usr/lib/jvm/jdk1.6.0_06
		 sudo cp -r jdk1.6.0_06 /usr/lib/jvm/jdk1.6.0_06
		 sudo rm -r jdk1.6.0_06

7 now , u should have ur jdk files on /usr/lib/jvm/jdk1.6.0_06

8 Updating to your latest JDK.
	command:
	sudo update-alternatives --install /usr/bin/javac javac /usr/lib/jvm/jdk1.6.0_06/bin/javac 30
	sudo update-alternatives --install /usr/bin/javac java /usr/lib/jvm/jdk1.6.0_06/bin/java 30
	sudo update-alternatives --config javac #then choose javac6 
	sudo update-alternatives --config java #choose java6 (please chose the  /usr/lib/jvm/jdk1.6.0_06/bin/java as default)

9 create java_home & classpath
	command : sudo gedit /etc/environment
		
	inside , please write like the sample below then save it
========================	   

PATH="/usr/lib/jvm/jdk1.6.0_06/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_AU.UTF-8"
LANGUAGE="en_AU:en"
JAVA_HOME="/usr/lib/jvm/jdk1.6.0_06/"
CLASSPATH="/usr/lib/jvm/jdk1.6.0_06/lib:." 
=========================	

10 update jvm
	command : sudo gedit /etc/jvm
	inside , please write like the sample below then save it
======================		
/usr/lib/jvm/jdk1.6.0_06/
=======================

11 check java version
	comand: java -version

12 done.

=======================================================================================================

if you follow the instruction above, you will have no problem installing latest netbean to ubuntu

1. download latest netbean6.1 for linux
2. put the installer into your desktop 
	command:
	cd Desktop (Make sure you are on Desktop directory)
	sudo chmod +x netbeans*.sh
	sudo sh ./netbeans*.sh
3 done

--------------------------------------------------------------------------------
at last, i managed to install my latest jdk and netbeans on my ubuntu desktop 08.4

---

