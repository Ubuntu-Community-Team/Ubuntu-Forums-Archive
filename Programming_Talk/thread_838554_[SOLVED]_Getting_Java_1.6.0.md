---
title: "[SOLVED] Getting Java 1.6.0"
date: 2008-06-23
forum: Programming Talk
---

### Post by ConMan318 on 2008-06-23
Pretty simple, I have Java 1.5.0 and I want the newest version.  I tried the repos but I don't really know which of them I need to install/uninstall to upgrade since there are so many packages that come up when I search 'java'.  Is there a command that'll upgrade the whole package to the new version?  Or do I need to get it from Sun's site?

Thanks.

---

### Post by dexter.deepak on 2008-06-23
sudo apt-get install sun-java6-jdk

or if you are a hungry mind:
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre 

wait if someone gives you a method of "upgrading" from java5 to java6..

---

### Post by xlinuks on 2008-06-23
If you're a Java developer you need this (type in the terminal):
```

 sudo apt-get install sun-java6-jdk

```
If you just want to have java installed on your computer (thus just to run Java programs) try this:
```

sudo apt-get install sun-java6-jre

```

---

### Post by ConMan318 on 2008-06-23
I used the -jdk install and it worked, thanks.

---

