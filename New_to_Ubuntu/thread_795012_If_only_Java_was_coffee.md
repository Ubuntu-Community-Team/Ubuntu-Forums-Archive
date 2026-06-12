---
title: "If only Java was coffee"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by expatCM on 2008-05-15
Does anyone understand Java?

If I run  sudo update-java-alternatives -l  I get this list 
```

java-6-openjdk 1061 /usr/lib/jvm/java-6-openjdk

java-6-sun 63 /usr/lib/jvm/java-6-sun

java-gcj 1042 /usr/lib/jvm/java-gcj


```

My default from java -version is 
```

java version "1.6.0_06"

Java(TM) SE Runtime Environment (build 1.6.0_06-b02)

Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)

```

and if I run sudo update-alternatives –config java
```

 +        1    /usr/lib/jvm/java-6-openjdk/jre/bin/java

*         2    /usr/lib/jvm/java-6-sun/jre/bin/java

          3    /usr/bin/gij-4.2

          4    /usr/lib/jvm/java-gcj/jre/bin/java

```

So in terms of knowing whether I am running what I should be running or what would be best for me to run I have not got a clue.

Just to make life more interesting ....  when I try to use Webmin to open the File Browser which is Java based it does not open.  Used to with 7.10 but not with 8.04.

Anyone with experience of this maze?

---

### Post by SupaSonic on 2008-05-15
I personally use
```
/usr/lib/jvm/java-6-sun
```
The rest might not work or behave in a strange way

---

### Post by kpkeerthi on 2008-05-15
java-6-openjdk, java-6-sun, java-gcj are the Java VM implementations. And you seem to have them all installed. But the default Java implementation ubuntu is using in your case is Sun's and that's what the *star indicates in the output of **update-alternatives -config java** command. **java -version** prints the version information of the Java VM currently active.

[http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)
[http://openjdk.java.net/](http://openjdk.java.net/)
[http://java.sun.com/javase/](http://java.sun.com/javase/)

In my opinion (being a Java/J2EE developer) Sun's implementation is the most complete one.

---

### Post by expatCM on 2008-05-16
So basically I am whole ....  good to hear, thank you.

The only thing I need to address is why the webmin file browser does not work with Ubuntu 8.04 but perhaps that is a separate issue ....

---

### Post by forrestcupp on 2008-05-16
If you have sun-java6 installed, you probably need to remove any openjdk package.  They don't work well together.  If you're using sun, you don't need the open version.  So remove them, then see if your app will open.

---

### Post by expatCM on 2008-05-16
Thanks for your suggestion .....  I just did it ....

---

### Post by forrestcupp on 2008-05-16
> **expatCM said:**
> Thanks for your suggestion .....  I just did it ....

Did it work?

---

### Post by expatCM on 2008-05-16
I had to reboot ...... and I had to finish something off first ...

But 

TOTALLY BRILLIANT

the file browser in Webmin is back to normal operation.

This is just great ....   my fingers have been getting tired on the command line ....

Thank you very much indeed ...  :)

---

