---
title: "Java installed, command not working"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by CraftyMarmoset on 2011-10-12
Hey, I've had java working on my computer for a while now, but I tried to switch from the OpenJDK JRE to Oracle Java, completely failed and so I uninstalled java and tried to reinstall it, however, even though it appears as installed on the software manager, and attempting "sudo apt-get install openjdk-7-jre" claims it is installed, using any java command, such at "java -version" produces the following:

```

thomas@Aspire-5315:~$ sudo apt-get install openjdk-7-jre
[sudo] password for thomas: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openjdk-7-jre is already the newest version.
openjdk-7-jre set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 575 not upgraded.
thomas@Aspire-5315:~$ java -version
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
thomas@Aspire-5315:~$ 

```

I've tried installing the openjdk packages cited by the terminal, but they're both apparently already installed.

Can anyone help? It would be much appreciated :)

EDIT: If it helps, I'm on 11.10 Oneiric Ocelot, the most recent beta as far as I know.

---

### Post by 11jmb on 2011-10-12
JDK 7 is not available in the Ubuntu repositories yet. You can download the linux binaries from the Oracle website and configure java yourself if you want

---

### Post by CraftyMarmoset on 2011-10-12
Well I had OpenJDK 7 installed and working perfectly fine before, and I had done nothing different, so I'm very confused...

---

### Post by 11jmb on 2011-10-12
search "openjdk" in synaptic whatever version listed will be the same that apt-get will search for.

I don't know for sure, but there's a good chance that 11.10 comes with java 7 binaries, even though the most recent jdk in the ubuntu repos is jdk6

---

### Post by CraftyMarmoset on 2011-10-12
Ok, I think there may be an issue here, after opening Synaptic, it crashed almost straight away, so I tried to report the problem but apparently I need to upgrade various packages so I'm doing that now, then I'll see what happens.

---

### Post by 11jmb on 2011-10-12
Its likely that there is some form of java depency that is killing synaptic. perhaps you should try to use apt-get to re-install the older version of openjdk for the time being

---

### Post by CraftyMarmoset on 2011-10-12
I may have to - I'll let apt-get upgrade finish doing its thing, and if it doesn't help, I'll try reverting to Java 6. Thanks anyway :)

---

### Post by 11jmb on 2011-10-12
post your results here, success or failure. If you have more problems, there are plenty of people who would love to help. If everything works, you can let everyone know that you don;t need any more help

---

### Post by CraftyMarmoset on 2011-10-12
Ok so I let the apt-get upgrade finish, no luck there, and I found that OpenJDK 6 was already installed, so I decided to uninstall all the java again, and try once more - this was the result:

