---
title: "Can Java files from Ubuntu Eclipse work or can be exported to the Windows Eclipse?"
date: 2013-03-02
forum: Programming Talk
---

### Post by Edgar117 on 2013-03-02
Hi,

I starting Java programming at school and take a good guess, everyone uses Window$ :confused:

So we are practicing java for beginners in Eclipse (In Windows).

I want to know if I send my teacher my projects would the files run smoothly with out any problem??:guitar:

Thank You for your time

---

### Post by Tununias on 2013-03-02
Yes. The .java and .class files will all work on Windows.

---

### Post by QIII on 2013-03-02
*Moved to **Programming Talk***

---

### Post by KdotJ on 2013-03-02
Java will work anywhere that Java is installed... no matter what operating system. The 'compiled' .class files that are created do not run on the native operating system... they run on a Java Virtual Machine (the [JVM]("http://en.wikipedia.org/wiki/Java_virtual_machine")).

---

### Post by r-senior on 2013-03-02
You probably also want to check you are using the same major version, e.g. Java 7.

---

### Post by tgalati4 on 2013-03-02
Put in the comments block:  *Please don't ding me if this doesn't run on your Windows machine.  It was programmed in a linux environment.  Neckbeards for Freedom.*

---

### Post by danniel on 2013-03-03
> **Edgar117 said:**
> I want to know if I send my teacher my projects would the files run smoothly with out any problem??
Yes, everything should work fine.

Also remember that Linux and Windows use different end-of-line symbols. Most advanced editors (like Eclipse), don't have an issue with this, but if your teacher views the files in Notepad, then the text will look as one long line :)

As far as I can remember, you can force a certain end of line style in Eclipse, by going to ***Window > Preferences > General > Workspace > New text file line delimiter*** and choosing "Windows".

---

### Post by ofnuts on 2013-03-03
If you only send .java/.class files yes it should work (if you teacher is really picky you may have to convert java files to Windows end-of-line conventions with "todos", but if he is that picky change teachers... he doesn't know much).

---

