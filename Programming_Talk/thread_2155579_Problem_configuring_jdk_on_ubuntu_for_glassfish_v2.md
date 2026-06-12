---
title: "Problem configuring jdk on ubuntu for glassfish v2.1 install"
date: 2013-06-18
forum: Programming Talk
---

### Post by zeckis on 2013-06-18
hi, 
am french but i will try to explain in english my problem.
I get a server online, and i had try to install jdk1.7.0.21, before i download it from official website of oracle.
After uncompressing, et move on /usr/lib/jvm.
Now i edit /etc/environnement: 
**PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"**
**JAVA_HOME=/usr/lib/jvm/jdk1.7.0_21**

and /etc/profile:
**JAVA_HOME=/usr/lib/jvm/jdk1.7.0_21**
**JDK_HOME=/usr/lib/jvm/jdk1.7.0_21**
**PATH=$PATH:$HOME/bin:$JAVA_HOME/bin**
**export JAVA_HOME**
**export PATH**
**export JDK_HOME**

When i check with : java -version, this is the result:
**java version "1.7.0_21"**
**Java(TM) SE Runtime Environment (build 1.7.0_21-b11)**
**Java HotSpot(TM) 64-Bit Server VM (build 23.21-b01, mixed mode)**

and too:
**root@xxxxx:~# echo $JAVA_HOME**
**/usr/lib/jvm/jdk1.7.0_21**
**root@xxxxxx:~# echo $PATH**
**/usr/lib/jvm/jdk1.7.0_21/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/lib/jvm/java-7-oracle/:/usr/lib/jvm/java-7-oracle/jre:/root/bin:/usr/lib/jvm/jdk1.7.0_21/bin:/root/bin:/usr/lib/jvm/jdk1.7.0_21/bin:/root/bin:/usr/lib/jvm/jdk1.7.0_21/bin**

so after all theses configuration i cant install glassfish , it cant see the jdk, only because it not good configured.
**root@xxxxxx:/opt/glassfish# lib/ant/bin/ant -f setup.xml**
**Buildfile: setup.xml**

**get.java.home:**

**setup.init:**

**tools.init.windows:**

**tools.init.solaris:**

**tools.init.solaris-sparc:**

**tools.init.solaris-x86:**

**tools.init.linux:**

**tools.init.darwin:**

**check-osforbuildjarinstaller:**

**check-installer-compatibility:**

**installer-message:**

**all:**

**get.java.home:**

**setup.init:**

**check-java:**

**get.java.home:**

**setup.init:**

**validate-java:**
**     [echo] Current Java Version 1.7.0_21**

**BUILD FAILED**
**/opt/glassfish/setup.xml:161: The following error occurred while executing this line:**
**/opt/glassfish/setup.xml:151: Glassfish requires JDK 1.5 or higher, you have java version "1.7.0_21"**
**Java(TM) SE Runtime Environment (build 1.7.0_21-b11)**
**Java HotSpot(TM) 64-Bit Server VM (build 23.21-b01, mixed mode)**


How or what to do? How to solve my problem?
thanks

---

### Post by sum1nil on 2013-06-19
I don't currently have the JDK installed but consider this a shot in the dark. Please make sure you have the JDK and not just the JRE.
I also have nothing but the variable PATH in '/etc/environment'. 
>  **/etc/profile:**
JAVA_HOME=/usr/lib/jvm/jdk1.7.0_21
JDK_HOME=/usr/lib/jvm/jdk1.7.0_21
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH
export JDK_HOME

It would seem that your Java exports should all be before you export your PATH variable. Also JAVA_HOME and JDK_HOME seem to point to the same directory. I believe the JRE is a folder inside of the JDK.
Try:
[B]
JDK_HOME=/path/to/jdk1.7.0_21
export JDK_HOME
JAVA_HOME=/path/to/jdk1.7.0_21/jre
export JAVA_HOME
PATH=*$JAVA_HOME/bin:$JDK_HOME/bin*:$PATH [ I usually put the Java stuff first to prevent overrides by package installs ]
export PATH
[/B]

I also put these types of things at the end of ~/.bashrc. I do not know what the common opinion is on .profile vs .bashrc but I've been using .bashrc since my first version of linux (Mandrake).

Logout and then login to reset the environment variables. 

I know it's not much; hope it helps.

---

### Post by zeckis on 2013-06-20
thanks for your reply, 

But, unfortunately, i always cant install my glassfish. I have the same error problem on JDK

---

