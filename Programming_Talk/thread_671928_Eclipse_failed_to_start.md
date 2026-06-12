---
title: "Eclipse failed to start"
date: 2008-01-19
forum: Programming Talk
---

### Post by arnab.here on 2008-01-19
Hi,

I have installed ubuntu builds of Eclipse and JDK(Sun). When I launch eclipse I am getting the following message:



JVM terminated. Exit code=1
/usr/lib/jvm/java-6-sun/bin/java
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
-exitdata d60020
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.2/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar 


I tried to Google it for sometime without any success. Please can anyone tell me the solution and the root cause....
Thanks in advance....

---

### Post by yu_raider on 2008-01-19
Same here...

---

### Post by Jessehk on 2008-01-19
I'm guessing, but it might be this bug: [https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/183969)

---

### Post by arnab.here on 2008-01-20
The following code in my

~/.bashrc file did the trick for me

[ -d ~/bin ] && [ "${PATH/$HOME\/bin/}" = "${PATH}" ] && export PATH="$HOME/bin:$PATH"

---

