---
title: "Java: a (what seems to be a) classpath issue in Ubuntu 10.04"
date: 2010-05-15
forum: Programming Talk
---

### Post by aske on 2010-05-15
Hello,

here is a "session" that describes what I am doing in my terminal, and you can find i think all the necessary information. I keep getting the same error: "package com.idrt does not exist" when compiling. This package is contained in the "AcceleGloveSDK.jar" file which is stored in a folder called classpath in my project folder, and the rest of the files are necessary for the application to run.

in mac and windows i did not have the same problem, setting the classpath was enough for the compiler to retrieve the .jar files..

```
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ java  -version
java version "1.6.0_18"

OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ echo  $CLASSPATH
/home/anthony/Dropbox/multimodal
project/code/classpath/AcceleGloveSDK.jar:/home/anthony/Dropbox/multimodal project/code/classpath/h2-1.1.115.jar:/home/anthony/Dropbox/multimodal
project/code/classpath/RXTXcomm.jar:/home/anthony/Dropbox/multimodal
project/code/classpath/librxtxSerial.so:/home/anthony/Dropbox/multimodal
project/code/classpath/AcceleGloveSDK-Linux.jar:/usr/lib/jvm/java-6-openjdk/jre/lib/:/usr/lib/jvm/java-6-openjdk/jre/lib/ext/
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ ls -l  classpath/
total 7992
-rwxrwxrwx 1 root    root    6762054 2010-05-12 00:11 AcceleGloveSDK.jar
-rwxrwxrwx 1 anthony anthony    3882 2009-05-14 20:40  AcceleGloveSDK-Linux.jar
-rwxrwxrwx 1 root    root    1175853 2010-05-12 00:11 h2-1.1.115.jar
-rwxrwxrwx 1 root    root     175806 2010-05-12 00:10 librxtxSerial.so
-rwxrwxrwx 1 root    root      60866 2010-05-12 00:11 RXTXcomm.jar
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ ls -l db/
DatabaseUtils.props
-rwxrwxrwx 1 anthony anthony   58 2009-05-14 02:54 DatabaseUtils.props

db/:
total 1156
-rwxrwxrwx 1 anthony anthony 131072 2009-05-22 17:56  AcceleGlove.1.log.db
-rwxrwxrwx 1 anthony anthony 131072 2010-05-10 15:34  AcceleGlove.26.log.db
-rwxrwxrwx 1 anthony anthony 663600 2009-05-22 17:56 AcceleGlove.data.db
-rwxrwxrwx 1 anthony anthony 131120 2009-05-22 17:56  AcceleGlove.index.db
drwxrwxrwx 2 anthony anthony   4096 2009-05-22 17:56 AcceleGlove.lobs.db
-rwxrwxrwx 1 anthony anthony 111540 2010-05-10 15:34  AcceleGlove.trace.db
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ ls -l  Example2.
Example2.class  Example2.java
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ ls -l  Example2.java
-rwxr-xr-x 1 anthony anthony 5145 2010-05-11 17:52 Example2.java
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ javac  Example2.java
Example2.java:2: package com.idrt does not exist
import com.idrt.Gesture;
               ^
Example2.java:3: package com.idrt does not exist
import com.idrt.GestureProbability;
               ^
Example2.java:4: package com.idrt does not exist
...
...

```yesterday I tried to compile setting the classpath in the command, like

```
javac -classpath "/home/anthony/Dropbox/multimodal  project/classpath/" Example2.java
```but still the same error appears..

today i tried this, again with no success:

```
javac -verbose -cp "/home/anthony/Dropbox/multimodal project/classpath/AcceleGloveSDK.jar" Example2.java
```i cannot solve this issue for more than four days now so i need some help..

thank you,
anthony

---

### Post by Some Penguin on 2010-05-15
I've usually seen classpaths be colon-delimited.

---

### Post by aske on 2010-05-15
> **Some Penguin said:**
> I've usually seen classpaths be colon-delimited.

uuuhm.. me too..

```
anthony@anthony-laptop:~/Dropbox/multimodal project/code$ echo  $CLASSPATH
/home/anthony/Dropbox/multimodal
project/code/classpath/AcceleGloveSDK.jar:/home/anthony/Dropbox/multimodal project/code/classpath/h2-1.1.115.jar:/home/anthony/Dropbox/multimodal
project/code/classpath/RXTXcomm.jar:/home/anthony/Dropbox/multimodal
project/code/classpath/librxtxSerial.so:/home/anthony/Dropbox/multimodal
project/code/classpath/AcceleGloveSDK-Linux.jar:/usr/lib/jvm/java-6-openjdk/jre/lib/:/usr/lib/jvm/java-6-openjdk/jre/lib/ext/

```...and there are colons, aren't there..?
i'm not sure if you mean something else

---

### Post by HotCupOfJava on 2010-05-15
He means when you put the arguments on the command-line, you use the colons as well:

```
javac -classpath "/home/anthony/Dropbox/multimodal:project/classpath/AcceleGloveSDK.jar" Example2.java
```

---

### Post by aske on 2010-05-15
> **HotCupOfJava said:**
> He means when you put the arguments on the command-line, you use the colons as well:

```
javac -classpath "/home/anthony/Dropbox/multimodal:project/classpath/AcceleGloveSDK.jar" Example2.java
```

the folder's name is "multimodal project", so this is no delimitation. i am just specifying one particular folder in the classpath.

---

### Post by Unterseeboot_234 on 2010-05-17
classpath multiples are semi-colons
```
C:> sdkTool -classpath classpath1;classpath2..
```

But, I have found greater flexibility using NetBeans and the include option to bring .jar files into a project. NetBeans manages all the classpath(s) needed to make a final distributed .jar.

---

### Post by mani10j on 2011-02-17
You might need to escape the space in the folder name since its a command line... that might be the reason

---

