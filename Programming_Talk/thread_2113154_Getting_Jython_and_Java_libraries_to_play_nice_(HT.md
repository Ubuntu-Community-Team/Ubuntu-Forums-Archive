---
title: "Getting Jython and Java libraries to play nice (HTTPUnit in this case)"
date: 2013-02-06
forum: Programming Talk
---

### Post by Aped on 2013-02-06
Hey guys, this is probably due to my lack of java experience in general more than to any fault in installers, package managers, etc, so I'm just looking for a little knowledge. I've installed jython recently and want to use it to do some javascript-capable web testing (one of the few things which Python libraries, such as Mechanize, seem to lack completely). 

Unfortunately, I'm doing something wrong. 

```

aped@desktop:~$ sudo apt-get install jython
...
aped@desktop:~$ sudo apt-get install libhttpunit-java
...
aped@desktop:~$ jython
Jython 2.5.1+ (Release_2_5_1, Oct 31 2011, 11:44:27) 
[OpenJDK 64-Bit Server VM (Sun Microsystems Inc.)] on java1.6.0_24
Type "help", "copyright", "credits" or "license" for more information.
>>> import com.meterware.httpunit
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named meterware
>>> from com import *
>>> locals().keys()
['xhaus', 'kenai', 'ziclix', '__doc__', 'sun', '__name__']
>>> ^D
aped@desktop:~$ java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.5) (6b24-1.11.5-0ubuntu1~12.04.1)
OpenJDK 64-Bit Server VM (build 20.0-b12, mixed mode)

```

Is this a $CLASSPATH issue or something of that nature? Any and all help would be appreciated, thanks.


EDIT: More fiddling, apparently the jar itself, not the directory containing the jar, needs to be in the $CLASSPATH. 
```

aped@desktop:~$ export CLASSPATH=/usr/share/java/httpunit.jar
aped@desktop:~$ jython
*sys-package-mgr*: processing new jar, '/usr/share/java/httpunit-1.7.jar'
from Jython 2.5.1+ (Release_2_5_1, Oct 31 2011, 11:44:27) 
[OpenJDK 64-Bit Server VM (Sun Microsystems Inc.)] on java1.6.0_24
Type "help", "copyright", "credits" or "license" for more information.
>>> from com.meterware import *
>>> 
```

Ta daa. Leaving noob question and obvious answer for posterity's sake, in case anyone is stupid in exactly the same way as I was.

---

### Post by r-senior on 2013-02-06
Most times it's better to set up the classpath on an as-needs basis rather than setting the CLASSPATH in the environment.

With a Java program, you'd do it with:

```
java -cp <CLASSPATH>
```

I don't have Jython to try, but the docs say it's possible to pass an argument through to the VM something like this:

```
jython -J-cp <CLASSPATH>
```

[http://www.jython.org/docs/using/cmdline.html#jython-launcher-options](http://www.jython.org/docs/using/cmdline.html#jython-launcher-options)

---

### Post by Aped on 2013-02-06
> **r-senior said:**
> Most times it's better to set up the classpath on an as-needs basis rather than setting the CLASSPATH in the environment.

With a Java program, you'd do it with:

```
java -cp <CLASSPATH>
```

I don't have Jython to try, but the docs say it's possible to pass an argument through to the VM something like this:

```
jython -J-cp <CLASSPATH>
```

[http://www.jython.org/docs/using/cmdline.html#jython-launcher-options](http://www.jython.org/docs/using/cmdline.html#jython-launcher-options)

Thanks for the heads up.

---

