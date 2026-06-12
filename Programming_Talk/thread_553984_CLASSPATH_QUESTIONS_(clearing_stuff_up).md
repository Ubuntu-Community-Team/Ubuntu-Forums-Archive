---
title: "CLASSPATH QUESTIONS (clearing stuff up)"
date: 2007-09-18
forum: Programming Talk
---

### Post by huggy77 on 2007-09-18
i have alot of CLASSPATH questions.

1) if i update /etc/environment do i have to update bash.rc?
2) do you use quotes when setting the path, i have seen posts saying not to and i have seen posts with quotes.
3) what is the **[COLOR="DarkGreen"]:.[/COLOR]** notation for?

my /etc/env* looks like
```

CLASSPATH = /opt/SDK/jdk/lib:.
JAVA_HOME = /opt/SDK/jdk
PATH=/opt/SDK/jdk/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
LANG="en_US.UTF-8"

```

i think it is working because java -version is returning:
```

java version "1.6.0_02"
Java(TM) SE Runtime Environment (build 1.6.0_02-b05)
Java HotSpot(TM) Client VM (build 1.6.0_02-b05, mixed mode)

```

thanks in advance - i have seen alot of classpath questions and some  conflicting info

---

### Post by pbrockway2 on 2007-09-19
Personally I don't like to rely on a CLASSPATH environment variable - I prefer to set the classpath as part of the command used to invoke a java tool.  This way I am protected from the values of CLASSPATH that might be inappropriate, and it is more flexible: there is no reason to believe that everything I do will require exactly the same classpath.  Eg, to compile and run:```
javac -cp . HelloWorld.java
java -cp . HelloWorld
```
or```
javac -cp .:path/to/thirdParty.jar pack/*.java
java -cp .:path/to/thirdParty.jar pack.Main
```
Either way the -cp switch is followed by the classpath expressed in the same syntax as the environment variable.  The CLASSPATH variable is ignored if the -cp switch is used.

The . means "current directory".  It is quite common for this to be part of the classpath and for very simple programs like the first example above it might be the only thing on the classpath.

java -version is not enough to check that the classpath is correct.  As I suggested above, there isn't (in my opinion) such a thing as a "correct" classpath, or a classpath that is "working".  The classpath is the list of directories (or jar files) within which the java tools will look for classes.  What this should be depends on the particular task being carried out.

---

### Post by mssever on 2007-09-19
> **huggy77 said:**
> 1) if i update /etc/environment do i have to update bash.rc?
I'm guessing you don't. I've never messed with that file, though. Change it, fire up a new shell, and check the values of the changed variables.
> 2) do you use quotes when setting the path, i have seen posts saying not to and i have seen posts with quotes.If this is in sh or bash format, as it appears to be, then it can't hurt to use double quotes. And, in fact, it's a good idea to do so if in doubt because sh/bash is very aggressive when it comes to breaking up strings.
> 3) what is the **[COLOR=DarkGreen]:.[/COLOR]** notation for?: is the record separator; it separates individual $PATH entries. The . means "current directory."
> ```
CLASSPATH = /opt/SDK/jdk/lib:.
JAVA_HOME = /opt/SDK/jdk
```If this is a bash/sh file, then these two lines contain syntax errors. In bash and sh, spaces on either side of the equal sign are forbidden if you're trying to assign to a variable. Try ```
CLASSPATH="/opt/SDK/jdk/lib:."
JAVA_HOME="/opt/SDK/jdk"
```

---

### Post by huggy77 on 2007-09-19
mssever - that is a great post - thank you so much....  I took those spaces out...

FANTASTIC POST.... THANKS AGAIN!

---

