---
title: "persistence of environment variables"
date: 2006-05-12
forum: Programming Talk
---

### Post by tedwardo2 on 2006-05-12
Every time I open a terminal window to compile/run Java I have to enter these commands
```
export JAVA_HOME=/usr/lib/j2sdk1.5-sun
export CLASSPATH=.:/usr/share/java/junit.jar
```
and if I close the terminal window and open another I get
```
tedwardo2@teo-ubuntu:~$ echo $JAVA_HOME

tedwardo2@teo-ubuntu:~$ echo $CLASSPATH

```

So for some reason these environment variables won't persist and I can't compile any Java without adding them again.  Does anybody know why that is?

Thanks,
Trent

---

### Post by xenmax on 2006-05-12
You need to put those lines in your ~/.bashrc - this will ensure that everytime bash startsup, these env variables will be set for you.

Any variables set in shell will be local only to that shell instance and will be lost once shell is exited.

---

### Post by tedwardo2 on 2006-05-12
Oh, cool.  Thanks for the quick reply.  That makes a lot of sense.

---

### Post by vinodis on 2006-06-07
In Dapper, try /etc/environment

---

