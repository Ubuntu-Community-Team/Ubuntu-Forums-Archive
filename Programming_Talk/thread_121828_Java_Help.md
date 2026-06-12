---
title: "Java Help"
date: 2006-01-26
forum: Programming Talk
---

### Post by JoshHendo on 2006-01-26
I am trying to run a java class file from the terminal that includes a blank GUI. Currently I am learning java, and all the things I have tried so far just display the result on the command line. When I try to run one with a blank GUI interface; it comes up the following:

> 
** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)
aborting...
Aborted


Does anyone know how I could fix this? I am using the most recent JDK version in synaptic.

-edit-
source code: [http://www.cadenhead.org/book/java-24-hours/source/chapter13/SalutonFrame.java](http://www.cadenhead.org/book/java-24-hours/source/chapter13/SalutonFrame.java)

---

### Post by jerome bettis on 2006-01-26
> **JoshHendo]I am trying to run a java class file from the terminal that includes a blank GUI. Currently I am learning java, and all the things I have tried so far just display the result on the command line. When I try to run one with a blank GUI interface said:**
> http://www.cadenhead.org/book/java-24-hours/source/chapter13/SalutonFrame.java[/URL]

the source code is not the problem (for now) :p

the java package is not installed properly (or borked), are you using that blackdown java?  it's not very good, your best bet is to install sun's java.  a search of the forums could get you set with that very easily.  or you could go here (i highly recommend this thing :D) [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)


** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)

not sure exactly what is going on here, but data_fid != 0 means that the program tried to open a file, but something went wrong.  if you want to have some fun you could find that .c file, check line 572 and go from there ... it could just be a typo or something.

---

### Post by Viro on 2006-01-26
Do not use any of the Java packages that come with Ubuntu!! They are usually not feature complete and are very poor choices for learning. Install Sun's Java VM instead.

---

### Post by JoshHendo on 2006-01-26
[QUOTE=jerome bettis]the source code is not the problem (for now) :p

the java package is not installed properly (or borked), are you using that blackdown java?  it's not very good, your best bet is to install sun's java.  a search of the forums could get you set with that very easily.  or you could go here (i highly recommend this thing :D) [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)


** ERROR **: file ../../../src/libjava/jni/gtk-peer/gnu_java_awt_peer_gtk_GtkImage.c: line 572 (createRawData): assertion failed: (data_fid != 0)

not sure exactly what is going on here, but data_fid != 0 means that the program tried to open a file, but something went wrong.  if you want to have some fun you could find that .c file, check line 572 and go from there ... it could just be a typo or something.[/QUOTE]
Thanks!

I installed both the java programs using that and it worked. :D

-Josh

---

