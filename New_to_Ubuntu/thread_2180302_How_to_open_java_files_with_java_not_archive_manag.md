---
title: "How to open java files with java not archive manager?"
date: 2013-10-12
forum: New to Ubuntu
---

### Post by Crinkle on 2013-10-12
How to do this?

Tried all the answers here, nothing works:

[http://askubuntu.com/questions/192914/how-run-a-jar-file-with-a-double-click](http://askubuntu.com/questions/192914/how-run-a-jar-file-with-a-double-click)

problem is, i can only run a file with java by right clicking the file, and selecting java from the open with menu, i want it to double click open in java. with archive manager demoted to the open with menu.

---

### Post by pbrane on 2013-10-12
I did this on **xubuntu** to make jar files run on a double click. You should be able to do something similar in other flavors of Ubuntu.

**1.** run a terminal and type **cd <name of directory where jar file is stored> **then type **chmod u+x <name of jar file>**
I had to do this in a terminal. the permissions in the file manager wouldn't let me change to executable. If yours does then add the executable bit there.

**2.** right click on the jar file and choose to open/run with other application. choose the java jre you want to use.
this sets the MIME type to always run with java.

You may experience issues with this because some java programs need some runtime arguments to make them work correctly.

EDIT: I should mention that this has to be done with every jar file. the executable bit is not set on jar files and will need to be set to run it.

---

