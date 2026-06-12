---
title: "javac problem need quick help"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by Zigon on 2008-05-25
I've read a few tutorials and searched the forums, I have no idea why it's still not working

/etc/profile
```
# /etc/profile: system-wide .profile file for the Bourne shell (sh(1))
# and Bourne compatible shells (bash(1), ksh(1), ash(1), ...).

if [ -d /etc/profile.d ]; then
  for i in /etc/profile.d/*.sh; do
    if [ -r $i ]; then
      . $i
    fi
  done
  unset i
fi

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

export PATH=$PATH:/home/zigon/Desktop/jdk1.6.0_06/bin
```

/etc/environment
```
PATH="/home/zigon/Desktop/jdk1.6.0_06/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/home/zigon/Desktop/jdk1.6.0_06/"
CLASSPATH="/home/zigon/Desktop/jdk1.6.0_06/lib:."

```

The output I receive when typing "javac" in the terminal:
```
The program 'javac' can be found in the following packages:
 * java-gcj-compat-dev
 * openjdk-6-jdk
 * gcj-4.2
 * kaffe
 * sun-java6-jdk
 * ecj
 * jikes-sablevm
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * jikes-kaffe
 * jikes-sun
Try: sudo apt-get install <selected package>
bash: javac: command not found

```

I installed jdk straight from the sun website. 
Quick question, does the colon replace the semicolon used in windows?

I apologize for  having this thread posted again, and again, and...

---

### Post by superprash2003 on 2008-05-25
better install java from synaptic (System->administratoin->synaptic)

---

### Post by Zigon on 2008-05-25
Thanks :D Could you explain why I had to do this? Why installing off the site and adding the environment values didn't work?
Also, I compiled successfully but when I try to run it "java test.java" I get the "exception in thread "main"" error.

EDIT: Nevermind, I was trying to run it with "java Test**.java**"

---

