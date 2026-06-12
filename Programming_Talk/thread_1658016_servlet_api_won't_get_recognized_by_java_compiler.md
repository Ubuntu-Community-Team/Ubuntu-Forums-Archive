---
title: "servlet api won't get recognized by java compiler"
date: 2011-01-02
forum: Programming Talk
---

### Post by chessmonster on 2011-01-02
hi, I am stuck with this problem for a day now and still can't seem to find any answers.

i tried to study servlets and used a class extending the servlets class but the compiler is not recognizing the servlet keyword.

but the compiler alone is working with simple java classes, but servlets

here is what I did, i added classpath which holds the directory to my servlet-api.jar. typed these to my bash.bashrc files. and I have two of them

JAVA_HOME=/usr/lib/jvm/java-6-openjdk
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
CLASSPATH = /home/simon/Downloads/apache-tomcat-7.0.5/lib/servlet-api.jar
export CLASSPATH

and my tomcat directory is in my downloads folder

it did not worked.
servlet keywords still can't be seen

second thing i did was I added a classpath to my 'etc/environment' text file

now it looks like this
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin"
TOMCAT_HOME="/home/simon/Downloads/apache-tomcat-7.0.5"
JAVA_HOME="/usr/lib/jvm/java-6-openjdk"
CLASSPATH="$TOMCAT_HOME/lib/servlet-api.jar"

still can't get it to work. the compiler alone is working fine with simple classes, and also the tomcat alone ,i believe, is working fine too because i was able to pull up the index.jsp with the home page of tomcat but i can't seem to make them work together.


need some help please.. [-o<
any suggestions would be very appreciated ):P

---

### Post by chessmonster on 2011-01-02
tried to use apache tomcat 6 still won't work.

---

### Post by dileepm on 2011-01-27
In your '/etc/environment' file try this

> CLASSPATH=/home/simon/Downloads/apache-tomcat-7.0.5/lib/servlet-api.jar:.

No quotes for environment variables

---

