---
title: "Eclipse and PHP"
date: 2007-08-13
forum: Programming Talk
---

### Post by Staach on 2007-08-13
I just got PHP working on Eclipse. Only thing I needed to change was the workspace to /var/www/ so that apache could interpret php. That gave me this crash:
[B]
JVM terminated. Exit code=1
/usr/lib/jvm/java-6-sun/bin/java
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar
-os linux
-ws gtk
-arch x86
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
-showsplash 600
-exitdata 127801c
-install /usr/lib/eclipse
-vm /usr/lib/jvm/java-6-sun/bin/java
-vmargs
-Djava.library.path=/usr/lib/jni
-Dgnu.gcj.precompiled.db.path=/var/lib/gcj-4.1/classmap.db
-Dgnu.gcj.runtime.VMClassLoader.library_control=never
-Dosgi.locking=none
-jar /usr/lib/eclipse/startup.jar [/B]

Every time I try to open a php file from Eclipse it gives me that crash. Can some one help out of this mess?

---

### Post by eclark on 2008-01-17
I've got the same problem, can anyone help? I've got the Sun version of Java installed, and eclipse came from the repositories (I think)

---

### Post by Compyx on 2008-01-17
I think your problem may lie in the fact that /var/www isn't owned by you. Changing the ownership of /var/www might 'solve' your problem but will have severe implications on security.

---

### Post by Sam on 2008-01-17
```
mkdir /var/www/workspace
chown user:user /var/www/workspace
ln -s /var/www/workspace /home/user/workspace
```
(of course replace 'user' with your username)

Now configure Eclipse to use /home/user/workspace as the workspace and access your work from [http://localhost/workspace/](http://localhost/workspace/)


Another way is creating Apache virtual hosts for every project you create in the workspace.
```
ServerName myproject.local
DocumentRoot /home/user/workspace/myproject
...
```
in /etc/apache2/sites-available/myproject


Ask if you want more explanation.

---

