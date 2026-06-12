---
title: "tomcat -- setting environment variables"
date: 2008-09-28
forum: Programming Talk
---

### Post by badperson on 2008-09-28
Hi,

I've been looking through some online info as to setting up tomcat, 

I set the JAVA_HOME variable in my bashrc file as 
/usr/lib

that is the directory where the java and javac executables are located. 


I get this on the console when checking the java_home variable

```
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ echo $JAVA_HOME
/usr/bin

```

most of the tutorials I've seen have the directory as something like
/usr/lib/java-sdk[someversion-number]

when I try to startup tomcat I get this:
```
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ sudo sh startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program

```

thanks, 
bp

---

### Post by jespdj on 2008-09-28
Why did you set JAVA_HOME to /usr/lib (or is is /usr/bin, as the output as "echo $JAVA_HOME" shows)?
You need to set it to the directory where your Java runtime environment is installed, for example **/usr/lib/jvm/java-6-sun-1.6.0.06**

Setting it to /usr/lib or /usr/bin is wrong.

---

### Post by badperson on 2008-09-28
Hi,

thanks. I set the variable there because that's where the javac and java exectuables were...that was similar to how I had done it on windows machines, my mistake. 

anyway, I tried setting the variable in a few places, 
 here's what's currently in my .bashrc file:

```
export JAVA_HOME=/usr/lib/jvm/java-6-sun-1.6.0.06/
export CLASSPATH=/usr/share/tomcat5.5/common/lib/jsp-api.jar:/usr/share/tomcat5.5/common/lib/servlet-api.jar

```

here's where the path is set:
```

jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ echo $CLASSPATH
/usr/share/tomcat5.5/common/lib/jsp-api.jar:/usr/share/tomcat5.5/common/lib/servlet-api.jar
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.06/
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$

```

I also tried all the other directories that made sense;
/usr/lib/jvm/java-6-openjdk
/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-6-sun-1.6.0.06


not sure what the problem is. 
I still get this:
```
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ sudo sh startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$


```


thanks for any help.

---

### Post by unutbu on 2008-09-28
Try 
```

sudo startup.sh
```

the "sh" in the middle changes your environment to one that lacks JAVA_HOME.

---

### Post by badperson on 2008-09-28
Hi,

If I do that from within the /usr/share/tomcat5.5/bin directory I get this:

```
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$ sudo startup.sh
sudo: startup.sh: command not found
jason@jason-kubuntu:/usr/share/tomcat5.5/bin$


```

If I go to another directory I get this:

```
jason@jason-kubuntu:/home$ sudo /usr/share/tomcat5.5/bin/startup.sh
Neither the JAVA_HOME nor the JRE_HOME environment variable is defined
At least one of these environment variable is needed to run this program
jason@jason-kubuntu:/home$


```

---

### Post by unutbu on 2008-09-28
Hm. Please post /usr/share/tomcat5.5/bin/startup.sh as an attachment.

---

### Post by jespdj on 2008-09-28
Try opening a new terminal, or logging out and in after changing your .bashrc.

---

### Post by badperson on 2008-09-28
thanks, 
here it is: 
```
#!/bin/sh
# -----------------------------------------------------------------------------
# Start Script for the CATALINA Server
#
# $Id: startup.sh 385888 2006-03-14 21:04:40Z keith $
# -----------------------------------------------------------------------------

# Better OS/400 detection: see Bugzilla 31132
os400=false
darwin=false
case "`uname`" in
CYGWIN*) cygwin=true;;
OS400*) os400=true;;
Darwin*) darwin=true;;
esac

# resolve links - $0 may be a softlink
PRG="$0"

while [ -h "$PRG" ] ; do
  ls=`ls -ld "$PRG"`
  link=`expr "$ls" : '.*-> \(.*\)$'`
  if expr "$link" : '/.*' > /dev/null; then
    PRG="$link"
  else
    PRG=`dirname "$PRG"`/"$link"
  fi
done
 
PRGDIR=`dirname "$PRG"`
EXECUTABLE=catalina.sh

# Check that target executable exists
if $os400; then
  # -x will Only work on the os400 if the files are: 
  # 1. owned by the user
  # 2. owned by the PRIMARY group of the user
  # this will not work if the user belongs in secondary groups
  eval
else
  if [ ! -x "$PRGDIR"/"$EXECUTABLE" ]; then
    echo "Cannot find $PRGDIR/$EXECUTABLE"
    echo "This file is needed to run this program"
    exit 1
  fi
fi 

exec "$PRGDIR"/"$EXECUTABLE" start "$@"

```

---

### Post by unutbu on 2008-09-28
[http://ubuntuforums.org/showthread.php?p=2611681#post2611681](http://ubuntuforums.org/showthread.php?p=2611681#post2611681)

---

### Post by badperson on 2008-09-28
that worked...thanks!!
bp

---

### Post by saeid3 on 2008-09-29
I have same problem for run james (Apache mail server) .

We can't run commands as normal user (we need sudo prefix) , so the result of below command is**not** same as normal user :

$ sudo java -version

I tried to add JAVA_HOME with sudo command:

$ sudo gedit /etc/environment

but it didn't worked !
I am new to the ubuntu and disable root user seems good idea, I like that as default but I don't know what I must do in situation like this.

Thanks in advance for any guide on this subject.

rgd,
sid

---

### Post by SeanHodges on 2008-09-29
I'm not sure I understand your problem.

The JVM used by Tomcat is determined by a variable set in /etc/default/tomcat5.5.

You can edit this file and change the "JAVA_HOME" setting (amongst others) there.

To edit a file as root, you should be able to use the command you described:

```
sudo gedit /etc/default/tomcat5.5
```

This depends on your user having "admin" privileges (if it's the default user created when you installed the system, then this will automatically be the case).

More info on sudo can be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by saeid3 on 2008-09-29
thanks for link ![[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")]

I've done below steps for run [james]("http://james.apache.org/") (which only need JAVA_HOME !)

1_$ sudo -i
2_# vim .bashrc
3_add to this file "export JAVA_HOME=/your/jdk"
4_# . .bashrc
5_# james-2.3.1/bin/run.sh

pay attention result of number 5 is not equals with:
5_$ sudo james-2.3.1/bin/run.sh

rgd,
sid

---

