---
title: "which java to install?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-05-23
I want to sort my bookmarks in Mozilla.  The firesort.jar looks appealing.  Tried to run it from the command line ("java -jar firesort.jar") but nothing doing, I have to install java first.  So I entered "sudo apt -get install gij-4.2" to have java installed.  Then, once again, "java -jar firesort.jar" but I got the following message:

Failed to load Main-Class manifest attribute from firesort.jar

What is to be done?

Thanks in advance

---

### Post by vishzilla on 2008-05-23
Install Sun Java (sun-java6-*)

---

### Post by jamesstansell on 2008-05-24
What version of Ubuntu are you running?

This problems sounds like possibly a a corrupt jar file - what does "unzip -l firesort.jar" give you?

---

### Post by superprash2003 on 2008-05-24
yea.. it seems that java is already installed and there is something wrong with the jar file

---

