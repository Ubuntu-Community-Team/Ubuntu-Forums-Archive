---
title: "How to install JAVA 7u21 offline? [Ubunutu 12.04] 32BIT"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by violetkiwi on 2013-05-31
i want to use java 7u21 for android strudio,

would you help me to install java 7 u21 (32 BIT) TAR package downloaded from ORACLE Website.

---

### Post by slickymaster on 2013-05-31
I'm assuming you've already downloaded both tars, JDK and JRE. So, here's what you have to do:
First create a directory to hold your Java JDK and JRE binaries:```
sudo mkdir -p /usr/local/java
```Then, copy the Java binaries into the** /usr/local/java** directory:```
cd folder_where_your_tars_are_located
sudo cp -r jdk-7u21-linux-i586.tar.gz /usr/local/java
sudo cp -r jre-7u21-linux-i586.tar.gz /usr/local/java
cd /usr/local/java
```Unpack the compressed Java binaries, in the directory **/usr/local/java**:```
sudo tar xvzf jdk-7u21-linux-i586.tar.gz
sudo tar xvzf jre-7u21-linux-i586.tar.gz
```Edit the system PATH file** /etc/profile** and add the following system variables to your system path. Use nano, geany, gedit or any other text editor, as root:```
sudo geany /etc/profile
```and add the following lines below to the end of your **/etc/profile** file:```
JAVA_HOME=/usr/local/java/jdk1.7.0_21
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
JRE_HOME=/usr/local/java/jre1.7.0_21
PATH=$PATH:$HOME/bin:$JRE_HOME/bin
export JAVA_HOME
export JRE_HOME
export PATH
```Save the /etc/profile file and exit.
After that, notify your Ubuntu system where your Java JDK/JRE are located:```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jre1.7.0_21/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.7.0_21/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jre1.7.0_21/bin/javaws" 1
```and  that Java JDK/JRE must be the default Java:```
sudo update-alternatives --set java /usr/local/java/jre1.7.0_21/bin/java
sudo update-alternatives --set javac /usr/local/java/jdk1.7.0_21/bin/javac
sudo update-alternatives --set javaws /usr/local/java/jre1.7.0_21/bin/javaws
```Finally, reload your system wide PATH /etc/profile by typing the following command:```
. /etc/profile
```

---

### Post by violetkiwi on 2013-05-31
if you see below error when  you launch android studio , RESTART THE COMPUTER

"tool.jar is not in Android Studio classpath. Please ensure JAVA_HOME points to JDK rather than JRE"

---

### Post by violetkiwi on 2013-05-31
Restarting system solved the issue.

---

### Post by violetkiwi on 2013-05-31
Thankyou slickyMaster for detailed steps for installation.

---

