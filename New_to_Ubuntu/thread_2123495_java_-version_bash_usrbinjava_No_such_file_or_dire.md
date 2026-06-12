---
title: "java -version bash: /usr/bin/java: No such file or directory ?"
date: 2013-03-08
forum: New to Ubuntu
---

### Post by 007casper on 2013-03-08
java -version
bash: /usr/bin/java: No such file or directory 

???

I set my java.

sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0/bin/javaws" 1
sudo chmod a+x /usr/bin/java
sudo chmod a+x /usr/bin/javac
sudo chmod a+x /usr/bin/javaws
sudo update-alternatives --set java /usr/lib/jvm/jdk1.7.0/bin/java
sudo update-alternatives --set javac /usr/lib/jvm/jdk1.7.0/bin/javac
sudo update-alternatives --set javaws /usr/lib/jvm/jdk1.7.0/bin/javaws


I changed the path of exported java home on .bashrc... tried several ways.   

#sun
export JAVA_HOME=/usr/lib/jvm/jdk1.7.0/bin/java
#export JAVA_HOME=/usr/lib/jvm/jdk1.7.0
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH

echo $JAVA_HOME
/usr/lib/jvm/jdk1.7.0/bin/java

java -version
bash: /usr/bin/java: No such file or directory

???

how come I dont see java -version? Why doesnt it set?

---

### Post by 007casper on 2013-03-08
sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                            Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/jdk1.7.0/bin/java                   1         manual mode

still
java -version
bash: /usr/bin/java: No such file or directory


locate bin/java
/usr/bin/java
/usr/bin/javaws
/usr/lib/jvm/java-6-openjdk-amd64/bin/java
/usr/lib/jvm/java-6-openjdk-amd64/bin/java-rmi.cgi
/usr/lib/jvm/java-6-openjdk-amd64/bin/javaws
/usr/lib/jvm/java-6-openjdk-amd64/jre/bin/java
/usr/lib/jvm/java-6-openjdk-amd64/jre/bin/javaws
/usr/lib/jvm/java-7-openjdk-amd64/bin/javaws
/usr/lib/jvm/java-7-openjdk-amd64/jre/bin/javaws
/usr/lib/ure/bin/javaldx

I dont see jdk1.7.0

cd /usr/lib/jvm/jdk1.7.0/bin/java

it does exist

???

---

### Post by schragge on 2013-03-08
Please post the output of ```
namei -l /usr/bin/java [COLOR=blue]# <- It's small letter L[/COLOR]
```

---

### Post by 007casper on 2013-03-08
namei -l /usr/bin/java

f: /usr/bin/java
drwxr-xr-x root  root  /
drwxr-xr-x root  root  usr
drwxr-xr-x root  root  bin
lrwxrwxrwx root  root  java -> /etc/alternatives/java
drwxr-xr-x root  root    /
drwxr-xr-x root  root    etc
drwxr-xr-x root  root    alternatives
lrwxrwxrwx root  root    java -> /usr/lib/jvm/jdk1.7.0/bin/java
drwxr-xr-x root  root      /
drwxr-xr-x root  root      usr
drwxr-xr-x root  root      lib
drwxr-xr-x root  root      jvm
drwxr-xr-x puter puter     jdk1.7.0
drwxr-xr-x puter puter     bin
-rwxr-xr-x puter puter     java



root@cookie:/usr/lib/jvm# chown -R root:root jdk1.7.0*

under root@cookie
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.7.0/bin/java" 1
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/lib/jvm/jdk1.7.0/bin/javac" 1
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/lib/jvm/jdk1.7.0/bin/javaws" 1
sudo chmod a+x /usr/bin/java
sudo chmod a+x /usr/bin/javac
sudo chmod a+x /usr/bin/javaws
sudo update-alternatives --set java /usr/lib/jvm/jdk1.7.0/bin/java
sudo update-alternatives --set javac /usr/lib/jvm/jdk1.7.0/bin/javac
sudo update-alternatives --set javaws /usr/lib/jvm/jdk1.7.0/bin/javaws

java -version
bash: /usr/bin/java: No such file or directory

javac -version
bash: /usr/bin/javac: No such file or directory


namei -l /usr/bin/java
f: /usr/bin/java
drwxr-xr-x root root /
drwxr-xr-x root root usr
drwxr-xr-x root root bin
lrwxrwxrwx root root java -> /etc/alternatives/java
drwxr-xr-x root root   /
drwxr-xr-x root root   etc
drwxr-xr-x root root   alternatives
lrwxrwxrwx root root   java -> /usr/lib/jvm/jdk1.7.0/bin/java
drwxr-xr-x root root     /
drwxr-xr-x root root     usr
drwxr-xr-x root root     lib
drwxr-xr-x root root     jvm
drwxr-xr-x root root     jdk1.7.0
drwxr-xr-x root root     bin
-rwxr-xr-x root root     java

