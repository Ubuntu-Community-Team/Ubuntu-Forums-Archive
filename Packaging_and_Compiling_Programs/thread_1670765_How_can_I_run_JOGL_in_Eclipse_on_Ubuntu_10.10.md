---
title: "How can I run JOGL in Eclipse on Ubuntu 10.10"
date: 2011-01-19
forum: Packaging and Compiling Programs
---

### Post by Bor1s on 2011-01-19
I have downloaded the gluegen-rt.jar and jogl.jar plus libgluegen-rt.so, libjogl.so, lobjogl_awt.so, libjogl_cg.so. 
I have the latest version of Eclipse, Java and Ubuntu. 
I created a new project 
I created a lib folder, where I copied the JARs and in the root of the project I copied the *.so files.
I added the JARs in my project through Properties->Build Path->Add External JARs
I tried to build and run the app but I got Exception in thread "main" java.lang.UnsatisfiedLinkError: no gluegen-rt in java.library.path . So I set the Native Library Locations for both JARs to be myproject/lib.

Same difference...what am I missing? I will add that I actually got it running once...and that was it...I don't know how, nor why it didn't run the second time. The OpenGL is ok, because I have no problem running it in C/C++.

---

### Post by syed.rakib.al.hasan on 2011-01-28
Hey,
could you solve this matter? 
i dont know how to get started with JOGL on Ubuntu

---

### Post by scribu on 2011-03-15
Here's how I did it:

1. Install the libjogl bindings from the repos:

```
sudo apt-get install libjogl-java
```

2. In Eclipse, go to Project -> Properties -> Java Build Path -> Libraries

3. Click "Add External JARs..." and select ```
/usr/share/java/jogl.jar
```

4. Click "Add External JARs..." and select ```
/usr/share/java/gluegen-rt.jar
```

Done.

---

