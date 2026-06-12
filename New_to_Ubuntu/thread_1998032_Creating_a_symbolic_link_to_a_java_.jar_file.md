---
title: "Creating a symbolic link to a java .jar file"
date: 2012-06-06
forum: New to Ubuntu
---

### Post by Senior_Buckethead on 2012-06-06
Hi all,

Im trying to create a symbolic link for arachnophilia that I can place on my desktop. the command that I need to execute is:
```

java -jar arachnophilia.jar

```
and my attempt is:
```

glenn@design:~/Desktop$ ln -s /home/glenn/.Arachnophilia/arachnophilia.jar ./java jar arachnophilia.jar
ln: target `arachnophilia.jar' is not a directory
glenn@design:~$

```
I have put arachnophilia.jar file in a director called .Arachnophilia in my home directory.

Can someone tell me where I have gone wrong?

---

### Post by MG&amp;TL on 2012-06-06
Symbolic links are just shortcuts to files. They can't execute anything.

If you can normally run the application by double-clicking on it, use this command:

```
ln -s ~/.Arachnophilia/arachnophilia.jar ~/Desktop/arachnophilia
```

this will make a symbolic link on your desktop to the file. When you double-click on it, it will try and open the file.

If not, make a new file, called "arachnophilia.desktop", on your desktop, with this content:

```

[Desktop Entry]
Version=1.0
Type=Application
Name=Arachnophilia
Exec=java -jar /home/glenn/.Arachnophilia/arachnophilia.jar
```

This is how application launchers work in general.

---

### Post by Senior_Buckethead on 2012-06-06
Ok, I made a file on the desktop that contained:
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Arachnophilia
Exec=java -jar /home/glenn/.Arachnophilia/arachnophilia.jar

```Then I chmod a+x the file to make it executable
I checked that I had permission to run it,
Then I went to run it:
```
glenn@design:~/Desktop$ arachnophilia.desktop
arachnophilia.desktop: command not found
glenn@design:~/Desktop$ sudo arachnophilia.desktop
sudo: arachnophilia.desktop: command not found
glenn@design:~/Desktop$ sudo sh arachnophilia.desktop
arachnophilia.desktop: 1: arachnophilia.desktop: [Desktop: not found
arachnophilia.desktop: 4: arachnophilia.desktop: -jar: not found
glenn@design:~/Desktop$

```What am I doing wrong?

EDIT> Can atleast open archnophilia in its folder by right mouse clicking and running with OpenJDK runtime. Should have thought about making the actual .jar file executable earlier.
Still no life clicking on the shortcut on the created above. Checked permissions on it and its glenn:glenn, so have no clue why it doesn't work.

---

### Post by MG&amp;TL on 2012-06-06
Okay, is the file (on the desktop, not in terminal) showing as "arachnophilia.desktop" or "Arachnophilia"? And have you tried double-clicking the .desktop file?

Only other thing I can think of is to use* alacarte* ("Main menu") and have the shortcut in the dash/menu.

---

### Post by Senior_Buckethead on 2012-06-06
Thanks for the help,

Ok I have tried with the shortcut on the desktop being both Arachnophilia and Arachnophilia.Desktop, neither one works.

In the .Arachnophilia directory, if I double-click on the Arachnophilia.jar file, it opens up archive manager to show the contents of the file.
Like I said earlier, the only way I can get the jar file to run is by right mouse-click on the file and run with either OpenJava 6 or 7 runtime.

Using alacarte, got same error as first did, no file or directory.

