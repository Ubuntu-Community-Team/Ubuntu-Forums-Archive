---
title: "Trying to help x64 bit users with java instructions"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by zanecannon on 2012-03-25
My first time posting.  I am a Ubuntu 64-bit user and tried following these instructions to manually installing java.

[https://help.ubuntu.com/community/Java#Manual_method](https://help.ubuntu.com/community/Java#Manual_method)


Where the command line seemed to honor the 32-bit java for compiling/running classes, whenever I would try to load a java applet my FireFox would crash.  After some amount of investigation and tinkering I figured out that the above instructions were to get the 32-bit version of java.

I wanted desperately to contribute my findings so that someone else behind me didn't suffer the same problems, but after going through a complicated set up process for SSO to edit the above manual java installation documentation, I don't seem to have been given any ability to do so.

So to anyone else who might have the ability/know-how here is what I wanted to contribute.



**Manual method**



Do-it-yourself method, but very easy to apply (basically: you copy/paste some terminal commands). 

[LIST]
[*]oracle java 6 32-bit jre 
[/LIST]

 $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-i586.bin)  $ chmod u+x jre-6u31-linux-i586.bin  $ ./jre-6u31-linux-i586.bin  $ mv jre1.6.0_31 /usr/lib/jvm/  $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_31/bin/java" 1  $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jre1.6.0_31/lib/i386/libnpjp2.so" 1or 

[LIST]
[*]oracle java 6 32-bit jdk 
[/LIST]

 $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jdk-6u31-linux-i586.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jdk-6u31-linux-i586.bin)  $ chmod u+x jdk-6u31-linux-i586.bin  $ ./jdk-6u31-linux-i586.bin  $ mv jdk1.6.0_31 /usr/lib/jvm/  $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0_31/bin/java" 1  $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jdk1.6.0_31/jre/lib/i386/libnpjp2.so" 1 

[LIST]
[*]oracle java 6 64-bit jre 
[/LIST]
 
  $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-x64.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jre-6u31-linux-x64.bin)  $ chmod u+x jre-6u31-linux-x64.bin  $ ./jre-6u31-linux-x64.bin  $ mv jre1.6.0_31 /usr/lib/jvm/  $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jre1.6.0_31/bin/java" 1  $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jre1.6.0_31/lib/amd64/libnpjp2.so" 1  or 
 
[LIST]
[*]oracle java 6 64-bit jdk 
[/LIST]
 
  $ wget [http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jdk-6u31-linux-x64.bin](http://download.oracle.com/otn-pub/java/jdk/6u31-b04/jdk-6u31-linux-x64.bin)  $ chmod u+x jdk-6u31-linux-x64.bin  $ ./jdk-6u31-linux-x64.bin  $ mv jdk1.6.0_31 /usr/lib/jvm/  $ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/jdk1.6.0_31/bin/java" 1  $ sudo update-alternatives --install "/usr/lib/mozilla/plugins/libjavaplugin.so" "mozilla-javaplugin.so" "/usr/lib/jvm/jdk1.6.0_31/jre/lib/amd64/libnpjp2.so" 1

---

