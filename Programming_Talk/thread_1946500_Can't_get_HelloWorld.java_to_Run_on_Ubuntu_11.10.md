---
title: "Can't get HelloWorld.java to Run on Ubuntu 11.10"
date: 2012-03-24
forum: Programming Talk
---

### Post by jpm0004 on 2012-03-24
OK, I am simply trying to run a java program and I can't figure out what is wrong. I've already read the stickys and am not finding the direct answer.

When I run javac -version I get: 
javac 1.6.0_23

When I run java -version, I get a whole other monster:


Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32	  use a 32-bit data model if available
    -d64	  use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -zero	  to select the "zero" VM
    -jamvm	  to select the "jamvm" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is server,
                  because you are running on a server-class machine.


    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -no-jre-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions with specified granularity
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions with specified granularity
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                  see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument
    -splash:<imagepath>
                  show splash screen with specified image
See [http://java.sun.com/javase/reference](http://java.sun.com/javase/reference) for more details.



And sudo update-alternatives --config java gives me:

There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java        1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java        1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java            63        manual mode
* 3            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode
----------------------------------------------------------------

I know there is a simple solution to this, but as always don't know what that solution is.

EDIT: I have tried changing alternative java to all 4 of the shown options. I keep getting this:
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-6-openjdk/jre/bin/java because link group java is broken.
update-alternatives: warning: not replacing /usr/bin/java with a link.

EDIT: I ran sudo apt-get purge openjdk-\* icedtea-\* icedtea6-\* in order to remove all versions of openjdk. javac -version is still: javac 1.6. Now sudo update-alternatives --config java gives me:

There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/jvm/java-6-sun/jre/bin/java because link group java is broken.
update-alternatives: warning: not replacing /usr/bin/java with a link.

---

### Post by slooksterpsv on 2012-03-25
You should only need to type in:

java HelloWorld

you don't need to append .java to the end cause it won't work.

---

### Post by Zugzwang on 2012-03-26
@OP: For a simple HelloWorld program, the Java version actually used should be quite irrelevant, as long as the major version of "java" is >= the major version of "javac".

Please have a look at the stickies and try compiling and running your first Java program: [http://ubuntuforums.org/showthread.php?t=713622](http://ubuntuforums.org/showthread.php?t=713622) (Part 0 is a bit outdated). If this does *not* work, copy and paste the error message you obtained and the command you were using when obtaining it here.

You haven't provided us with any information that suggests that it is indeed your Java installation that causes the problems. For example, you didn't say that you actually compiled your "hello world" program.

---

