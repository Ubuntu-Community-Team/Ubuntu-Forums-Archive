---
title: "Unable to run Eclipse CDT, and lots of error dialogs"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by Leif Goodwin on 2013-04-01
I have installed the Java OpenJDK and Eclipse, using the command line apt-get tool. How do I run Eclipse? If I go to the Dash Home => Applications and select Eclipse, nothing happens. I also get a lot of errors messages from Ubuntu, such as "System program problem detected". 

I am running Ubuntu 12.10 on a 64 bit PC with UEFI, installed as a dual boot alongside Windows 8.

---

### Post by Nutster on 2013-04-01
What happens if you run "eclipse" from within a terminal?  Open a terminal and then type "eclipse".  Are there any message on the terminal as eclipse tries to start?

---

### Post by Cheesemill on 2013-04-01
I've always had problems in the past trying to run Eclipse using OpenJDK instead of the Oracle Java JDK.

Try installaing Oracle Java using the following commands, this may solve your problem.
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by Leif Goodwin on 2013-04-01
Solved: 

[http://akovid.blogspot.co.uk/2012/08/installing-eclipse-juno-42-in-ubuntu.html](http://akovid.blogspot.co.uk/2012/08/installing-eclipse-juno-42-in-ubuntu.html)

I tried several online installation tutorials, which did not work, before finding the above.

---

