---
title: "couldn't install a .jar file properly"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by yuanhangliu1 on 2012-10-29
I want to install a .jar file. The download link is [http://www.compneuro.org/CDROM/nmorph/download.html](http://www.compneuro.org/CDROM/nmorph/download.html) 
I download the file "cvapp.jar", and type in the command exactly as it indicates "java -classpath cvapp.jar:$CLASSPATH cvapp" But only return with a wrong information as follows:
Exception in thread "main" java.awt.HeadlessException
    at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:173)
    at java.awt.Window.<init>(Window.java:477)
    at java.awt.Frame.<init>(Frame.java:419)
    at neuronEditorFrame.<init>(neuronEditorFrame.java:30)
    at cvapp.main(cvapp.java:89)

Can anybody help me with this?

---

### Post by yuanhangliu1 on 2012-10-29
Anybody can help? Thanks!

---

### Post by yuanhangliu1 on 2012-10-29
Problem solved. 
Because of Java incompatibility
solved with the command "sudo apt-get install openjdk-6-jdk"

---

