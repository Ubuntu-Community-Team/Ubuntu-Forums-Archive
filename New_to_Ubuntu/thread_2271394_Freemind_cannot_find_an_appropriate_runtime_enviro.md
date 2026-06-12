---
title: "Freemind cannot find an appropriate runtime environment"
date: 2015-03-29
forum: New to Ubuntu
---

### Post by Nina_Milliken on 2015-03-29
I'm running Ubuntu version 14.04 on my Macbook with Java version 1.7.0_76.  

I installed Freemind through the Ubuntu Software Center and it will not run.  When I try to execute it in Terminal, I get the following output:

```

ninamillik@ninamillik-MacBook:/usr/bin$ freemind
[warning] /usr/bin/freemind: No java runtime was found
[error] /usr/bin/freemind: Unable to find an appropriate java runtime. See java_wrappers(7) for help

```

This is what I've tried:
As per this thread: [thread]2087426[/thread]
I found the directory where java, javaws, etc. were located: /usr/lib/jvm/java-7-oracle/bin
as well as where jvm-lists.sh and java-wrappers.sh were located: /usr/lib/java-wrappers
I changed in /usr/lib/java-wrappers/**jvm-lists.sh** the [COLOR=#ff0000][FONT=courier new]__jvm_default="/usr/lib/jvm/default-java"[/FONT][/COLOR] to [COLOR=#ff0000][FONT=courier new]__jvm_default="/usr/lib/jvm/java-7-oracle/bin"[/FONT][/COLOR]
and in /usr/lib/java-wrappers/**java-wrappers.sh** the[COLOR=#ff0000] [FONT=courier new]DIR=""[/FONT][/COLOR] to [COLOR=#ff0000][FONT=courier new]DIRS="$__jvm_default"[/FONT][/COLOR]

But I still got the same error message.

In the Freemind source code, it states that the program is looking for java6.

```

#--------- Put the environment together --------------------------------

_source /etc/freemind/freemindrc
_source ~/.freemind/freemindrc

if [ -r /usr/lib/java-wrappers/java-wrappers.sh ]
then # the Debian method
        . /usr/lib/java-wrappers/java-wrappers.sh
        require_java_runtime **java6**
else
        findjava
        if [ $? -ne 0 ]
        then
                exit 1
        fi
fi

```

I changed [FONT=courier new][COLOR=#FF0000]java6[/COLOR][/FONT] to [FONT=courier new][COLOR=#FF0000]java7[/COLOR][/FONT] but this did not work.

The last thing I tried was installing the JDK version 6 to my computer and changing [COLOR=#ff0000][FONT=courier new]__jvm_default[/FONT][/COLOR][FONT=courier new][FONT=verdana] to the directory where the java, javaws, etc. (version 6) were located.

As far as I can tell, everything is set up correctly, but it still will not run.  Any and all advice will be greatly appreciated!
[/FONT][/FONT]

---

### Post by steeldriver on 2015-03-29
Hello and welcome to the forums

It appears to work out of the box on my 14.04 64-bit Intel system with the default openjdk-7 jre version 1.7.0_75

```

$ java -version
java version "1.7.0_75"
OpenJDK Runtime Environment (IcedTea 2.5.4) (7u75-2.5.4-1~trusty1)
OpenJDK 64-Bit Server VM (build 24.75-b04, mixed mode)

```

I don't know if that helps.

---

### Post by Nina_Milliken on 2015-03-29
Wow!  I installed the openjdk-7 and it worked right away!  Thank you so much!

---

### Post by Bucky Ball on 2015-03-30
Good news you got it sorted. Freemind rocks (I also use Freeplane, almost identical). Enjoy. ;)

> **steeldriver said:**
> It appears to work out of the box on my 14.04 64-bit Intel system with the default openjdk-7 jre version 1.7.0_75



Same here.

---

