---
title: "Eclipse, java"
date: 2006-02-01
forum: Programming Talk
---

### Post by Mis_Uszatek on 2006-02-01
Hello

I have installed Eclipse, but I had a problem with debbugging, so I have installed Java50 SDK from Sun homepage.
Ok, now Eclipse is working and debugging(I've changed environment settings in Eclipse) great, but it(Eclipse) is still running under Java 1.4(I can see it in SystemMonitor)
When I have typed "java -version" I've got :
>java version "1.4.2"
>gij (GNU libgcj) version 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1->4ubuntu9)

The problem is, that Eclipse is soooo slow on my machine (Ubuntu 5.10, xfce, 0.9GHZ, 512MB).

I have read on this forum somewhere that Eclipse running under jre50 from Sun is much, much faster. I don't know is it true, but I would like to check it.

How to change it, that Eclipse(and other Java applications will be running under jre50, and not from jre1.4)?

Are there any other tricks to speed up Eclipse?

Best Regards

---

### Post by hod139 on 2006-02-01
Try running the command 
```

sudo update-alternatives --config java

``` 
and choose a default java of your liking.  

Note, for me, I also had to remove gcj executable
 ```

apt-get remove --purge java-gcj-compat
 
``` which forced eclipse to search for an alternative java runtime when launching.

---

### Post by slavik on 2006-02-01
no need to remove anything :)

find the dir where you installed java 5 (I am assuming it's not a default dir since you got it from sun's site) then in one of the menus for the compiler, it will allow you to select the environment.

when you get to the compiler menu to select the default compiler version, there should be a 'blue link' (html type link) on the bottom of the form (can't miss it) that will talk about some config stuff, click it

The gcj (the GNU Java Compiler, is it native code compiler or java bytecode compiler?) should be (probably is) the only thing listed.

then you press the add button (I think) and browse to the dir where you installed the java5 jdk (/opt/java5 if that is your install dir, mine was installed to the desktop for a very moronic reason.) and click select and it will be loaded and you can select it.

alternatively, you can get it to search your entire file system for all of the available jdk/jre environments ... but that could take a while.

---

### Post by hod139 on 2006-02-01
Slavik, the problem, as I understood it, isn't getting Eclipse to compile programs using Sun's JDK; the problem is getting Eclipse itself (which is written in Java) to run using Sun's JRE instead of GNU's open Java runtime.  It runs much faster using Sun's implementation that it does using GNU's.  The update-alternatives command I gave updates the default Java runtime (JRE) for the system, not for eclipse only.  

For me though, simply setting the default to Sun's JRE wasn't enough.  I had to remove the  java-gcj-compat package which is "java-gcj-compat is a collection of wrapper scripts, symlinks and jar files.  It is meant to provide a Java-RTE-like interface to the GIJ/GCJ tool set."  With this package gone, Eclipse would search for another JRE to use to launch itself.  With the package installed, Eclipse would always use the GNU java runtime (maybe a bug) even though I changed the default using the update-alternatives command.

---

### Post by slavik on 2006-02-01
you most likely missed half my instructions because when I wrote them I wasn't looking at eclipse (it's my fault) ...

in eclipse, you can select which jre to use. :)

---

### Post by hod139 on 2006-02-01
[quote=slavik] in eclipse, you can select which jre to use. :)[/quote] 
Maybe I am missing something, but I am pretty sure the jre you select is for running the java programs you write with Eclipse only.  If I click Window->Preferences->Java->Compiler there is no html link.  Also, all I can set is the compliance level (which effects only code I write) and 5 Classfile generation checkboxes.  There is also no useful settings under the compiler options.

If instead I go to Window->Preferences->Java->Installed JREs I can now Add, remove, or edit JRE definitions.  But again, these JREs are used to build and run Java programs, not eclipse.  From the Installed JREs page "The checked JRE will be used by default to build and run Java programs".  This is not the JRE Eclipse uses to run.

I looked everywhere in the preferences for specifying a runtime for eclipse to use, but couldn't find anything.  The only way I know of for having eclipse run using the sun-jre is what I wrote in my first post.  I have eclipse version 3.1.1.  Maybe I am looking in the wrong place?

Could you do me a favor and launch eclipse from a terminal. I have posted the output I get.
```

~$eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...not found
testing /usr/lib/kaffe/pthreads...not found
testing /usr/lib/sablevm...not found
testing /usr/lib/fjsdk...not found
testing /usr/lib/j2se/1.5...not found
testing /usr/lib/j2se/1.4...not found
testing /usr/lib/j2sdk1.5-ibm...not found
testing /usr/lib/j2sdk1.4-ibm...not found
testing /usr/lib/j2sdk1.5-sun...found

```
As you can see, since I removed the gcj runtime, eclipse was forced to search for a location from a set of default location.  You can also specify the location using the -vm option

