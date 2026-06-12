---
title: "problem with eclipse"
date: 2009-09-09
forum: Programming Talk
---

### Post by ivh90 on 2009-09-09
hi !
i am taking a java programming course , and my teacher told us we have to use eclipse ... so i downloaded it and used sun-java6 as requested .
i ve been using it for about a week and everything was great up until this morning when eclipse decided to stop working and it gave me the "JVM terminated.exit code=1"message
i googled and tried several solutions , i even removed and reinstalled  but no luck !!!!!
please help me it is urgent , i need it worked out by tommorow morning :( :( 
ps. i am using ubuntu 9.04 
thanks

---

### Post by dwhitney67 on 2009-09-09
It is not essential to use Eclipse to perform Java development.  As a last (or in my case, a first) resort, you can use the command line and your favorite editor.

The editor that is closest in behavior to the generic editor include with Eclipse is perhaps gedit.

Once you have the file(s) created and saved, you can compile your Java source files using:
```

javac <MainClassName>.java   # when you have a single file

or

javac *.java    # when you have multiple files

```
Then to run:
```

java <MainClassName>

```
If you have trouble running your code from the command line, perhaps the issue will be because of the lack of a definition for CLASSPATH.  Set this environment variable as appropriate so that the JRE can find your Java class(es).  For example:
```

export CLASSPATH=./:$CLASSPATH

```

P.S.  Eclipse relies on Java (Java Virtual Machine).  If you must have Eclipse, consider checking to see if you Java installation is still sound (ie installed).

---

### Post by karlmp on 2009-09-09
don't use eclipse from the repositories, download it and install it from the website [http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/](http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/)

the version from the repositories is out of date
[https://blueprints.launchpad.net/ubuntu/+spec/eclipse](https://blueprints.launchpad.net/ubuntu/+spec/eclipse)
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-eclipse-update](https://blueprints.launchpad.net/ubuntu/+spec/foundations-karmic-eclipse-update)

---

### Post by Shin_Gouki2501 on 2009-09-09
repositorys are so great... if they keep up..

---

### Post by linuxford on 2009-09-29
I also had problems and used this one (as the previous poster mentions) and it works beautifully so far with Ubuntu Jaunty

[http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/](http://johnpaulett.com/2009/06/26/install-eclipse-galileo-3-5-on-ubuntu-jaunty-9-04/)

---

