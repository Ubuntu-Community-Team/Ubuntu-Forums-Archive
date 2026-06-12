---
title: "eclipse for j2ee"
date: 2009-02-23
forum: Programming Talk
---

### Post by sainageswar on 2009-02-23
i already have eclipse installed. but it is not having any facility for j2ee
how to add this facility

---

### Post by jespdj on 2009-02-23
Very simple:

1. Download it from the [Eclipse website](http://www.eclipse.org/).

2. Unpack the archive in any directory you like:
```
tar xfz eclipse-jee-ganymede-SR1-linux-gtk.tar.gz
```

3. Run the 'eclipse' executable in that directory.

Ofcourse you do need to have Java installed before you do this:
```
sudo apt-get install sun-java6-jdk
```

---

### Post by CptPicard on 2009-02-23
Do you absolutely have to use Eclipse? Netbeans' J2EE integration is just absolutely awesome.

---

### Post by StutteringJohnSmith on 2011-03-22
I am trying to do this but I am getting the following error:

Package sun-java6-jdk is not available

can someone help me

---

### Post by PaulM1985 on 2011-03-22
Have you tried doing

sudo apt-get install sun-java6-jdk

at command line?

Paul

---

### Post by rabbitdaone on 2011-03-22
You can also install java from the Ubuntu Software center

---

### Post by StutteringJohnSmith on 2011-03-22
but iis it the Java JEE version

---

### Post by Some Penguin on 2011-03-23
Would it have been repeatedly suggested as appropriate, without correction, if it weren't?

---

### Post by urbuddytintin on 2013-02-07
I tried this command but nothing is happening it is saying resource temporarily unavailable.
sudo apt-get install sun-java6-jdk

---

### Post by Cheesemill on 2013-02-07
Due to licensing issues Oracle (Sun) Java is no longer available in the standard repositories. To install it use the following commands...
```
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer
```

---

### Post by slickymaster on 2013-02-07
> **CptPicard said:**
> Do you absolutely have to use Eclipse? Netbeans' J2EE integration is just absolutely awesome.

+1

You should definitely give Netbeans a try. NetBeans provides the best out-of-the-box experience for Java EE development, deployment, and debugging and already started providing support for several Java EE 7 features.

---