```

~$eclipse -vm /usr/lib/j2sdk1.5-sun
using specified vm: /usr/lib/j2sdk1.5-sun

```

Using the -vm flag every time you launch eclipse would probably avoid the need to uninstall the java-gcj-compat package; but on my system I don't want anything to use it so it was safe to remove.

---

### Post by Mis_Uszatek on 2006-02-02
As I type from terminal 'eclipse'
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found

But I have found where are the eclipse settings.
/etc/eclipse/java_home

There is a list of all of vm which it is looking for.
I have added on the first place vm from Sun, and it is working now.

Thanks everyone.

---

### Post by tbe on 2006-02-05
Thanks guys, I had the same problem and I found this thread really helpful ;) 
It all worked!

The only thing I did not find here was a tip on how to install Sun's JVMs using apt-get. 
I found that here: 
[http://www.ubuntuforums.org/showthread.php?t=106222&highlight=Eclipse](http://www.ubuntuforums.org/showthread.php?t=106222&highlight=Eclipse)

After doing that, rather than move JVM paths around in /etc/eclipse/java_home,  I followed the instructions in the comment at the top of that file:

# This file determines the search order the Eclipse Platform uses to find a
# compatible JAVA_HOME. This setting may be overridden on a per-user basis by
# altering the JAVA_HOME setting in ~/.eclipse/eclipserc.

i.e, doing 

> echo 'JAVA_HOME=/usr/lib/j2re1.5-sun' >> ~/.eclipse/eclipserc

after installing the sun j2re1.5 was all I needed to do.

---

### Post by cow_racer on 2006-02-05
Eclipse is not going to be running fast on a 900 MHz computer.  In fact, it is almost unusable.  You will need a faster machine.  If you don't mind not having features such as autocompletion, turn them off.  Turn off the auto checking for error as you type.    Best solution is to get a faster machine (1.6 Ghz or better with 512 MB RAM or more.)

---

### Post by Mis_Uszatek on 2006-02-08
Yes, it is true that eclipse is still slow on my machine, but mostly I'm using it for package management and debugging. I write code in gedit, and gedit is quite fast ;) But thanks for the tip with errors and autocompletion, I will check it.

---

### Post by cabezon on 2006-08-09
What if I want to use eclipse gcj version. 
I got this: 
ii  eclipse-base                                    3.1.1-1ubuntu3                       Eclipse distribution base
ii  eclipse-jdt                                     3.1.1-1ubuntu3                       Java Development Tools plug-ins for Eclipse
ii  eclipse-jdt-common                              3.1.1-1ubuntu3                       Java Development Tools plug-ins for Eclipse
ii  eclipse-jdt-gcj                                 3.1.1-1ubuntu3                       Java Development Tools plug-ins for Eclipse
ii  eclipse-pde                                     3.1.1-1ubuntu3                       Plug-in Development Environment to develop E
ii  eclipse-pde-common                              3.1.1-1ubuntu3                       Plug-in Development Environment to develop E
ii  eclipse-pde-gcj                                 3.1.1-1ubuntu3                       Plug-in Development Environment to develop E
ii  eclipse-platform                                3.1.1-1ubuntu3                       Eclipse platform without plug-ins to develop
ii  eclipse-platform-common                         3.1.1-1ubuntu3                       Eclipse platform without plug-ins to develop
ii  eclipse-platform-gcj                            3.1.1-1ubuntu3                       Eclipse platform without plug-ins to develop
ii  eclipse-rcp                                     3.1.1-1ubuntu3                       Eclipse rich client platform
ii  eclipse-rcp-common                              3.1.1-1ubuntu3                       Eclipse rich client platform (common files)
ii  eclipse-rcp-gcj                                 3.1.1-1ubuntu3                       Eclipse rich client platform (GCJ version)
ii  eclipse-sdk                                     3.1.1-1ubuntu3                       Extensible Tool Platform and Java IDE
ii  eclipse-source                                  3.1.1-1ubuntu3                       Eclipse source code plug-ins


So i should be able to run eclipse with the GCJ vm, i speacially downloaded the gcj rich client, to see how fast it goes an x86_64

but it aint working just after an aptitude install.


any help is apreaciated.

---

