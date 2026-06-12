---
title: "installing things  programs?"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-05-04
Have tried this with a few things and get nowhere everytime. I will pick this so everyone can see it.
[http://sourceforge.net/projects/xmm/?source=dlp](http://sourceforge.net/projects/xmm/?source=dlp)
I click on download, the manger opens and saves the file or the rar "box" I extract it and now I'm stuck with a file in my download file.
So what do I do next so I can use the program?
Where do I have to place the file? 
How do I get it to work like having an icon on my dash to pick it and have it run?
When I download things from the software center it does all this. But when I pick open source programs off the web  I just get a file in my download file and have no clue on what to do next.

---

### Post by QIII on 2014-05-04
Hello!

That is the difference between a "package manager" and downloading some random piece of software from the web.  The first has been prepared for a particular distro or group of distros so that you don't have to do much.  The second, not so much.  You are often on your own -- some still require compilation.

It looks to me that the file downloaded is ultimately a .jar.  Is that correct?  Is there a "read me" file included?

If so, do you have the Java Runtime Environment (JRE -- either Oracle or OpenJDK) installed?

---

### Post by Vladlenin5000 on 2014-05-04
The example you gave is a Java app therefore you need to have any Java RE previously installed.
This one specifically is the installer, a JAR file... No need to extract, just run it and follow the installer's instructions.

---

### Post by EZZ9 on 2014-05-05
I looked and I have OpenJDK Java 7 Runtime, OpenJDK Java 6 Runtime & policy tool 6 & 7 clicked on them all and nothing happens

---

### Post by EZZ9 on 2014-05-05
Downloaded it again clicked on the rear box open with JDK and get this.
MovieManager.v.2.9.1.3.installer.jar' is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit.

---

### Post by monkeybrain20122 on 2014-05-05
Right click it, in properties, permissions check "allow to execute".

---

### Post by The Cog on 2014-05-05
Right-click the jar file's icon, edit the properties and set it to be executable. Then you will be able to run it.

---

