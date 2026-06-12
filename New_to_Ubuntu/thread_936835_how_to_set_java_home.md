---
title: "how to set java home"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by deembee on 2008-10-03
Hi I have installed musicip and it tells me i have to set java home

i have looked at this thread
 [http://ubuntuforums.org/showthread.php?t=593033](http://ubuntuforums.org/showthread.php?t=593033)
which covers the software but as a complete beginner i have no idea what the java home setting is. Is it some sort of text file that has to be set? Any help would be appreciated thanks.

---

### Post by klytu on 2008-10-03
> **deembee said:**
> Hi I have installed musicip and it tells me i have to set java home

i have looked at this thread
 [http://ubuntuforums.org/showthread.php?t=593033](http://ubuntuforums.org/showthread.php?t=593033)
which covers the software but as a complete beginner i have no idea what the java home setting is. Is it some sort of text file that has to be set? Any help would be appreciated thanks.

In that thread JAVA_HOME is a system environment variable which points to the directory where your java virtual machine files are located on your system.

Do you know what version of java you have installed? If not open up a terminal window by going to Applications>Accessories>Terminal. Then type or cut and paste the command below into the terminal window. ```
java -version
``` Post back the result and we'll try to help.

---

### Post by abhishek.malhotra35 on 2008-10-03
from terminal type: set PATH=$(path where you have installed java)/bin;
set CLASSPATH=$(path where you have installed java)/lib;
then start your tool from commandline by typing its name. Most probably should be musicip. It will start.

---

### Post by SupaSonic on 2008-10-03
> **abhishek.malhotra35 said:**
> from terminal type: set PATH=$(path where you have installed java)/bin;
set CLASSPATH=$(path where you have installed java)/lib;
then start your tool from commandline by typing its name. Most probably should be musicip. It will start.

If he has java installed from the repositories, PATH and CLASSPATH are already set. He needs to set JAVA_HOME.

As already mentioned, please paste the output of
```
java -version
```
and 
```
whereis java
```

---

### Post by abhishek.malhotra35 on 2008-10-04
not necessary that path and classpath are set. The question above doesn't specify that path are classpath are set. Instead of confusing the person posting the question, try to solve it. To set Java_home type whereis java. Once u find the path, set the path: set JAVA_HOME=(path you found above).

---

### Post by porchrat on 2008-10-04
Why can't you use this:

```
sudo update-alternatives --config java
```

Works for me...sets all the links automatically.

Then if you need to change the compiler just do:

```
sudo update-alternatives --config javac
```

---

### Post by vintermann on 2010-04-03
When I install java-6-sun from the repository, and run update-java-alternatives to use it, why doesn't it set $JAVA_HOME or $CLASSPATH ? 
I can set them manually, of course, but I like the package system to keep track of as much as possible for me, to make updates less of a hassle.

---

### Post by SwaroopKunduru on 2010-04-13
> sudo update-alternatives --config javac
update-alternatives: error: no alternatives for javac.

This was my problem I installed java6. 

When I give which javac nothing come up.

Regards,

Swaroop Kunduru.

---

