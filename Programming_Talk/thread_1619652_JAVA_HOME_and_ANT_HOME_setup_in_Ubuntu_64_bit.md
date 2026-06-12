---
title: "JAVA_HOME and ANT_HOME setup in Ubuntu 64 bit"
date: 2010-11-12
forum: Programming Talk
---

### Post by albertwt on 2010-11-12
Hi All,

I've successfully installed Java and Ant using **apt-get**, however when i tried to echo the env. variable, I doesn't give me anything ?

But, i can see some result here:
> 
root@SSV:~# java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) 64-Bit Server VM (build 17.1-b03, mixed mode)

root@SSV:~# ant
Buildfile: build.xml does not exist!
Build failed


is that working configuration or i shall add it into /etc/environment file like the following ?

> 
root@SSV:~# whereis ant
**ant: /usr/bin/ant /usr/share/ant /usr/share/man/man1/ant.1.gz**

root@SSV:~# whereis java
**java: /usr/bin/java /etc/java /usr/share/java /usr/share/man/man1/java.1.gz**
root@SSV:~#


Any help would be greatly appreciated. 

Thanks

---

### Post by spjackson on 2010-11-12
You don't need to set JAVA_HOME and ANT_HOME in order for java and ant to work, which is why installing the packages doesn't result in them being set.
```

ant -diagnostics | grep home

```If the values of ant.home and/or java.home are not what you want, then you will need to set the environment variables in order to override the system defaults. You would also need to set them if you use them in scripts etc.

If you need the variables to be set for all users, then /etc/environment is the right place. If it's just for you, then put them in ~/.bashrc instead.

Finally, if you set the variables in /etc/environment or ~/.bashrc the changes won't affect your current shell, so there's no point editing these files, then reporting that echo doesn't show the changes. /etc/environment is read at login time and ~/.bashrc is read when you start a new shell.

---

### Post by albertwt on 2010-11-12
> **spjackson said:**
> You don't need to set JAVA_HOME and ANT_HOME in order for java and ant to work, which is why installing the packages doesn't result in them being set.
```

ant -diagnostics | grep home

```If the values of ant.home and/or java.home are not what you want, then you will need to set the environment variables in order to override the system defaults. You would also need to set them if you use them in scripts etc.

**If you need the variables to be set for all users, then /etc/environment is the right place. If it's just for you, then put them in ~/.bashrc instead.**

Finally, if you set the variables in /etc/environment or ~/.bashrc the changes won't affect your current shell, so there's no point editing these files, then reporting that echo doesn't show the changes. /etc/environment is read at login time and ~/.bashrc is read when you start a new shell.

Ah yes, then it is already working now.
Thanks for the help and explanation man, I appreciate it.

Cheers,

Albert

---

