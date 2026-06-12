---
title: "bash find + xargs"
date: 2011-08-01
forum: Programming Talk
---

### Post by psycho5 on 2011-08-01
hi, 

I'm trying to run a script that will find a .jar file with a nametag and then pipe the output to execute that jar file...

```

find $HOME -name '*.jar' -name nametag* -type f -print0 | xargs --null java -Xmx512m -Xincgc -jar 

```

How do I pass the file name to the -jar command at the very end? Also... is my find command's syntax correct?

---

### Post by soltanis on 2011-08-01
It looks like that command would do it, have you tried it yet?

From the looks of it a shell glob might also work for you (if there is only one file to execute):

```

java -Xmx512m -Xincgc -jar $HOME/nametag*.jar

```

---

### Post by fdrake on 2011-08-01
> **soltanis said:**
> It looks like that command would do it, have you tried it yet?

From the looks of it a shell glob might also work for you (if there is only one file to execute):

```

java -Xmx512m -Xincgc -jar $HOME/nametag*.jar

```

what if the file is inside a folder inside home? you still need to use find to search recursively

```
find $HOME -name nametag*.jar -type f -print0 | xargs --null java -Xmx512m -Xincgc -jar
```

---

### Post by psycho5 on 2011-08-01
Here's what I get so far

```

[root@vmmyabpafedora abeer]# cat ./InstallerScript.sh 
#!/bin/bash

find $HOME -name '*.jar' -name nametag* -type f -print0 | xargs --null java -Xmx512m -Xincgc -jar 
[root@vmmyabpafedora abeer]# ./InstallerScript.sh 
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32	  use a 32-bit data model if available
    -d64	  use a 64-bit data model if available
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
See http://java.sun.com/javase/reference for more details.
[root@vmmyabpafedora abeer]# 


```

---

### Post by psycho5 on 2011-08-01
I want it so the find command can search the home folder and it's subsequent folders, and also I don't know why it's not passing the results to the java command...

---

### Post by sisco311 on 2011-08-01
Your command will invoke java with a list of files returned by find.
For example:
```
java OPTIONS 1.jar 2.jar 3.jar
```

I guess, you want invoke java for each file separately:
```
java OPTIONS 1.jar
java OPTIONS 2.jar
...

```

You can use find's **-exec command '{}' \;** syntax:
```
find PATH OPTIONS -exec java OPTIONS '{}' \;
```

The same thing with xargs:
```
find PATH OPTIONS -print0 | xargs -0 -I'{}' java OPTIONS '{}'
```

In some cases you have to run java from the subdirectory where the .jar file is. In this case you can use the -execdir option:
```
find PATH OPTIONS -execdir java OPTIONS '{}' \;
```

---

### Post by psycho5 on 2011-08-01
> **sisco311 said:**
> Your command will invoke java with a list of files returned by find.
For example:
```
java OPTIONS 1.jar 2.jar 3.jar
```

I guess, you want invoke java for each file separately:
```
java OPTIONS 1.jar
java OPTIONS 2.jar
...

```

You can use find's **-exec command '{}' \;** syntax:
```
find PATH OPTIONS -exec java OPTIONS '{}' \;
```

The same thing with xargs:
```
find PATH OPTIONS -print0 | xargs -0 -I'{}' java OPTIONS '{}'
```

In some cases you have to run java from the subdirectory where the .jar file is. In this case you can use the -execdir option:
```
find PATH OPTIONS -execdir java OPTIONS '{}' \;
```

Thanks! I don't know why it tells me exec or execdir command not found but xargs -0 -I'{}' java options '{}' \; worked just fine. =)

---

### Post by sisco311 on 2011-08-01
> **psycho5 said:**
> Thanks! I don't know why it tells me exec or execdir command not found

They aren't commands. They are options of the find command (like -name or type):
```
find ~/ -name 'name*.jar' **-execdir** java OPTIONS '{}' \;
```  

See: **man find** for details.

---

