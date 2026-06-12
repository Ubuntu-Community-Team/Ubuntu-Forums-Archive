---
title: "Sun WTK 2.5.2 installing problem"
date: 2009-02-01
forum: Programming Talk
---

### Post by potzdonner on 2009-02-01
Dear all

I think this is rather a permission than a Sun WTK 2.5.2 problem, that's why I'm asking here in this forum. Here is my problem: I try to install Sun WTK 2.5.2 on my Ubuntu/8.04 (hardy) machine executing the following file as root 

-rwxr-xr-x 1 root   root   39797585 2009-01-31 17:54 sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh

The shell try to untar in /usr/lib/jvm/java-6-sun/jre/bin/jar, which has the following permissions

drwxrwxrwx 2 root root 4096 2009-01-31 18:09 jar

The result is

../Desktop/sun_java_wireless_toolkit-2.5.2_01-linuxi486.bin.sh: 466: /usr/lib/jvm/java-6-sun/jre/bin/jar: Permission denied
Failed to extract files. Installation will stop now.

I can't find the cause of the problem. The target directory has full write-persmissions. Any suggestions?

---

