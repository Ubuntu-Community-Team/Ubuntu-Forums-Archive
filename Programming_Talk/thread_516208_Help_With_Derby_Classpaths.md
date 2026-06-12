---
title: "Help With Derby Classpaths"
date: 2007-08-02
forum: Programming Talk
---

### Post by themusicwave on 2007-08-02
I have been trying to get derby working for HOURS.  I read several threads to no avail.

I know I am almost there, the error is in the envirment variables or .bashrc I think

Here is the relevant .bashrc section:

#set up derby path
export DERBY_HOME=/opt/Derby_10

#export CLASSPATH "=$JAVA_HOME:$CLASSPATH"
export PATH="$DERBY_HOME/bin:$PATH"

Here is whats in etc/enviroment:

LANGUAGE="en_US:en"

LANG="en_US.UTF-8"
PATH="/usr/local/jvm/java-6-sun/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
CLASSPATH="/usr/local/jvm/java-6-sun/lib:./opt/Derby_10/lib/derby.jar:.:/opt/Derby_10/lib/derbytools.jar"


The error occurs when at this line:
 Class.forName("org.apache.derby.jdbc.EmbeddedDriver")

The error is:
java.lang.ClassNotFoundException: org.apache.derby.jdbc.EmbeddedDriver


I beleive something is wrong in one of those files above.  I am new to this whole setting up the environment thing so please go easy on me.

Thanks,

Jon

---

### Post by AlexThomson_NZ on 2007-08-03
Well I can tell you the class org.apache.derby.jdbc.EmbeddedDriver is not on the classpath.  Can you check inside the jars specified on your CLASSPATH (you can just browse inside them like a zip file), and make sure there is a directory path:
org/apache/derby/jdbc/

And inside that is a file, EmbeddedDriver.class

If not, you will have to find a package with this class and add it to the classpath

---

### Post by jetiandresito on 2009-09-14
I made it work under Ubunty Jaunty.

This tutorial seems very useful:
[http://db.apache.org/derby/papers/DerbyTut/ns_intro.html#ij_ns_client](http://db.apache.org/derby/papers/DerbyTut/ns_intro.html#ij_ns_client)

except the default installation path of Apache Derby (if You use Syaptic package manager) is     /usr/lib/jvm/java-6-sun-1.6.0.16/db

I think there is two differences between You did, and the tuturoal advises:
-  You forgot to run    .setNetworkClientCP.ksh   or   . setNetworkClientCP  (whichever it appers in your /usr/lib/jvm/java-6-sun-1.6.0.16/db/bin     directory,
- the tutorial uses $DERBY_INSTALL instead of $DERBY_HOME, but maybe it is not a serious problem. 





> **themusicwave said:**
> I have been trying to get derby working for HOURS.  I read several threads to no avail.

I know I am almost there, the error is in the envirment variables or .bashrc I think

Here is the relevant .bashrc section:

#set up derby path
export DERBY_HOME=/opt/Derby_10

#export CLASSPATH "=$JAVA_HOME:$CLASSPATH"
export PATH="$DERBY_HOME/bin:$PATH"

Here is whats in etc/enviroment:

LANGUAGE="en_US:en"

LANG="en_US.UTF-8"
PATH="/usr/local/jvm/java-6-sun/bin:.:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
JAVA_HOME="/usr/lib/jvm/java-6-sun"
CLASSPATH="/usr/local/jvm/java-6-sun/lib:./opt/Derby_10/lib/derby.jar:.:/opt/Derby_10/lib/derbytools.jar"


The error occurs when at this line:
 Class.forName("org.apache.derby.jdbc.EmbeddedDriver")

The error is:
java.lang.ClassNotFoundException: org.apache.derby.jdbc.EmbeddedDriver


I beleive something is wrong in one of those files above.  I am new to this whole setting up the environment thing so please go easy on me.

Thanks,

Jon

---

### Post by aganhuyag on 2010-04-15
thanks for the reply! it helped me solve similar problem!

---

