---
title: "[SOLVED] Help With Java &amp;amp; Eclipse"
date: 2008-06-22
forum: Programming Talk
---

### Post by Natilator3 on 2008-06-22
I've downloaded sun's jdk1.5.0 and eclipse and both I'm SHURE are the right version for my system (I'm running Hardy). But when I try to run eclipse i get this error message:

A Java Runtime Environment (JRE) or Java Development Kit (JDK)
must be available in order to run Eclipse. No Java virtual machine
was found after searching the following locations:
/home/nate/Desktop/eclipse/jre/bin/java
java in your current PATH

what? there is no jre folder in the eclipse folder, i look in jdk1.5.0_15 and there's /jre/bin/java, so i copy and paste the folder into eclipse's folder and i get this error message:

JVM terminated. Exit code=13
/home/nate/Desktop/eclipse/jre/bin/java
-Xms40m
-Xmx256m
-jar /home/nate/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-os linux
-ws gtk
-arch x86_64
-showsplash
-launcher /home/nate/Desktop/eclipse/eclipse
-name Eclipse
--launcher.library /home/nate/Desktop/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_64_1.0.3.R33x_v20080118/eclipse_1023.so
-startup /home/nate/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar
-exitdata c800c
-vm /home/nate/Desktop/eclipse/jre/bin/java
-vmargs
-Xms40m
-Xmx256m
-jar /home/nate/Desktop/eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20080118.jar

quite frankly I'm clueless(:confused:)

---

### Post by Can+~ on 2008-06-22
Are you installing from the webpage or from repository?

like, you know, [FONT="Courier New"]sudo apt-get install eclipse[/FONT]?

I just installed Hardy, ran the above command and Eclipse works beautifully (although with eclipse-cdt and eclipse-pydev)

Both the JVM (Java Virtual Machine) and the JRE (Java Runtime Environment) are downloaded as dependencies with that command.

---

### Post by Natilator3 on 2008-06-22
i downloaded it from the webpage, so i'm using the command you suggested right now and it's downloading (finger's crossed)

thanks for the help

---

### Post by Natilator3 on 2008-06-22
Yay Everything Works Thanks So Much!

---