```

thomas@Aspire-5315:~$ sudo apt-get remove openjdk-7-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-11 linux-headers-3.0.0-11-generic esound-common libesd0
  libxt-dev libaudiofile0 wine1.2-gecko
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  openjdk-7-jdk openjdk-7-jre
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 37.8 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 251991 files and directories currently installed.)
Removing openjdk-7-jdk ...
Removing openjdk-7-jre ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
thomas@Aspire-5315:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  esound-common libaudiofile0 libesd0 libxt-dev linux-headers-3.0.0-11
  linux-headers-3.0.0-11-generic wine1.2-gecko
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
After this operation, 108 MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 251835 files and directories currently installed.)
Removing libesd0 ...
Removing esound-common ...
Removing libaudiofile0 ...
Removing libxt-dev ...
Removing linux-headers-3.0.0-11-generic ...
Removing linux-headers-3.0.0-11 ...
Removing wine1.2-gecko ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
thomas@Aspire-5315:~$ sudo apt-get remove openjdk-6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  default-jre icedtea-netx libaccess-bridge-java libaccess-bridge-java-jni
  openjdk-6-jre
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 2,085 kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 229902 files and directories currently installed.)
Removing icedtea-netx ...
Removing default-jre ...
Removing openjdk-6-jre ...
update-alternatives: warning: alternative /usr/lib/jvm/java-7-openjdk-i386/bin/policytool (part of link group policytool) doesn't exist. Removing from list of alternatives.
update-alternatives: warning: /etc/alternatives/policytool is dangling, it will be updated with best choice.
Removing libaccess-bridge-java-jni ...
Removing libaccess-bridge-java ...
Processing triggers for man-db ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
thomas@Aspire-5315:~$ sudo apt-get install openjdk-6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  icedtea-netx libaccess-bridge-java libaccess-bridge-java-jni
Suggested packages:
  icedtea-plugin
The following NEW packages will be installed
  icedtea-netx libaccess-bridge-java libaccess-bridge-java-jni openjdk-6-jre
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,110 kB of archives.
After this operation, 2,064 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package libaccess-bridge-java-jni.
(Reading database ... 229840 files and directories currently installed.)
Unpacking libaccess-bridge-java-jni (from .../libaccess-bridge-java-jni_1.26.2-6_i386.deb) ...
Selecting previously deselected package openjdk-6-jre.
Unpacking openjdk-6-jre (from .../openjdk-6-jre_6b23~pre10-0ubuntu5_i386.deb) ...
Selecting previously deselected package libaccess-bridge-java.
Unpacking libaccess-bridge-java (from .../libaccess-bridge-java_1.26.2-6_all.deb) ...
Selecting previously deselected package icedtea-netx.
Unpacking icedtea-netx (from .../icedtea-netx_1.1.3-1ubuntu1_i386.deb) ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up libaccess-bridge-java (1.26.2-6) ...
Setting up libaccess-bridge-java-jni (1.26.2-6) ...
Setting up openjdk-6-jre (6b23~pre10-0ubuntu5) ...
Setting up icedtea-netx (1.1.3-1ubuntu1) ...
update-alternatives: using /usr/lib/jvm/java-6-openjdk/jre/bin/javaws to provide /usr/bin/javaws (javaws) in auto mode.
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
thomas@Aspire-5315:~$ java
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
thomas@Aspire-5315:~$ 

```

Any other ideas? :(

---

### Post by CraftyMarmoset on 2011-10-12
Nothing at all?

---

### Post by Lisiano on 2011-10-12
I have an idea.
Could you try doing this?
```
cd /usr/lib/jvm/java-7-openjdk/bin
./java -version
```
I'm on 11.04 thus on v6 so if there is no java-7-openjdk, try looking around in /usr/lib/jvm for reference to it.

EDIT: If you have v6 installed, just go to java-6-openjdk instead of 7.

---

### Post by CraftyMarmoset on 2011-10-12
Now that did work, but only for the java 6:

```

thomas@Aspire-5315:/usr/lib/jvm/java-6-openjdk/bin$ ./java -version
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre10-0ubuntu5)
OpenJDK Client VM (build 20.0-b11, mixed mode, sharing)
thomas@Aspire-5315:/usr/lib/jvm/java-6-openjdk/bin$ cd
thomas@Aspire-5315:~$ java
The program 'java' can be found in the following packages:
 * gcj-4.4-jre-headless
 * gcj-4.6-jre-headless
 * openjdk-6-jre-headless
 * gcj-4.5-jre-headless
 * openjdk-7-jre-headless
Try: sudo apt-get install <selected package>
thomas@Aspire-5315:~$ 

```

So it appear that it IS installed, but it isn't being picked up outside of the folder it's in... and the Java 7 folder only appears to have a Policy tool of some sort whenever I apt-get it.

What next?

EDIT: The Java 7 folder also has a different title format - java-7-openjdk-i386, which seems a little odd...

---

### Post by Lisiano on 2011-10-12
i386 is the CPU architecture, just means you are using 32-bit.

It seems that the executables are not getting linked to their respective folders. Until 11.10 is released (I think they will fix it by then), I suggest adding an alias to java in your .bash_aliases
```
alias java="/usr/lib/jvm/java-6-openjdk/bin/java"
```
Reopen your terminal and you should be able to call java within it, if you need any other java executable, just find it in the directory and do the same as we did for java.
Note this is just a kludge since I don't know how to use alternatives good enough to add java into it.

---

### Post by CraftyMarmoset on 2011-10-12
Aha, that has worked :) Thanks a lot :P I wonder why it stopped working normally though, but this will do! Have a gold :KS

---