Contents of the .Arachnophilia Directory:
```

glenn@design:~$ cd .Arachnophilia
glenn@design:~/.Arachnophilia$ ls -al
total 2584
drwxrwxr-x  8 glenn glenn    4096 Jun  7 08:22 .
drwxr-xr-x 90 glenn glenn    4096 Jun  7 08:00 ..
drwxrwxr-x  2 glenn glenn    4096 Jun  6 15:37 ArachConf
-rw-rw-r--  1 glenn glenn    2469 Jun  7 08:22 ArachErrorLog.txt
-rwxrwxr-x  1 glenn glenn 2608946 Jun  6 15:29 Arachnophilia.jar
drwxrwxr-x  2 glenn glenn    4096 Jun  6 15:30 CustomClasses
drwxrwxr-x  4 glenn glenn    4096 Jun  6 15:30 Documentation
drwxrwxr-x  2 glenn glenn    4096 Jun  6 15:30 Macros
drwxrwxr-x  2 glenn glenn    4096 Jun  6 15:30 SpellCheckData
drwxrwxr-x  2 glenn glenn    4096 Jun  6 15:30 Templates
glenn@design:~/.Arachnophilia$ 

```Also included the Arachnophilia Error Log File:
```

Error log for Arachnophilia 5.5 build 2691
Thu Jun 07 08:22:10 NZST 2012
Operating System: Linux
Java Version: 1.6.0_24
If you plan to submit a bug report, be sure to include the entire contents of this log.
If there are no messages below the dashed line, there were no errors
during the most recent Arachnophilia session.
If you see a message below about an error "in native code outside the VM",
or language like that, this means there was an error in your operating system,
not in Java or Arachnophilia.
------------------------------------------------------------
java.lang.ClassNotFoundException: javax.swing.plaf.nimbus.NimbusLookAndFeel
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:264)
    at javax.swing.SwingUtilities.loadSystemClass(SwingUtilities.java:1871)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:573)
    at Arachnophilia.ArachComp.setupLookAndFeel(ArachComp.java:207)
    at Arachnophilia.Arachnophilia.initPhase2(Arachnophilia.java:191)
    at Arachnophilia.Arachnophilia.<init>(Arachnophilia.java:171)
    at Arachnophilia.Arachnophilia$8.run(Arachnophilia.java:1541)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:647)
    at java.awt.EventQueue.access$000(EventQueue.java:96)
    at java.awt.EventQueue$1.run(EventQueue.java:608)
    at java.awt.EventQueue$1.run(EventQueue.java:606)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:617)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```

---

### Post by Senior_Buckethead on 2012-06-07
Bump

---

### Post by MG&amp;TL on 2012-06-08
> **Senior_Buckethead said:**
> 
[/CODE]Also included the Arachnophilia Error Log File:
```

Error log for Arachnophilia 5.5 build 2691
Thu Jun 07 08:22:10 NZST 2012
Operating System: Linux
Java Version: 1.6.0_24
If you plan to submit a bug report, be sure to include the entire contents of this log.
If there are no messages below the dashed line, there were no errors
during the most recent Arachnophilia session.
If you see a message below about an error "in native code outside the VM",
or language like that, this means there was an error in your operating system,
not in Java or Arachnophilia.
------------------------------------------------------------
java.lang.ClassNotFoundException: javax.swing.plaf.nimbus.NimbusLookAndFeel
    at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
    at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
    at java.lang.Class.forName0(Native Method)
    at java.lang.Class.forName(Class.java:264)
    at javax.swing.SwingUtilities.loadSystemClass(SwingUtilities.java:1871)
    at javax.swing.UIManager.setLookAndFeel(UIManager.java:573)
    at Arachnophilia.ArachComp.setupLookAndFeel(ArachComp.java:207)
    at Arachnophilia.Arachnophilia.initPhase2(Arachnophilia.java:191)
    at Arachnophilia.Arachnophilia.<init>(Arachnophilia.java:171)
    at Arachnophilia.Arachnophilia$8.run(Arachnophilia.java:1541)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:226)
    at java.awt.EventQueue.dispatchEventImpl(EventQueue.java:647)
    at java.awt.EventQueue.access$000(EventQueue.java:96)
    at java.awt.EventQueue$1.run(EventQueue.java:608)
    at java.awt.EventQueue$1.run(EventQueue.java:606)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.security.AccessControlContext$1.doIntersectionPrivilege(AccessControlContext.java:105)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:617)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:275)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:200)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:190)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:185)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:177)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:138)

```

I have to say, that's not looking good. I'm not sure if the app has actually crashed, or just  had a bit of a blip. 

Anyway, what are you putting in the "Command" field of *alacarte*? That's the only thing I can think of that would give no file or directory.

---

### Post by Senior_Buckethead on 2012-06-08
The only way I can get arachnophilia to run, is to navigate to the folder in nautilus, and right mouse click on the program and 'open with OpenJDK 6 (or 7) runtime'.

Do you think it is worth submitting a bug report?

---

### Post by MG&amp;TL on 2012-06-08
> **Senior_Buckethead said:**
> The only way I can get arachnophilia to run, is to navigate to the folder in nautilus, and right mouse click on the program and 'open with OpenJDK 6 (or 7) runtime'.

