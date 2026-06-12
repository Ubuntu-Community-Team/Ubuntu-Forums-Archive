---
title: "Java problem"
date: 2006-10-09
forum: Programming Talk
---

### Post by jinxen on 2006-10-09
When i try to run a program with dialogs and etc, graphic.. I get this.
The package classpath-gtkpeer is installed.

> Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(libgcj.so.70)
   at java.awt.Window.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at java.awt.Frame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities$OwnerFrame.<init>(libgcj.so.70)
   at javax.swing.SwingUtilities.getOwnerFrame(libgcj.so.70)
   at javax.swing.JOptionPane.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at Hej.main(Hej.java:8)
Caused by: java.lang.UnsatisfiedLinkError: libgtkpeer: libgtkpeer.so: cannot open shared object file: No such file or directory
   at java.lang.Runtime._load(libgcj.so.70)
   at java.lang.Runtime.loadLibrary(libgcj.so.70)
   at java.lang.System.loadLibrary(libgcj.so.70)
   at gnu.java.awt.peer.gtk.GtkToolkit.<clinit>(libgcj.so.70)
   at java.lang.Class.initializeClass(libgcj.so.70)
   at java.lang.Class.forName(libgcj.so.70)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.70)
   ...9 more


Best regards, Tommy

---

### Post by meng on 2006-10-09
Which java/javas do you have installed, just the default gcj? Perhaps you should install and use sun java instead.

---

### Post by jinxen on 2006-10-09
i have the sun5-java-jdk installed with the others that follow to (bin, jre and something else), and the libgcj8-dev i think.

---

### Post by meng on 2006-10-09
Is the Sun Java configured as your default java? If not, check out:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)
the section on: Selecting the default Java version

---

### Post by jinxen on 2006-10-09
That fixed the problem! I had the gcj as default, as a selected tje sun version everything worked great! :) Is it possible to change so that i can use the swedish letters åäö in files? Because now its utf-8 only. And ofcourse some of my old programs have got swedish letters in them :P

Best Regards, Tommy

---

### Post by meng on 2006-10-09
I'm glad it's working. I wish I could help you with that other problem, but unfortunately I'm not that clever.

---

### Post by jinxen on 2006-10-10
yeah, thats super its working! But i have to get the swedish letters to work, because my teacher insists in having those letters in the programs :P 

Someone that know how to get the iso typing to work in java instead of utf-8?

---

### Post by sgtBiafra on 2006-10-10
Which part of the equation isn't supporting ISO characters: eclipse or java?

---

### Post by jinxen on 2006-10-10
Both, i can write åäö in eclipse but when i open files with the letters in them they area auto erased.. And when i compile with javac i get the complaints on the letters.

Regards, tommy


> jinxen@skynet:~/Desktop/javapgm$ javac HissDemo.java 
HissDemo.java:10: warning: unmappable character for encoding UTF8
        h1.k&#65533;rTill(r1);
            ^
HissDemo.java:12: warning: unmappable character for encoding UTF8
        h2.k&#65533;rTill(r1);
            ^
HissDemo.java:13: warning: unmappable character for encoding UTF8
        System.out.println("h1 = " + h1.vilkenV&#65533;ning());
                                               ^
HissDemo.java:14: warning: unmappable character for encoding UTF8
        System.out.println("h2 = " + h2.vilkenV&#65533;ning());
                                               ^
HissDemo.java:10: illegal character: \65533
        h1.k&#65533;rTill(r1);
            ^
HissDemo.java:10: not a statement
        h1.k&#65533;rTill(r1);
          ^
HissDemo.java:12: illegal character: \65533
        h2.k&#65533;rTill(r1);
            ^
HissDemo.java:12: not a statement
        h2.k&#65533;rTill(r1);
          ^
HissDemo.java:13: illegal character: \65533
        System.out.println("h1 = " + h1.vilkenV&#65533;ning());
                                               ^
HissDemo.java:14: illegal character: \65533
        System.out.println("h2 = " + h2.vilkenV&#65533;ning());
                                               ^


---

### Post by nikosft on 2006-10-10
javac has a -encoding option. May be playing with that solves the problem

---

### Post by jinxen on 2006-10-10
Think i figured out the problem that didnt really excist. It seems i copied the files from a windows mounted disc, and the åäö's got changed to symbols, and when i changed them back when in the linux environment the programs worked again. A little work ahead for me, but well worth it ;)

Regards, Tommy

---

### Post by zeekay on 2007-07-02
Thank you so much, I've been trying to make VE work on eclipse for quite some, and now it does! :D

Thank you again.

happyguy++;

---

