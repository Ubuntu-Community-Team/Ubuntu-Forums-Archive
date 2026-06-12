---
title: "[SOLVED] How to compile a Java Program"
date: 2008-10-21
forum: New to Ubuntu
---

### Post by Prabakar on 2008-10-21
Hi again!
I installed Java with this command

```
sudo apt-get install sun-java6-bin sun-java6-jre
```


```

prabakar@HomeComputer:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)

```
```

prabakar@HomeComputer:~$ whereis java
java: /usr/bin/java /usr/share/java /usr/share/man/man1/java.1.gz

```
```

prabakar@HomeComputer:~$ java
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
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
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
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

```
```

prabakar@HomeComputer:~$ javac
The program 'javac' can be found in the following packages:
 * jikes-sun
 * jikes-sablevm
 * gcj-4.2
 * kaffe
 * sun-java6-jdk
 * openjdk-6-jdk
 * ecj
 * j2sdk1.4
 * jikes-classpath
 * jikes-gij
 * gcj-4.1
 * sun-java5-jdk
 * jikes-kaffe
 * java-gcj-compat-dev
Try: sudo apt-get install <selected package>
bash: javac: command not found

```
**Now I have a simple hello world program program that I am not able to compile. Should I set path? If so what is the path I have to set**?

Please Help.

---

### Post by Joeb454 on 2008-10-21
You need to use "javac" to compile your programs. Try installing the following 2 packages:
```
sudo apt-get install openjdk-6-jdk sun-java6-jdk
```

---

### Post by kostkon on 2008-10-21
And, I assume you would want to use the *Sun Java* as your default. To set it, you will need to do this in a terminal:
```
sudo update-java-alternatives -s java-6-sun
```

after this, you can compile your file like this
```
javac filename.java
```

For more complex projects, you could use an IDE like *Netbeans* or *Eclipse*.

---

### Post by Nepherte on 2008-10-21
> **Joeb454 said:**
> You need to use "javac" to compile your programs. Try installing the following 2 packages:
```
sudo apt-get install openjdk-6-jdk sun-java6-jdk
```
Although it can't really harm, I'd just install one jdk and not two.

---

### Post by Prabakar on 2008-10-21
Thank you. It works like a charm:)

---

### Post by Joeb454 on 2008-10-21
> **Nepherte said:**
> Although it can't really harm, I'd just install one jdk and not two.

I can't remember which gave me javac, which is why I suggested both.

---

