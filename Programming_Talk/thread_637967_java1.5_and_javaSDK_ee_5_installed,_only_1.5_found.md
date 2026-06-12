---
title: "java1.5 and javaSDK ee 5 installed, only 1.5 found by system"
date: 2007-12-11
forum: Programming Talk
---

### Post by cuco2772 on 2007-12-11
This is a real bugger of a problem, here's what I've done to try to
fix it:

I have java version "1.5.0_11", I cant compile servlets so I installed
this one, the SDK with JDK : java_ee_sdk-5_03-linux.bin, in /opt/SDK/jdk
Problem is, if I do javac, it only finds the 1.5 version, so I cant compile servlets. I've reset $JAVA_HOME to /opt/SDK/jdk, doesnt help.

I tried doing this from a java package, using fakeroot, here's what
happened:

cuco@coat:~/Desktop$ fakeroot make-jpkg java_ee_sdk-5_03-linux.bin
Creating temporary directory: /tmp/make-jpkg.WOrlLt6874
Loading plugins: blackdown-j2re.sh blackdown-j2sdk.sh common.sh ibm-j2re.sh ibm-j2sdk.sh j2re.sh j2sdk-doc.sh j2sdk.sh j2se.sh sun-j2re.sh sun-j2sdk-doc.sh sun-j2sdk.sh

Detected Debian build architecture: i386
Detected Debian GNU type: i486-linux-gnu

No matching plugin was found.
Removing temporary directory: done

I'm about ready to give up at this point, any ideas on what to try ?
update-alterenatives doesnt find the right java either

---

### Post by geirha on 2007-12-11
whichever java is first in the path is the one it will use, so try 
```
export PATH="/opt/SDK/jdk/bin:$PATH"
export JAVA_HOME="/opt/SDK/jdk"
```

and ```
type -a java
``` will show all java-binaries in the path. The first one it lists is the one it uses when you type "java"

---

### Post by cuco2772 on 2007-12-11
Where should I add that,  .bashrc (or bash.bashrc) or in
/etc/environment ?
Yesterday I added $JAVA_HOME to the path, ie path=$JAVA_HOME:$path, 
something like that where I had $JAVA_HOME first,  and really screwed my bash shell to the point where it couldn't find any programs, ie ls, vim, nothing. Luckily I had more than one terminal open so I was able
to edit my .bashrc for root user in another terminal and save myself a major hassle. Not sure I want to go down that road again !

---

### Post by cuco2772 on 2007-12-11
I just did the type -a java and got this:

root@coati:/opt/SDK/jdk# type -a java
java is /usr/bin/java
java is /usr/bin/X11/java
java is /opt/SDK/jdk/bin/java
java is /opt/SDK/jdk/jre/bin/java
java is /opt/SDK/jdk/bin/java
java is /opt/SDK/jdk/jre/bin/java

So it looks like my problem had nothing to do with that. Thanks, anyway.

---

