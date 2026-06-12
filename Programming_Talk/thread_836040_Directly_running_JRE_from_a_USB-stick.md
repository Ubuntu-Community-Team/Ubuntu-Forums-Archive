---
title: "Directly running JRE from a USB-stick"
date: 2008-06-21
forum: Programming Talk
---

### Post by vbtricks on 2008-06-21
Salut,

in order to get my Java application running on any Linux pc without having to install the JRE, I'm trying to integrate the JRE into the USB-stick.

I therefore downloaded the self-extracting file from java.com and extracted it. The first try starting it directly using

```
cd /path/to/java
./java -jar /some/other/path/app.jar
```

resulted in an error message

```
./java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
```

So I added the direct path of the libjli.so to LD_LIBRARY_PATH and tried again. So I got another error message

```
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.
```

As this error message looks different to the first one, I doubted that adding the direct path of libjava.so to LD_LIBRARY_PATH would work and trying to confirmed by suspicion.

Did any of you succeed getting the JRE to run without install, and if how?


Thanks in advance,

Stefan

---

### Post by xlinuks on 2008-06-21
I haven't tried yet (but I guess I'll try soon), I would suggest creating a softlink to the java executable and putting it into the folder where the .jar app lies. Then do "./java app.jar" and see whether this works. Haven't tested but might work.

---

### Post by xlinuks on 2008-06-21
Well I actually tried and succeeded.
I tested it on a computer that doesn't have Java installed.
I created a symbolic link in the dir where the .jar app lies and created an .sh script to runs that file. The contents of the sh file is this (my test java app is called Signer.jar:
```

#!/bin/sh

./java -jar Signer.jar

```
The screenshot is attached.

PS: you will need to format the USB stick to Ext3 since Fat32 doesn't support symbolic links.

---

### Post by vbtricks on 2008-06-21
Thanks, works perfectly.

---

### Post by xlinuks on 2008-06-21
You're welcome :)

---

### Post by aMeR1CaN_aUsSie on 2008-06-23
I found a simpler solution:

```
ln -s / /cow
```

For more information go to my tutorial here:

[http://ubuntuforums.org/showthread.php?t=829866]("http://ubuntuforums.org/showthread.php?t=829866")

Enjoy.

aMeR1CaN_aUsSiE

---

### Post by vbtricks on 2008-06-23
Well, in fact it's even easier. My problem was that I switched to the directory of the java and then called 
```
./java -jar /complete/path/to/my.jar
```
Instead I only needed to switch to the directory of the .jar file and the call
```
relative/path/to/java -jar my.jar
```

---

### Post by An85Zk9tc8rfjV8i on 2009-05-13
> **xlinuks said:**
> You're welcome :)
__________________
62°23&#8242;30&#8243;N 145°09&#8242;0&#8243;W
&#1105;&#1105;&#1084;&#1072;&#1105;&#1105;.. 


:popcorn:

[High Frequency Active Auroral Research Program - Wikipedia]("http://en.wikipedia.org/wiki/High_Frequency_Active_Auroral_Research_Program")

[GeoHack - High Frequency Active Auroral Research Program]("http://stable.toolserver.org/geohack/geohack.php?pagename=High_Frequency_Active_Auroral_Research_Program&params=62_23_30_N_145_09_03_W_")

:popcorn:

---

