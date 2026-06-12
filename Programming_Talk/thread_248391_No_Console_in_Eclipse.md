---
title: "No Console in Eclipse"
date: 2006-09-01
forum: Programming Talk
---

### Post by nrwilk on 2006-09-01
I had java installed from the repositories.  I installed eclipse, and tried to run a hello world program, but I got an error dialog that said "Exception occured executing command line."  I messed with various things (installed other eclipse packages, edited files, removed packages) to see if I could get it to work correctly.  Eventually, I stopped getting the console error, and instead I got this output in Eclipse's console tab:```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

``` It also opens a completely new instance of Eclipse, too.

I found a thread with a similar problem, and the answer was to install Sun's java.  It worked for the thread starter, so i tried it.

I installed sun's jdk 1.5.0_08 successfully.  It includes jre version 1.5.0_08, which works correctly as verified in firefox.

Here's the output of java -version:
```
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Server VM (build 1.5.0_08-b03, mixed mode)
``` 
I then installed eclipse-platform and eclipse-jdt, which were pretty much guesses as to what I'd need just to compile java programs with Eclipse.  That installed all of the following:```
ant ant-optional ecj-bootstrap ecj-bootstrap-gcj eclipse eclipse-jdt-common eclipse-jdt-gcj eclipse-pde
  eclipse-pde-common eclipse-pde-gcj eclipse-platform-common eclipse-platform-gcj eclipse-rcp
  eclipse-rcp-common eclipse-rcp-gcj eclipse-source junit libbcel-java libcommons-beanutils-java
  libcommons-collections-java libcommons-collections3-java libcommons-dbcp-java libcommons-digester-java
  libcommons-el-java libcommons-fileupload-java libcommons-launcher-java libcommons-logging-java
  libcommons-modeler-java libcommons-pool-java libgcj7-awt libjsch-java liblog4j1.2-java liblucene-java
  liblucene-java-doc libmx4j-java libregexp-java libservlet2.4-java libswt3.1-gtk-gcj libswt3.1-gtk-java
  libswt3.1-gtk-jni libtomcat5-java

``` 
I edited /etc/eclipse/java_home to include the path to my new java version.  Eclipse detects it, and correctly uses it after enabling it in Window>Preferences...>Java>Installed JREs.  Eclipse is much faster when using this version of java too.

But, I still get the wierd errors in the console tab; namely:```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
``` Also, it still starts a completely new instance of Eclipse when trying to run my program.

The program compiles fine.  No errors, no warnings.  This weird stuff happens at runtime.

Please, I'd like any help I can get on this issue.  After trying things for a few hours now, I can't think of anything else to do. :confused: :-x

Thanks much for any help! :)

nrwilk

---

### Post by hod139 on 2006-09-01
See if this howto helps: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

### Post by nrwilk on 2006-09-01
> **hod139 said:**
> See if this howto helps: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

No, that thread basically describes what I've already done.  I just did it the long way and installed the official sun package rather than the package in the repositories.

My Eclipse is using the official sun java 1.5.0_08.

Thank you for trying though.

---

### Post by mortsahl on 2006-09-01
Using Ubuntu Dapper ...

I didn't use the Eclipe version in the repostories but downloaded it and manually installed it (v3.2 -- Callisto) from the Eclipse site.  Installation was easy.  Just decompress then copy the Eclipse directory to where you want it to reside (if it wasn't decompressed there to begin with).

I'm using Sun's JDK and everything works as expected.

Good luck.

---

### Post by nrwilk on 2006-09-01
Ok, so I removed all eclipse packages from my system, and I installed Eclipse 3.2 from the Eclipse site.

I still am getting the *exact same results*.


This tells me that the problem is on my system.  Does Eclipse rely on a certain terminal?  Does it embed another terminal within itself?  Maybe I don't have the terminal program it needs installed?

Thanks for any help here.  I really want to use Eclipse in Linux, and not in Windows or on my Mac.

---

### Post by nrwilk on 2006-09-02
Alright, so I fixed it.

By issuing this command:```
sudo aptitude search eclipse
```I saw that several eclipse packages still had config files on my system.  So, I removed them by doing a ```
sudo aptitude purge ~neclipse
```

I then issued a```
slocate eclipse
```and deleted everything I could find that eclipse had created.  For some reason, the aptitude purge had NOT deleted my ~/.eclipse/ directory.

I then tried the version that I downloaded from the Eclipse website, and everything worked.

Many thanks to everyone who tried to help me. :D

nrwilk

---

