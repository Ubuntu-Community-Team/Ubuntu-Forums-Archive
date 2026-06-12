---
title: "Environment variables"
date: 2011-12-09
forum: New to Ubuntu
---

### Post by Scarlet Sphere on 2011-12-09
How do I create an environment variable EJBCA_HOME?
Where are environment variables stored?

---

### Post by bluexrider on 2011-12-09
> **Scarlet Sphere said:**
> How do I create an environment variable EJBCA_HOME?
Where are environment variables stored?
The kernel stores the list of environment  variables and their values for each process, and inherit them to child  processes. They exist at runtime, and are not stored in some file or so.  But there is a virtual file in 
  /proc/<pid>/environ   Which contains all the environment variables. The kernel makes them  visible by that virtual file. One can list them. For example to view the  variables of process 3940, one can do
  cat /proc/3940/environ | tr '\0' '\n'   Each variable is delimited by a binary zero from the next one. tr replaces the zero into a newline. 



-----http://stackoverflow.com

---

### Post by Lars Noodén on 2011-12-09
If you're talking about the shell, then environment variables are stored in [.profile](http://linux.die.net/Bash-Beginners-Guide/sect_03_01.html#sect_03_01_02_03).  You can use [export](http://manpages.ubuntu.com/manpages/precise/en/man1/export.1posix.html) to set the variables.

```

export EJBCA_HOME="The quick brown fox jumped over the lazy god."

```

---

### Post by Scarlet Sphere on 2011-12-11
> **Lars Noodén said:**
> If you're talking about the shell, then environment variables are stored in [.profile](http://linux.die.net/Bash-Beginners-Guide/sect_03_01.html#sect_03_01_02_03).  You can use [export](http://manpages.ubuntu.com/manpages/precise/en/man1/export.1posix.html) to set the variables.

```

export EJBCA_HOME="The quick brown fox jumped over the lazy god."

```

I tried that but it didn't work. I tried:
```
export EJBCA_HOME="/home/user/ejbca"
```
and also:
```
export EJBCA_HOME=/home/user/ejbca
```
I am trying to access it by running:
```
String ejbcaHomeDir = System.getenv("EJBCA_HOME");
```

Did I do something wrong?

---

### Post by wannabegeek on 2011-12-11
I know very little about this topic but have an interest. I didn't know about the system command.  I am wondering what the dot operating is.  Does it call a child function....? I didn't see getenv in the man pages under system. 

I use 
echo $ENVAR  to get the value of a variable

wbg

EDIT

I'm a noob....I thought that system.getenv looked like python....It's JAVA
I got the python version to work,  os.getenv("DISPLAY"), this is a quite useful tid bit

---

### Post by Lars Noodén on 2011-12-12
Try also [font=Courier New].bashrc[/font]

---

### Post by MartijnNL on 2011-12-12
If you want the variable to be present for other users as well, you could also add it to /etc/bash.bashrc (at least that's the file which is used on 10.04).

If it should be available in a login shell (like when using ssh or direct console access) you could use /etc/profile.

For a terminal for yourself only the mentioned ~/.bashrc is the right file. And to be complete: ~./.profile is for login shells for yourself only.

In all cases the syntax would be:
```

export EJBCA_HOME="/home/user/ejbca"
```

---

