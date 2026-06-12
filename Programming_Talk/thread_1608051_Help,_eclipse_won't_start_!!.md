---
title: "Help, eclipse won't start !!"
date: 2010-10-28
forum: Programming Talk
---

### Post by amityak on 2010-10-28
Hello Everyone !!

I've downloaded eclipse helios from eclipse, this file: eclipse-jee-helios-linux-gtk.tar.gz. The reason i didnt apt-get it is because of the WDT (Web Development Tools) which are not available in the repository version (or tell me please if im wrong)

well saying ./eclipse just don't do anything (starts 4 processes which abort quite fast)

saying ./eclipse -debug give following :

```
amit@amit-desktop:~/app/eclipse$ ./eclipse -debug
Start VM: /usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
-jar /home/amit/app/eclipse/plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/amit/app/eclipse/eclipse
-name Eclipse
--launcher.library /home/amit/app/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.1.0.v20100503/eclipse_1307.so
-startup /home/amit/app/eclipse/plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar
-exitdata 21801a
-product org.eclipse.epp.package.jee.product
-debug
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-XX:MaxPermSize=256m
-Xms40m
-Xmx512m
-jar /home/amit/app/eclipse/plugins/org.eclipse.equinox.launcher_1.1.0.v20100507.jar 
Install location:
    file:/home/amit/app/eclipse/
Configuration file:
    file:/home/amit/app/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/amit/app/eclipse/configuration/
Framework located:
    file:/home/amit/app/eclipse/plugins/org.eclipse.osgi_3.6.0.v20100517.jar
Framework classpath:
    file:/home/amit/app/eclipse/plugins/org.eclipse.osgi_3.6.0.v20100517.jar
Splash location:
    /home/amit/app/eclipse/plugins/org.eclipse.platform_3.6.0.v201006080911/splash.bmp
Debug options:
    file:/home/amit/app/eclipse/.options not found
Time to load bundles: 38
Starting application: 5530
amit@amit-desktop:~/app/eclipse$ 

```

comparing to another computer it's a similar output just went on, but here no splash screen, no gui, nothin !!

any ideas?

im running 10.4 64bit
Thanks !

---

### Post by r-senior on 2010-10-28
> The reason i didnt apt-get it is because of the WDT (Web Development Tools) which are not available in the repository version (or tell me please if im wrong)
I don't think they come by default but you can download the plugins from within Eclipse. I'm using Eclipse with the web tools stuff from the 10.04 repository version on 64-bit.

Does Eclipse create a workspace directory? Have you tried looking for log files in the .metadata sub-directory?

Only other suggestion I would have before giving up would be to try using the Sun JDK.

---

### Post by amityak on 2010-10-28
Cheers for the screenshot !
I'm giving it another shot even though i remember grabbing that plugin went wrong last time i tried it the other day. I'm trying it now and i hope it works. I'll update soon

---

### Post by mainerror on 2010-10-28
What Java version are you using? OpenJDK or Sun JDK and have you checked the file/directory permissions?

---

### Post by amityak on 2010-10-28
@r-señor (:   :   Well i did managed to install the plugins now, it's funny how it didnt work last time, but it seems right. i'm currently working on something else so i won't test it this evening but later. Thank you !!


... but i still don't get it why helios refuses to work ?!?!?


@mainerror (like yer' nick !): 

```

amit@amit-desktop:~/app/eclipse$ java -version
java version "1.6.0_22"
Java(TM) SE Runtime Environment (build 1.6.0_22-b04)
Java HotSpot(TM) 64-Bit Server VM (build 17.1-b03, mixed mode)
amit@amit-desktop:~/app/eclipse$ javac -version
javac 1.6.0_22

```

and also saying
```

amit@amit-desktop:~/app$ chown amit -R eclipse

```

and then trying again didn't change anything ):

Thank you both guys !!

---

### Post by why2jjj on 2011-12-08
Was there a solution to this problem?  I have the same issue: 

1. Running 64-bit Ubuntu 10.04 LTS
2. Have java version:

java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

3. This is what happens when I type 'eclipse debug': 

jpfreyen@poundcake:~$ eclipse -debug
Start VM: /usr/bin/java
-Xms128m
-Xmx512m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
-XX:MaxPermSize=256m
-jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
-os linux
-ws gtk
-arch x86_64
-showsplash
-launcher /usr/lib/eclipse/eclipse
-name Eclipse
--launcher.library /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.200.v20090519/eclipse_1208.so
-startup /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar
-exitdata 14801f
-debug
-vm /usr/bin/java
-vmargs
-Xms128m
-Xmx512m
-Dorg.eclipse.equinox.p2.reconciler.dropins.directory=/usr/share/eclipse/dropins
-XX:MaxPermSize=256m
-jar /usr/lib/eclipse//plugins/org.eclipse.equinox.launcher_1.0.201.R35x_v20090715.jar 
Install location:
    file:/usr/lib/eclipse/
Configuration file:
    file:/usr/lib/eclipse/configuration/config.ini loaded
Configuration location:
    file:/home/jpfreyen/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/
Configuration file:
    file:/home/jpfreyen/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/config.ini loaded
Shared configuration location:
    file:/usr/lib/eclipse/configuration/
Framework located:
    file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.5.2.R35x_v20100126.jar
Framework classpath:
    file:/usr/lib/eclipse/plugins/org.eclipse.osgi_3.5.2.R35x_v20100126.jar
Splash location:
    /usr/lib/eclipse/plugins/org.eclipse.platform_3.3.202.v201002111343/splash.bmp
Debug options:
    file:/home/jpfreyen/.options not found
Time to load bundles: 4
Starting application: 467

---

### Post by amityak on 2011-12-08
not that I remember, sorry ... but it has been a while. In the meantime I've discovered IntelliJ and happy ever since (:

Good luck !

---

