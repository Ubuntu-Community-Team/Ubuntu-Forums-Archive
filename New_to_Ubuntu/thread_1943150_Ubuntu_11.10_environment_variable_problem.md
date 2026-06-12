---
title: "Ubuntu 11.10 environment variable problem"
date: 2012-03-19
forum: New to Ubuntu
---

### Post by huu2011 on 2012-03-19
Hello all,
I have manually installed Tomcat6(/usr/local/tomcat)
,java6(/usr/local/java) with symbolink.
The I added  CATALINA_HOME and JAVA_HOME to ~/.bashrc for non-root and root user.
but I think when I was adding as root, probably could have created the problem below.

root@test-apire-5738:/usr/local/tomcat# gedit ~/.bashrc
Command 'gedit' is available in '/usr/bin/gedit'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
gedit: command not found.

I need to make the variables permanent for all users(,me,root and tomcat).
Please any help how to solve above error appreciated.

---

### Post by huu2011 on 2012-03-19
please,any idea

---

### Post by huu2011 on 2012-03-19
[B]User X:
if I echo $PATH got[/B]
```

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"

```
**root:**
if I echo $PATH,got
```

/usr/local/java/bin

```
**using ls in root:**
```

root@X-Aspire-5738:/home/X# ls
Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found.

```
```

root@X-Aspire-5738:/# ls
Command 'ls' is available in '/bin/ls'
The command could not be located because '/bin' is not included in the PATH environment variable.
ls: command not found

```

**In /etc/environment got this:**

```
gksudo gedit /etc/environment:
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```

google helped little but didnt managed make it work.
any help please

---

### Post by huu2011 on 2012-03-19
guys,
anyone to help me with this silly question??

---

### Post by adit on 2012-03-19
Post the contents of (at least relevant lines)
/etc/profile
/etc/bash.bashrc

---

### Post by huu2011 on 2012-03-19
in /etc/profile, there is just script code

for /etc/bash.bashrc
```

# this file has to be sourced in /etc/profile.

export JAVA_HOME=/usr/lib/jvm/java-6-sun
export PATH=$PATH:$JAVA_HOME/bin
```

i gues the problem originated when I left $PATH
in this:
```
export PATH=$JAVA_HOME/bin:$PATH
```

thank you

---

