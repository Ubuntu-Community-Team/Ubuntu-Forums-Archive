---
title: "java CLASSPATH Ubuntu 12.10 Server"
date: 2013-04-25
forum: Programming Talk
---

### Post by kr651129 on 2013-04-25
I'd really like to set a CLASSPATH variable in my system so I don't need the -cp flag when compiling Java programs.  I set CLASSPATH in /etc/environment and can echo it fine but javac still seems to not want to use this.  Is there something I'm missing?

---

### Post by slickymaster on 2013-04-26
You can set the CLASSPATH environment variables by adding the following line in **.bashrc** or **.bash_profile** of the home directory or in **/etc/profile** for all users.
```
export CLASSPATH=.://usr/local/java/jdk1.7.0_21/lib/:$CLASSPATH
```
Then just refresh the bash shell:
```
source ~/.bashrc
```
or
```
source ~/.bash_profile
```
or
```
$ source /etc/profile
```, depending on where you add export CLASSPATH line.

---