Do you think it is worth submitting a bug report?
Hm.

Possibly, what does:

```
java -jar ~/.Arachnophilia/Arachnophilia.jar
```

output?

---

### Post by Senior_Buckethead on 2012-06-08
Hey! No output from terminal, just launches Arachnophilia.

---

### Post by MG&amp;TL on 2012-06-08
> **Senior_Buckethead said:**
> Hey! No output from terminal, just launches Arachnophilia.

Hm. How about:

```
java -jar /home/glenn/.Arachnophilia/Arachnophilia.jar 
```?

If that works, try copy-pasting that into alacarte. It's very easy to make a typo.

---

### Post by Azdour on 2012-06-08
Hi,

Hmmm... Looks like from your error log you are running Oracle Java?:

```
Java Version: 1.6.0_24
```

And that running Arachnophilia.jar with the OpenJDK works.

From what I can gather the NimbusLookAndFeel class changed it's location under Sun/Oracle JDK 1.6 update 10 from:
```

javax.swing.plaf.nimbus.NimbusLookAndFeel

```
to:
```

com.sun.java.swing.plaf.nimbus.NimbusLookAndFeel

```

That's why I think you are having problems running it. Therefore if you are going to use:

```
java -jar /home/glenn/.Arachnophilia/arachnophilia.jar
```

You have several options. You could change the java alternative on your machine from oracle to openjdk via terminal:

```
sudo update-alternatives --config java
```

Here you should be able to choose the openjfk, and then everytime you call java it will be the openjdk one.

Or possibly you can use the full path to the openjdk java command on your machine in the desktop file you created?

---

### Post by Senior_Buckethead on 2012-06-08
Hey thats great. dragged the shortcut from alacarte to the desktop. I think I have issues with alacarte but that can be another night.
Interestingly the icon on the desktop is not that of arachnophilia but a gnome foot.

Anyway it works, thank you for your help.

---

### Post by Senior_Buckethead on 2012-06-08
Im running OpenJava Runtime 7.

---

### Post by Azdour on 2012-06-08
Hi,

That's really strange as the log you included in your post says:

> 
Error log for Arachnophilia 5.5 build 2691
Thu Jun 07 08:22:10 NZST 2012
Operating System: Linux
Java Version: 1.6.0_24


It was the Java Version that got me thinking. If you are solely running openjava runtime 7 surely the version would have been:

> 
Java Version: 1.7

Anyway you seem to have it all working now so that's great.

---

### Post by Senior_Buckethead on 2012-06-08
You know I put my hand on my heart and say I honestly thinking its open Java. I cant remember installing anything else, but then, like alot of things, I could be wrong.

---

### Post by Azdour on 2012-06-08
Hi,

Running:

```
sudo update-alternatives --config java
```

Will show you which versions of Java you have installed if you are curious. You can always use Ctrl+C to exit the Java selection.

Running:

```

java -version

```

Will tell you what Java you computer will use by default.

---

### Post by MG&amp;TL on 2012-06-08
> **Senior_Buckethead said:**
> Hey thats great. dragged the shortcut from alacarte to the desktop. I think I have issues with alacarte but that can be another night.
Interestingly the icon on the desktop is not that of arachnophilia but a gnome foot.


Default icon. If you want to make the icon a different one, open the shortcut up in alacarte and edit it.

---

### Post by Senior_Buckethead on 2012-06-08
```

glenn@design:~$ sudo update-alternatives --config java
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                           Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk-i386/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-7-openjdk-i386/jre/bin/java   1051      manual mode

Press enter to keep the current choice
[*], or type selection number: 

```
Theres the output. Seems I am running 6 and not 7.

---

### Post by Senior_Buckethead on 2012-06-11
So the way I created a symbolic link on the desktop was to create a file called "Arachnophilia.desktop". In this file I have:
```

[Desktop Entry]
Version=1.0
Type=Application
Name=Arachnophilia
Exec=java -jar /home/glenn/.Arachnophilia/Arachnophilia.jar

```
I then chown the file (sudo chown glenn:glenn Arachnophilia.desktop)
and chmod the file (sudo chmod 644 Arachnophilia.desktop).

The file then I can click on and it will open Arachnophilia. Alternatly, I can click on the file and right-mouse click 'open' and this will open arachnophilia.

[Solved]

---

