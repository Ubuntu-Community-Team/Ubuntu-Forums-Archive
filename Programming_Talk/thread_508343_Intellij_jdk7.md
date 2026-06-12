---
title: "Intellij jdk7"
date: 2007-07-24
forum: Programming Talk
---

### Post by aliov_85 on 2007-07-24
Hello everybody , I installed jdk 6, and I'm not able to run idea.sh correctly.
When I run idea.sh I get this message:
[b]ERROR: cannot start IntelliJ IDEA.
No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
exec: 63: /bin/java: not found[/b]

Here is my idea.sh:
[b]#!/bin/sh
#
# ------------------------------------------------------
#  IntelliJ IDEA Startup Script for Unix
# ------------------------------------------------------
#

# ---------------------------------------------------------------------
# Before you run IntelliJ IDEA specify the location of the
# JDK 1.5 installation directory which will be used for running IDEA
# ---------------------------------------------------------------------


if [ -z "$IDEA_JDK" ]; then
  IDEA_JDK= $JDK_HOME
  if [ -z "$IDEA_JDK" ]; then
    echo ERROR: cannot start IntelliJ IDEA.
    echo No JDK found to run IDEA. Please validate either IDEA_JDK or JDK_HOME points to valid JDK installation
  fi
fi

#--------------------------------------------------------------------------
#   Ensure the IDEA_HOME var for this script points to the
#   home directory where IntelliJ IDEA is installed on your system.

IDEA_HOME=`dirname "$0"`/..
IDEA_BIN_HOME=`dirname "$0"`

export JAVA_HOME
export IDEA_HOME

if [ -n "$IDEA_PROPERTIES" ]; then
  IDEA_PROPERTIES_PROPERTY=-Didea.properties.file=$IDEA_PROPERTIES
fi

if [ -z "$IDEA_MAIN_CLASS_NAME" ]; then
  IDEA_MAIN_CLASS_NAME="com.intellij.idea.Main"
fi

if [ -z "$IDEA_VM_OPTIONS" ]; then
  IDEA_VM_OPTIONS="$IDEA_HOME/bin/idea.vmoptions"
fi

REQUIRED_JVM_ARGS="-Xbootclasspath/p:../lib/boot.jar $IDEA_PROPERTIES_PROPERTY $REQUIRED_JVM_ARGS"
JVM_ARGS=`tr '\n' ' ' < "$IDEA_VM_OPTIONS"`
JVM_ARGS="$JVM_ARGS $REQUIRED_JVM_ARGS"

CLASSPATH=../lib/bootstrap.jar
CLASSPATH=$CLASSPATH:../lib/openapi.jar
CLASSPATH=$CLASSPATH:../lib/jdom.jar
CLASSPATH=$CLASSPATH:../lib/log4j.jar
CLASSPATH=$CLASSPATH:../lib/extensions.jar
CLASSPATH=$CLASSPATH:$IDEA_JDK/lib/tools.jar
CLASSPATH=$CLASSPATH:$IDEA_CLASSPATH

export CLASSPATH

LD_LIBRARY_PATH=.:$LD_LIBRARY_PATH
export LD_LIBRARY_PATH


cd "$IDEA_BIN_HOME"
exec $IDEA_JDK/bin/java $JVM_ARGS $IDEA_MAIN_CLASS_NAME $*[/b]

Here is my /etc/environment:
[b]PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_US.UTF-8"
LANGUAGE="en_US:en"

CLASSPATH=.:/usr/lib/java-6-sun-1.6.0.00/bin
JAVA_HOME=/usr/lib/java-6-sun-1.6.0.00
[/b]

The path of idea is: /usr/lib/idea-6833

Thanks in advance for any help

---

### Post by jnorthr on 2007-07-24
from a terminal command line can you try 
java -v
or
javac -v
to confirm java is installed  correctly

---

### Post by aliov_85 on 2007-07-24
Hello man, thank you for your reply.
You were wright. Here are the result of commands:
> 
nazanin@ali:~$ java -v
Unrecognized option: -v
Could not create the Java virtual machine.
nazanin@ali:~$ javac -v
javac: invalid flag: -v
Usage: javac <options> <source files>
use -help for a list of possible options
nazanin@ali:~$


What should I do know?

---

### Post by oparnier on 2007-07-24
try "java -version" to see what JVM you have installed

Please run : "env" to see all your environments variables

---

### Post by aliov_85 on 2007-07-24
java -version:
> 
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

env:
> 
SSH_AGENT_PID=5286
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
GTK_RC_FILES=/etc/gtk/gtkrc:/home/nazanin/.gtkrc-1.2-gnome2
WINDOWID=65011807
USER=nazanin
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-sOeMxz5248/agent.5248
GNOME_KEYRING_SOCKET=/tmp/keyring-RElrnE/socket
SESSION_MANAGER=local/ali:/tmp/.ICE-unix/5248
USERNAME=nazanin
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/lib/java-6-sun-1.6.0.00//bin
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/nazanin
JAVA_HOME=/usr/lib/java-6-sun-1.6.0.00/
LANG=en_US.UTF-8
GDMSESSION=default
HISTCONTROL=ignoredups
SHLVL=1
HOME=/home/nazanin
LANGUAGE=en_US:en
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=nazanin
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-cpfqq7AFwo,guid=4b249219aef73f56c1bac90046a58e35
CLASSPATH=.:/usr/lib/java-6-sun-1.6.0.00/bin
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/nazanin/.Xauthority
_=/usr/bin/env

Thank you very much

---

### Post by oparnier on 2007-07-24
try 
```
export JDK_HOME=$JAVA_HOME
```

it will set a new environment variable JDK_HOME (asked by IDA installer script) to your JAVA_HOME directory where you java JVM is installed. 

and rerun install

---

### Post by aliov_85 on 2007-07-24
Excuse me I don't understand what do you mean by "rerun install".

I've done what you told me, I do this:
> export JDK_HOME=$JAVA_HOME

and then when try again with > ./idea.sh I have the same problem.

---

### Post by aliov_85 on 2007-07-24
please

---

### Post by oparnier on 2007-07-24
maybe try 
```
export IDEA_JDK=$JAVA_HOME
```
and rerun idea script in the same terminal

---

### Post by jnorthr on 2007-07-24
Hi Naz -
The value in your PATH statement PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/usr/lib/java-6-sun-1.6.0.00[COLOR="Red"]//[/COLOR]bin
does not appear correct with two [COLOR="red"]//[/COLOR] char.s before the last bin. Could you pls remove one of those to see what happens ?

---

### Post by aliov_85 on 2007-07-25
Hello guys, I would like to thank for your help.

In fact I resolved the problem by Using at first:
> export IDEA_JDK=$JAVA_HOME

The value in my PATH statement was wrong. I think I copied the path from another site which produced the error. so I chane it as you told me and the is no more error.

Thank you very much

Ali 

bye bye

---

### Post by jnorthr on 2007-07-25
You are welcome. Let us know how you get on with java. Have you loaded the java 6.0 documentation yet ?

---

