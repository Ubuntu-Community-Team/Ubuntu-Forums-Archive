---
title: "jedit wont run"
date: 2007-08-19
forum: Programming Talk
---

### Post by Nolander on 2007-08-19
hi all,

When i run jedit i get this error not sure wat it all means
```

Warning: $JAVA_HOME environment variable not set! Consider setting it.
          Attempting to locate java...
Found a virtual machine at: /usr/bin/java...
nolander@nolander-desktop:~$ Exception in thread "main" java.lang.NoClassDefFoundError: org.gjt.sp.jedit.jEdit
   at java.lang.Class.initializeClass(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at gnu.java.lang.MainThread.run(libgcj.so.7)
Caused by: java.lang.VerifyError: verification failed at PC 122 in org.gjt.sp.jedit.jEdit:reloadModes(()V): incompatible type on stack
   at java.lang.Class.initializeClass(libgcj.so.7)
   ...2 more

```

ta,
nolander.

---

### Post by jnorthr on 2007-08-19
Does not seem like your java jre is installed correctly. Can you go to a terminal command line and type java -version to see which version you have. On my windows xp it shows:
> C:\Documents and Settings\HP_Owner>java -version
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
Since jedit cannot correctly identify your java configuration it cannot run properly as jedit is a java based IDE.

---

### Post by Nolander on 2007-08-19
```

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

do i need to update java. how?

ta,
nolander

---

### Post by cseljatib on 2007-11-18
i am having the same problem, how did you fix it?
please let me know

---

### Post by dwhitney67 on 2007-11-18
Have you followed this advice?

[PHP]Warning: $JAVA_HOME environment variable not set! Consider setting it.[/PHP]

Where do you have Java SDK installed on your system?  Find "javac" using this command:

[FONT="Courier New"]$ which javac[/FONT]

The path leading to java is probably what you need to set JAVA_HOME to.  For instance:

[FONT="Courier New"]export JAVA_HOME=/path/leading/to/SDK[/FONT]

---

