---
title: "classpath and compilation problem in java"
date: 2006-10-28
forum: Programming Talk
---

### Post by kno712 on 2006-10-28
Hi, there

Maybe someone can help me with this. 

I hava a very easy java program, that just connect to a mysql database, prompts a success/failure message and then exits. It is just one of those samples that are over the net. 

I use the mysql-connector.jar provided by mysql, located in /usr/share/java and test.java and test.class are in /home/jupiter/java/testSQL

To run it properly I must do

$java -classpath /usr/share/java/mysql-connector.jar:/home/jupiter/java/testSQL test

if not I will get an error.

that seems a lot of folders declarations to me in for running a java program. I know of the classpath variable, but I'm not sure where to declare it: /etc/environment or .bash_profile in $HOME? Which method is the right one? And, will I have to declare every single directory that I will use for storing my java progs? Let's say, next time I use /home/jupiter/java/test_other_program, will I have to declare this folder in the CLASSPATH as well?

Thanks a lot

---

### Post by koala114 on 2006-10-28
My Java environment variable is adhered to /etc/profile
[PHP]
ford@ford-desktop:~$ cat /etc/profile
#/etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ "$PS1" ]; then
  if [ "$BASH" ]; then
    PS1='\u@\h:\w\$ '
    if [ -f /etc/bash.bashrc ]; then
        . /etc/bash.bashrc
    fi
  else
    if [ "`id -u`" -eq 0 ]; then
      PS1='# '
    else
      PS1='$ '
    fi
  fi
fi

umask 022
export JAVA_HOME=/usr/share/jdk1.5.0_08
export JRE=${JAVA_HOME}/jre
export CLASSPAHT=$JAVA_HOME/lib:$JRE/lib:.
export PATH=$PATH:$JAVA_HOME/bin:$JRE/bin:.
ford@ford-desktop:~$
[/PHP]
If you use Ubuntu 6.06 need to remove the gcj, and making Sun's java interpreter is the default.
In this case you could append /usr/share/java/mysql-connector.jar to the CLASSPAHT

---

### Post by kno712 on 2006-10-29
Ok, thanks a lot. I'll try this one. Did you set it manually or was it set automatically when you installed the sdk? Why is that mine is a completely different folder? I did a "sudo aptitude install". (I'm ussing dapper). Does it matter where it is installed?

Thanks a lot.

---

### Post by koala114 on 2006-10-29
I installed the SDK manually, so the folder is difference from you.:KS 
There are two alternative installation for SDK,

Refer to
[https://help.ubuntu.com/community/Java]("https://help.ubuntu.com/community/Java")

---

