---
title: "how to configure Java"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Zeck on 2008-05-05
Hi all,
How to install java ? please help me !!!!!!!!!!!!

I installed it but it have is the error.

Here is the error !

The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * j2re1.4
 * kaffe
 * cacao
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found


Regards,
Zeck

---

### Post by Arasfang on 2008-05-05
Hmm,

```
sudo apt-get install java
```

usually works. Or you can open Synaptic Package Manager and search for Java and install it that way.

You can also go to [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com) and look for a .deb-package, download and then click to install.

/Mattias

---

### Post by mlentink on 2008-05-05
Applications > Add/Remove Programs

Search for 'Java' ....

Tip: a lot of what you might need is in Add/Remove Programs

---

### Post by Bubba64 on 2008-05-05
I think Java 6 is in Ubuntu restricted extras in add remove.

---

### Post by vishzilla on 2008-05-05
install using ```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by gandaran on 2008-05-05
open synaptic, search for the open java installed, uninstall all does packages, choose complete removal, then find the sun-java6-plugin and check it for install and click apply.
also click the reload button on synaptic before installing anything.

---

