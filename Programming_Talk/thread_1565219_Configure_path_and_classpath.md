---
title: "Configure path and classpath?"
date: 2010-08-31
forum: Programming Talk
---

### Post by Auden on 2010-08-31
Hey this is my first time using ubuntu. And i'm a bit of a java coder, and i'd like to use Ubuntu. Anyways, i got a client from a friend, and i'm trying to run it, but the terminal won't show, i think the main reason is because i haven't set classpath or path. This is what my run.sh currently looks like:

```
#!/bin/bash 
export JAVA_HOME='/usr/lib/jvm/java-6-sun' 
PATH=$JAVA_HOME:$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH 
cd bin && java -Xmx1024M client
```

All the files are in a folder named bin ofc. Can someone give me a tutorial on how to fix it? (Go easy on me as i'm still learning the system of ubuntu)

---

### Post by dileepm on 2011-01-27
What is the error that you get when you try to run the code

---

