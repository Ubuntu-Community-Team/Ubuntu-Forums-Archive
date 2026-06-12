---
title: "Installing jdk"
date: 2007-11-19
forum: Programming Talk
---

### Post by dsh2va on 2007-11-19
Hi,

I'm new to linux so please be as specific as possible. I switched my Dell Inspiron 9400 from XP to gusty a week or so ago. I'm trying to set  up eclipse, I used synaptic to get j2sdk1.4. Everything seemed to install fine, but when I tried to run Eclipse, I get the following error:

JVM terminated. Exit code=1
/usr/lib/j2se/1.4/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 180017
-install /usr/lib/eclipse
-vm /usr/lib/j2se/1.4/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 

Any help would be much appreciated. 

Thanks, 
Dan

---

### Post by LaRoza on 2007-11-19
```

sudo aptitude install sun-java6-jdk

```

---

### Post by jespdj on 2007-11-20
Dan, you are using GNU Java. Eclipse doesn't work with GNU Java.
GNU Java is a slow and incomplete implementation of Java 1.4.
Install Sun Java instead with the command that LaRoza mentioned.

---

### Post by dsh2va on 2007-11-20
Thanks!! That worked great.

---

### Post by hod139 on 2007-11-20
> **LaRoza said:**
> ```

sudo aptitude install sun-java6-jdk

```

Installing sun's java isn't enough, you have to tell ubuntu to actually use it.
```

sudo update-java-alternatives -s java-6-sun

```

If you installed eclipse from the repository you still might have to do some tweaking: [http://ubuntuforums.org/showthread.php?t=201378](http://ubuntuforums.org/showthread.php?t=201378)

---