on /home/puter/.bashrc
#sun
#export JAVA_HOME=/usr/lib/jvm/jdk1.7.0/bin/java
export JAVA_HOME=/usr/lib/jvm/jdk1.7.0
PATH=$PATH:$HOME/bin:$JAVA_HOME/bin
export JAVA_HOME
export PATH


still the same problem
java -version
bash: /usr/bin/java: No such file or directory

javac -version
bash: /usr/bin/javac: No such file or directory

---

### Post by 007casper on 2013-03-08
on my other server I did the same set up and it worked.  However, on that server I have user_id and group_id 500 

500 got picked up automatically.

???

---

### Post by schragge on 2013-03-08
FYI, default UID/GID=500 for the first created user are on RedHat-based systems, on Debian-based it's 1000. But that's irrelevant here as java executable is now owned by root.

Try to call java by the full path ```
/usr/lib/jvm/jdk1.7.0/bin/java -version
```

---

### Post by 007casper on 2013-03-08
/usr/lib/jvm/jdk1.7.0/bin/java -version
bash: /usr/lib/jvm/jdk1.7.0/bin/java: No such file or directory

---

### Post by schragge on 2013-03-08
Then try ```
/usr/bin/env PATH=/bin:/usr/bin sh -c 'java -version'
```

---

### Post by 007casper on 2013-03-08
/usr/bin/env PATH=/bin:/usr/bin sh -c 'java -version'
sh: 1: java: not found

---

### Post by steeldriver on 2013-03-08
are you sure the binary you selected is the correct architecture for your machine (32 bit versus 64 bit)?

---

### Post by 007casper on 2013-03-08
ohhh! I think you are right.  The jdk I used on the server was 32 bit.  This computer 64 bit.  That must be it.  I am going to check and give status.

---

### Post by 007casper on 2013-03-08
it doesnt work.  

ln -s /usr/lib/jvm/jdk1.7.0_17/bin/java -> /etc/alternatives/java
bash: /etc/alternatives/java: No such file or directory

cd /etc/alternatives

java is there but in red color

at /usr/lib/jvm Java is in red color, and the rest are in light blue... the other files in the same directory is green

lrwxrwxrwx  1 root   root          22 Oct 19 07:45 java -> /etc/alternatives/java
lrwxrwxrwx  1 root   root          23 Mar  6 14:03 javac -> /etc/alternatives/javac
lrwxrwxrwx  1 root   root          24 Oct 19 07:45 javaws -> /etc/alternatives/javaws
lrwxrwxrwx  1 root   root          23 Oct 19 07:45 jexec -> /etc/alternatives/jexec

I dont know what red color means on the terminal
???

---

### Post by 007casper on 2013-03-08
sudo update-alternatives --config java
update-alternatives: warning: /etc/alternatives/java is dangling, it will be updated with best choice.
There is only one alternative in link group java: /usr/lib/jvm/jdk1.7.0/bin/java
Nothing to configure.

---

### Post by 007casper on 2013-03-08
fix the situation. Now it works.

It was the wrong version of jdk and the links werent updating.

I update it to right jdk version 64 bit, and remove the links and relink it.

java -version
java version "1.7.0_17"
Java(TM) SE Runtime Environment (build 1.7.0_17-b02)
Java HotSpot(TM) 64-Bit Server VM (build 23.7-b01, mixed mode)

thank you all

---

### Post by schragge on 2013-03-09
*Answering PM, as it may be of interest to others even if off-topic*.
> **007casper][quote=schragge said:**
> FYI, default UID/GID=500 for the first created user are on RedHat-based  systems, on Debian-based it's 1000.I am using ubuntu 12.04 not redhat on the server.  I am  just curious why it would set to 500.[/QUOTE]Hmm, interesting. On my  system (Debian wheezy) both adduser and useradd use 1000 by default:
```

[COLOR=green]$[/COLOR] grep ^FIRST_.ID /etc/adduser.conf
[COLOR=green]FIRST_UID=1000
FIRST_GID=1000[/COLOR]
[COLOR=green]$[/COLOR] grep ^.ID_MIN /etc/{login.defs,default/useradd}
[COLOR=green]/etc/login.defs:UID_MIN                  1000
/etc/login.defs:GID_MIN                  1000[/COLOR]

```These  are the  default values for regular user accounts if you don't specify UID/GID  explicitly. Perhaps, you created a system account instead?

---

