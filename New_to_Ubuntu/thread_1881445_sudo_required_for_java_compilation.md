---
title: "sudo required for java compilation"
date: 2011-11-15
forum: New to Ubuntu
---

### Post by e-blade on 2011-11-15
While I admire the opensource JRE shipped with Ubuntu, I am in the situation where I need to write and compile Java code using SUNs original JDK/JRE.

Now I went through the motions and installed the JRE/JDK and so forth.

The thing I then find is that if I do a "java HelloWorld" (just to test the installation) I get a ClassNotFoundException despite standing in the directory where HelloWorld exist and knowing full well that the java command points to the correct JRE. However if I do "sudo java HelloWorld" it works perfectly.

How can I remove the need for prefixing the execution with sudo?

Thanks :)

---

### Post by greendragons on 2011-11-15
What are the permission of the directory where ur output is produced....

---

