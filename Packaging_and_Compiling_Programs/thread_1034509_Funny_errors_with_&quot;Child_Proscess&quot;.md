---
title: "Funny errors with &quot;Child Proscess&quot;?"
date: 2009-01-08
forum: Packaging and Compiling Programs
---

### Post by Tamalin on 2009-01-08
Okay,
When my application installs from a deb, it places a script and a JAR file into /usr/bin which I will refer to as myprog and myprog.jar.  After installing the debian package, and selecting it from the menu, I get an error stating: "Failed to execute child process "myprog" (Permission denied)."

Does anyone know what is wrong?
Thank You!

---

### Post by meatpan on 2009-01-16
A few quick questions:

What is the relation between myprog and myprog.jar?  Does one file refer to the other (like a java wrapper)?   What are the permissions of the file when you run 'ls -l myprog' and  'ls -l myprog.jar'?

It would also be helpful if you posted the exact commands that were run by the package manager.

---

### Post by Tamalin on 2009-01-16
Well myprog calls java -jar myprog.jar. They are both in /usr/bin.
I did enable it to run as an executable file which seems to work.

---

