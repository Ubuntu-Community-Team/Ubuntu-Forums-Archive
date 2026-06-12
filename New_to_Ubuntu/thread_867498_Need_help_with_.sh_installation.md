---
title: "Need help with .sh installation"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Ameades on 2008-07-22
Hey guys,

First off, I am looking for a program that will enable me play music off my computer by saying the name of the artist/song into a mic.  I found this program called talkhouse and they have a linux version.  The download is called talkhouse_unix.sh and when I go to install it I does not complete.

When the Java box pops up for the installation it is blank and then nothing happens.  Does anyone know how to fix this or could suggest a program that does the same thing and is free???

---

### Post by cozmicharlie on 2008-07-23
I am not that familiar with this but it looks like all you need to do is install java.  The web site does not provide much info does it.
Open a terminal and at the prompt copy and paste the following:   
```
sudo apt-get remove icedtea-gcjwebplugin openjdk-6-jre openjdk-6-jre-headless openjdk-6-jre-lib && sudo apt-get install sun-java6-fonts sun-java6-jre sun-java6-plugin unrar
```

If that does not work then maybe someone else will post a solution or you may need to ask the help at talkhouse for more info.

---

### Post by Sef on 2008-07-23
Easy way to install java on 32-bit OS:

Applications > Add/Remove > Show: change to 'All Available Applications' > Search: Sun Java 6 > check top box (Sun Java 6 Runtime) > apply changes > apply > close

Read [How to Install Anything in Ubuntu]("http://monkeyblog.org/ubuntu/installing/") to install .sh

---

