---
title: "Setting default to suv java6"
date: 2010-08-17
forum: Programming Talk
---

### Post by niteshreddy on 2010-08-17
hey... i installed open-jdk at first.

But later installed sun-java6-jdk package and also its associated runtime.

But when i try to set it as the default jvm and jdk i get an error.

```

niteshreddy@niteshreddy-laptop:~$ sudo update-java-alternatives --list
java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk
java-6-sun 63 /usr/lib/jvm/java-6-sun

niteshreddy@niteshreddy-laptop:~$ sudo update-java-alternatives --set java-6-sun
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.
update-alternatives: error: alternative /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so for mozilla-javaplugin.so not registered, not setting.
update-alternatives: error: no alternatives for xulrunner-1.9-javaplugin.so.

niteshreddy@niteshreddy-laptop:~$ 

```



I dont understand what the problem is. Help would be appreciated.

Thanks..!

---

### Post by r-senior on 2010-08-17
The update-java-alternatives tries to switch a whole list of things. I think the messages you have are browser plugins and similar that it can't find alternatives for. You probably need to install sun-java6-plugin if you want a completely clean switch.

As far as the basic JVM and compiler that you'd use for development is concerned, you can check which version is actually in use following the update-java-alternatives command like so ...

```

$ java -version
java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8.1) (6b18-1.8.1-0ubuntu1)
OpenJDK 64-Bit Server VM (build 16.0-b13, mixed mode)

$ javac -version
javac 1.6.0_18

$ sudo update-java-alternatives -s java-6-sun

$ java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)

$ javac -version
javac 1.6.0_20

```

---

### Post by niteshreddy on 2010-08-18
Thanks it worked..!

I have another small problem

I set my JAVA_HOME editing my user .bashrc file.

When i do "echo $JAVA_HOME" everything is fine as u see i the code below.

But when i put the PATH as /usr/lib/jvm/java-6-sun/bin
i am loosing all my commands.(such a vi)

So i tried the "export" command.
But this only works for one login. When i logout and login it goes..!!

What is my solution here?

Thanks..!!

```

niteshreddy@niteshreddy-laptop:~$ echo $JAVA_HOME
/usr/lib/jvm/java-6-sun-1.6.0.20

```

---

### Post by niteshreddy on 2010-08-18
I used this link for my reference.

[http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/")

---

