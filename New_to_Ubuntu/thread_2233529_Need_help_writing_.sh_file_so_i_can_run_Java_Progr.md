---
title: "Need help writing .sh file so i can run Java Program - RSPS (Runescape Private Server"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by hexer2 on 2014-07-09
Hi,

Sorry if I posted in wrong place, wasn't quite sure of where to post this.

I have been been creating a Runescape Private Server as a learning  project, I have been using Windows Vista to do this. But I think my time  would be best spent developing it on linux. I have been using Ubuntu  for a number of years now but have never learnt how to write a .sh file  for a java program.

The .bat file that I was using in windows reads:

@echo off
title Acquittal
java -Xmx1500m -cp  bin;deps/poi.jar;deps/mysql.jar;deps/RuneTopListV2.jar;deps/GTLVote.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar;  server.Server
pause

My "java -version" out put in the terminal is:

unknown@unknown-access-point:~$ java -version
java version "1.7.0_60"
Java(TM) SE Runtime Environment (build 1.7.0_60-b19)
Java HotSpot(TM) Server VM (build 24.60-b09, mixed mode)

And for the RSPS client .bat file

@echo off
title Client
java -cp . -Xmx300m client 10 0 highmem members 32
pause

I am wanting to know how to write a .sh file so that I can run this java program in ubuntu

Any help would be much appreciated,

Thanks

---

### Post by slooksterpsv on 2014-07-10
Well... if you need a title, that will depend on your Terminal version, if it's the Gnome version (which I think Ubuntu uses) I believe you can do this:
wmctrl -r :ACTIVE: -N "MyWindowTitle"

For java, just the command you use to run java apps with whatever you're running.

Pause isn't needed as the terminal doesn't close, it just returns to the bash prompt if an app is finished running.

EDIT: Your sh script would look something like this:

```

#/bin/bash
wmctrl -r:ACTIVE:-N "Hello Terminal"
java *whatever commands here*

```

Change permissions on it:
chmod +x ./*script_name_with_ending_of_*.sh

Then you can run:
./*the_script_you_just_made*.sh

---

### Post by hexer2 on 2014-07-10
Hi I am unsure if I did it right but this is the .sh file I did

Run.sh

```
#/bin/bash 
java -Xmx1500m -cp bin;deps/poi.jar;deps/mysql.jar;deps/RuneTopListV2.jar;deps/GTLVote.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server
```

And this is the output I get when i do ./Run.sh in terminal. I did chmod +x .

```
unknown@unknown-access-point:~/Projects/RSPS/474/474server$ ./Run.sh
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)
where options include:
    -d32      use a 32-bit data model if available
    -d64      use a 64-bit data model if available
    -client      to select the "client" VM
    -server      to select the "server" VM
    -hotspot      is a synonym for the "client" VM  [deprecated]
                  The default VM is server,
                  because you are running on a server-class machine.


    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose:[class|gc|jni]
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
See http://www.oracle.com/technetwork/java/javase/documentation/index.html for more details.
./Run.sh: line 2: deps/poi.jar: Permission denied
./Run.sh: line 2: deps/mysql.jar: Permission denied
./Run.sh: line 2: deps/RuneTopListV2.jar: Permission denied
./Run.sh: line 2: deps/GTLVote.jar: Permission denied
./Run.sh: line 2: deps/mina.jar: Permission denied
./Run.sh: line 2: deps/slf4j.jar: Permission denied
./Run.sh: line 2: deps/slf4j-nop.jar: Permission denied
./Run.sh: line 2: deps/jython.jar: Permission denied
./Run.sh: line 2: log4j-1.2.15.jar: command not found
./Run.sh: line 2: $'server.Server\r': command not found
unknown@unknown-access-point:~/Projects/RSPS/474/474server$
```

this is the Run.bat file that I was using in Windows to run program

```
@echo off 
title Acquittal 
"C:\Program Files\Java\jdk1.7.0_55\bin\java.exe" -Xmx1500m -cp bin;deps/poi.jar;deps/mysql.jar;deps/RuneTopListV2.jar;deps/GTLVote.jar;deps/mina.jar;deps/slf4j.jar;deps/slf4j-nop.jar;deps/jython.jar;log4j-1.2.15.jar; server.Server 
pause
```

Thanks

---

### Post by spjackson on 2014-07-10
In a shell script, the semicolon marks the end of a command. Therefore you use a colon to separate the items in the classpath.
```

#!/bin/bash 
java -Xmx1500m -cp bin:deps/poi.jar:deps/mysql.jar:deps/RuneTopListV2.jar:deps/GTLVote.jar:deps/mina.jar:deps/slf4j.jar:deps/slf4j-nop.jar:deps/jython.jar:log4j-1.2.15.jar server.Server

```

---

### Post by hexer2 on 2014-07-10
Thankyou very much for your help I have the feel of it now thanks

---

