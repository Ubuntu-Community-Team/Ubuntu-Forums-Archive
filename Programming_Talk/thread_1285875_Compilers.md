---
title: "Compilers"
date: 2009-10-08
forum: Programming Talk
---

### Post by Dark Sorrow on 2009-10-08
Can someone give me links for the following compilers.
(1) C and C++
(2) Java(entire package) and J2ME
(3) Ada 95 or Ada 2005
(4) C# 2008

---

### Post by XCan on 2009-10-08
I'm not sure I understood you completely, unusual question:

1) gcc, g++ are installed by default (you'll probably want the build-essential package though).
2) javacc can be installed through synaptics (you'll probably want the whole SDK 
though which too can be instealld through synaptics).
3) gnat can be instealled through synaptics.
4) Doubt that exists, C# is for .net.

---

### Post by bapoumba on 2009-10-08
Moved to PT.

---

### Post by falconindy on 2009-10-08
> **XCan said:**
> I'm not sure I understood you completely, unusual question:

1) gcc, g++ are installed by default (you'll probably want the build-essential package though).
2) javacc can be installed through synaptics (you'll probably want the whole SDK 
though which too can be instealld through synaptics).
3) gnat can be instealled through synaptics.
4) **Doubt that exists, C# is for .net.**
You would be mistaken. [MonoDevelop](http://monodevelop.com/) is an IDE for C# in Linux. It uses xMCS as its compiler.

---

### Post by Can+~ on 2009-10-08
Smells like homework.

---

### Post by divyesh456 on 2009-10-08
A compiler converts a programming language into code that a computer can understand.

The advantage of this is that once this is done, you can run the computer code and not have to worry about processing the original code. 

There are languages that dont have a compiler. When you run that code, it has to get its syntax checked, then it has to go through the processes to figure out how to run the code, then runs it. This is done every time you run this code.

If you program in a language that uses a compiler, it speeds up the program by not having to redo figuring out how to run the code every time.
________________________________________________________
[hair dressing games](http://www.y3.com/search-results/18354/hair-dressing-games)  [SMART LIPOSUCTION](http://www.laserlipoguide.com/)

---

### Post by jespdj on 2009-10-09
For C, C++, install gcc and g++:
```
sudo apt-get install build-essential
```

To install the JDK (Java Development Kit):
```
sudo apt-get install sun-java6-jdk
```
Don't know about J2ME.

Use MonoDevelop for C#:
```
sudo apt-get install monodevelop
```

---

