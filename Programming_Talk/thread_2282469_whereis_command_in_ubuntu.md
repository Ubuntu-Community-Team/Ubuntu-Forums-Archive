---
title: "whereis command in ubuntu"
date: 2015-06-14
forum: Programming Talk
---

### Post by IAMTubby on 2015-06-14
This is the output of the whereis command when when I run it to get details about the java in my system.

```

IAMTubby@IAMTubby-Inspiron-3542:/usr/lib/java$ whereis java
java: /usr/bin/java /etc/java /usr/lib/java /usr/bin/X11/java /usr/share/java /usr/share/man/man1/java.1.gz

```

I would like to understand the output of the whereis command.
I understand that 
1. **/usr/bin/java** is the executable
2. **/usr/lib/java** contains the libraries
3. **/usr/share/man/man1/java.1.gz** are the man pages

But what are 
**/etc/java, /usr/bin/X11/java **and[B] /usr/share/java

[/B]What do these do?****

---

### Post by kerry_s on 2015-06-14
settings-> /etc/java
executable-> /usr/bin/X11/java 
config files-> /usr/share/java

---

### Post by tgalati4 on 2015-06-14
*Whereis* will find binary, source and manual pages.  You can use switches to limit the search results:

```
man whereis
```

> tgalati4@Mint17 ~ $ whereis bash
bash: /bin/bash /etc/bash.bashrc /usr/share/man/man1/bash.1.gz


In this case, the binary *bash* is stored in /bin/bash, the system-wide configuration file is in /etc/bash.bashrc (bash resources), and the manual (documentation) page is compressed (*.gz) and stored in the usual place:  /usr/share/man/man1/bash.1.gz.

---

### Post by IAMTubby on 2015-06-17
> **kerry_s said:**
> 
executable-> /usr/bin/X11/java 

Thanks kerry_s
But if /usr/bin/X11/java is the executable, then what is /usr/bin/java . I thought this was the executable.

---

### Post by slickymaster on 2015-06-17
**/usr/bin/java** is actually a symbolic link to **/etc/alternatives/java**```
~$ ls -l /usr/bin/java
lrwxrwxrwx 1 root root 22 Out  1  2014 /usr/bin/java -> /etc/alternatives/java
```But, on the other hand```
~$ ls -l /etc/alternatives/java
lrwxrwxrwx 1 root root 39 Out  1  2014 /etc/alternatives/java -> /usr/lib/jvm/java-8-oracle/jre/bin/java
```which is java home directory.

---

