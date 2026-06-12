---
title: "Firefox 3.0 not recognizing Java Runtime Environment"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by TMcKSmith on 2008-08-01
I'm using Firefox 3.0 on Hardy, and it doesn't seem to be recognizing my JRE.  Here's the ouput of java -version:

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Server VM (build 10.0-b22, mixed mode)


When I point my browser to about:plugins, no JRE exists.  

Any help would be appreciated.

---

### Post by raptor2552 on 2008-08-01
Hello

There is a more up to date Java available from Sun (update 7) if your care to first get that. There is also a How To here:[http://ubuntuforums.org/showthread.php?t=876209](http://ubuntuforums.org/showthread.php?t=876209)

But if you'd like to try this:

First open a terminal and type: **which java**
which should output something like: **/usr/bin/java**
which will show you what java you're trying to execute
next we'll take that output and use it to find the directory java is actually in so type: **ls -l /usr/bin/java**
which should show something like:**lrwxrwxrwx 1 root root 33 2008-07-31 19:28 /etc/alternatives/java -> /usr/lib/jvm/jre1.6.0_07/bin/java**
the very first character in the output (l) shows us that this is a link to the real executable where (**/usr/lib/jvm/jre1.6.0_07/bin/java**) lives. Links are used to help us from having executables all over the place

next we're going to go to the directory where firefox looks for it's plugins, type: **cd /usr/lib/firefox-addons/plugins**

and the moment of truth, we're going to create our own link to the java plugin, type:
**sudo ln -s /usr/lib/jvm/jre1.6.0_07/plugin/i386/ns7/libjavaplugin_oji.so .**

Note; be sure to substitute your paths for those shown here. If you download and install Java 6 update 7 these should work for you. Be sure to close and start firefox

---

### Post by TMcKSmith on 2008-08-01
I just installed java-6-plugin from the repository and now it's working fine.  Thanks.

---

### Post by gandaran on 2008-08-01
edit

---

