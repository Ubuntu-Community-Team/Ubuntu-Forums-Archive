---
title: "Eclipse crashses"
date: 2007-09-13
forum: Programming Talk
---

### Post by Masterslave on 2007-09-13
Hello all,

I've a problem when I'm using Eclipse for a several minutes it crashes.
And I get the following error (see attachement).

I'm using Gusty Gibbon.
I've installed java 6.

/etc/jvm
```

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

```

I've run:
```

sudo update-java-alternatives -s java-6-sun

```

/etc/eclipse/java_home
```

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/kaffe/pthreads
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/j2se/1.5
/usr/lib/j2se/1.4
/usr/lib/j2sdk1.5-ibm
/usr/lib/j2sdk1.4-ibm
/usr/lib/j2sdk1.5-sun
/usr/lib/j2sdk1.4-sun

```

I've also read somewhere that I have to delete the .metadata in the root of the workspace, but it didn't help.

also I tried this:
Delete these 2 files and start eclipse. That works :-)
\.metadata\.plugins\org.eclipse.core.resources\.snap
and
\.metadata\.plugins\org.eclipse.core.resources\.root\.markers.snap

Can anybody help me?

---

### Post by aitorcalero on 2007-09-13
It is possible that your eclipse run out of virtual memory. Try to increase it with this:
```

%ECLIPSE_PATH%/eclipse -vmargs -Xms128m -Xmx512m -XX:PermSize=64M -XX:MaxPermSize=128M

```

---

### Post by Masterslave on 2007-09-13
Uh, how do I increase that? Via the terminal with your code you just gave?

---

### Post by m0eman on 2007-09-13
did you install from the repos or from the package on eclipse's site? I've always found the the eclipse in the repository doesn't work very well.

---

### Post by Masterslave on 2007-09-13
I've download it from the repos, when I'm home I'll download it from the eclipse site.
The /etc/eclipse/java_home should stay on my file system?

---

### Post by m0eman on 2007-09-13
I don't have it in that folder nor my eclipse folder, maybe just keep it as backup in case you need it later on.

---

### Post by aitorcalero on 2007-09-13
> **Masterslave said:**
> Uh, how do I increase that? Via the terminal with your code you just gave?

Yes, you only need to put this in a terminal (with your correct path to eclipse executable). Then if it works for you, you could create a launcher with this line.

---

### Post by Masterslave on 2007-09-13
Seems to be working.
I've deleted the "Ubuntu" Eclipse and download the package and installed.
Haven't crashed...yet ;-)
Next Thursday I'm working with Java again for a couple of hours, then I can see if it really works.

---

### Post by oneiota on 2007-09-14
I'd like to do the same and install eclipse 3.3 from eclipse directly.  Can you tell me how you did it?  By simply untarring the archive in /etc using sudo?

---

### Post by spamalot on 2007-09-14
hi,

eclipse cdt also crashes (recently).

i switched from 
/usr/lib/jvm/java-gcj/jre/bin/java  to /usr/lib/jvm/java-6-sun/jre/bin/java but w/o sucess.

i've noticed eclipse 3.3 now avail for windows only?

---

### Post by spamalot on 2007-09-14
ok, it's avail not just for win. i just encountered a temp pb. i believe that's the download for eclipse/cdt/linux?

[http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20070702/eclipse-cpp-europa-linux-gtk.tar.gz&r=1&protocol=http](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/20070702/eclipse-cpp-europa-linux-gtk.tar.gz&r=1&protocol=http)

a) i don't see any intall intructions for cdt in the tar package.
b) do i have to install eclipse classic on top of that?

---

### Post by spamalot on 2007-09-14
maybe like this?

[http://www.iram.fr/~roche/linux/softwares/softwares_LocalInstallation.html](http://www.iram.fr/~roche/linux/softwares/softwares_LocalInstallation.html)

---

### Post by spamalot on 2007-09-14
well i tried...

eclipse: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

how do i resolve this linking pb? pls help.

---

### Post by spamalot on 2007-09-14
ok i wasn't aware of 

[https://help.ubuntu.com/community/EclipseIDE](https://help.ubuntu.com/community/EclipseIDE)

so let me look into this 1st...

---

### Post by spamalot on 2007-09-14
to sum up: installing from zip file did not work for me so i reinstalled both eclipse and cdt using the package manager. 

cdt still crashes. i made sure /usr/lib/jvm/java-6-sun/jre/bin/java is the default in the system and at the top of eclipse/have_home

still it crashes when i try to build a project. from the message below it appears the change above did not take effect. so i checked in java_home and java-6-sun is at the top...

JVM terminated. Exit code=1
/usr/lib/jvm/java-gcj/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86_64
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 3c0014
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-gcj/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar

---

### Post by spamalot on 2007-09-14
misc question: what does + mean?

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
 +        2    /usr/lib/jvm/java-gcj/jre/bin/java
*         3    /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by spamalot on 2007-09-14
/usr/lib/jvm/java-1.5.0-sun

(not java-6) worked, finally, and is also faster.

---

### Post by Masterslave on 2007-09-17
> **oneiota said:**
> I'd like to do the same and install eclipse 3.3 from eclipse directly.  Can you tell me how you did it?  By simply untarring the archive in /etc using sudo?Sorry, fot my late respons.
I've removed Eclipse by using sudo apt-get remove eclipse.
Then I download it form the eclipse site and extract it to my /opt directory.
[http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/eclipse-SDK-3.3-linux-gtk.tar.gz](http://download.eclipse.org/eclipse/downloads/drops/R-3.3-200706251500/eclipse-SDK-3.3-linux-gtk.tar.gz)

Thursday I'm working with Eclipse again so I will post if it crashed then that day.

---

### Post by kzimir on 2007-09-20
i can confirm eclispe being unstable.

- i also use java6 as vm. 
- i work a lot on webprojects  (WST and PDT) and it even crashes on html files
- increase of the MaPermSize didnt helped
- reinstall didnte helped 
- update plugins didnt helped
- i am busy to kick out plugins one by one.

if anybody has a smart answer on this.. i am curious

---

