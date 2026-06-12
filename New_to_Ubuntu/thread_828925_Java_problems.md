---
title: "Java problems"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by Master-of-None on 2008-06-14
Java doesn't work despite Java 6 is installed. What else do I need? What should I do?

---

### Post by dracayr on 2008-06-14
the java-plugin for firefox or the real java jre?

dracayr

---

### Post by Sef on 2008-06-14
1) What OS do you have?

2) What browser are you using?

3) How did you install java?

---

### Post by sdowney717 on 2008-06-14
[http://forum.java.sun.com/thread.jspa?threadID=567732](http://forum.java.sun.com/thread.jspa?threadID=567732)

setting the java home variable

Plus there is a command to tell it which version of java to use

[http://forum.java.sun.com/thread.jspa?threadID=757537&messageID=4327477](http://forum.java.sun.com/thread.jspa?threadID=757537&messageID=4327477)

---

### Post by Master-of-None on 2008-06-14
I have Kubuntu8.04 with KDE 4.0

I use firefox

and it was installed with the Ubuntu Restricted Extras package.

---

### Post by dracayr on 2008-06-14
As far as I know, you don't need the extras for java. what choices do you get, when running ```
sudo update-alternatives --config java
```? And when do you get the problem? when you try to use an applet with firefox, or when you try to use a java application, or when you try to compile sth. with javac?

dracayr

---

### Post by Master-of-None on 2008-06-14
In Firefox it says I need additional software to run Java Apps, then it gives me 4 choices, two for gjc or something like that, and two from Sun. Java 5 and Java 6. I click Java 6, and it says its already installed.

Yet, installing anything else doesn't help either.

---

### Post by Master-of-None on 2008-06-14
bump

---

### Post by avtolle on 2008-06-14
When you go to about:plugins in the FF address bar, does the java plugin show up? If so, to which java does it refer?

---

### Post by Master-of-None on 2008-06-15
It doesn't have a plugin for Java. How do I get the Java Plugin for Firefox?

---

### Post by Master-of-None on 2008-06-15
bump

---

### Post by Master-of-None on 2008-06-15
bump

---

### Post by jamesstansell on 2008-06-18
If you have the icedtea-gcjwebplugin package installed, then it's probably best to remove it.  Then install the sun-java6-plugin package and restart Firefox.

You are using Firefox 3, right?

If you search for posts with the 'java' tag you will find other people who have resolved similar problems.

Also, you may need to run this command

```
$ sudo update-java-alternatives -s java-6-sun
```

---

