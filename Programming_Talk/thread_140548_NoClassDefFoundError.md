---
title: "NoClassDefFoundError"
date: 2006-03-06
forum: Programming Talk
---

### Post by jimmah on 2006-03-06
Hi guys,
     I'm sure this has been discussed and solved many times but couldn't seem to be able to locate a definitive solution. Basically I can compile any and all .java files I wish, but when i come to run them, i get the ubiquitous "NoClassDefFoundError" compiler error.

An example of my compiler output is:
```
jim@daedalus:~/work/java/networking/multiSockets/server$ java MultiServer
Exception in thread "main" java.lang.NoClassDefFoundError: MultiServer

```

Contents on the folder I'm working in:
```
jim@daedalus:~/work/java/networking/multiSockets/server$ ls
MultiServer$1.class  MultiServerThread$1.class  MultiServerThread.java
MultiServer.class    MultiServerThread$2.class  MultiServerThread.java~
MultiServer.java     MultiServerThread$3.class
MultiServer.java~    MultiServerThread.class
```



I know the java code is correct, as I have run it in my university laboratory, it appears to be some problem with java being unable to locate class files (i.e. classpath problem). 

Just need to set the classpath permanently, so I can get on with this! Any help very very much appreciated.

Jim :)

---

### Post by knalle on 2006-03-06
try

```

java -cp .:$CLASSPATH MultiServer

```

---

### Post by jimmah on 2006-03-06
yeah that works for the short-term, but I really could do with just having it set permanently so I don't have to use the '-cp' or '-classpath' switch each time.

Any ideas?

Thanks
Jim

---

