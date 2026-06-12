---
title: "programming windows apps on linux -- java or python (PyGTK)??"
date: 2008-05-20
forum: Programming Talk
---

### Post by eragon100 on 2008-05-20
Java runs on all platforms, but is it possible to program java apps without using system-specifif API calls, libraries and stuff like that?

It can be done with pyGTK, so I guess java can do it as well. The point is that I have to write a windows program for school, and I need to do bug-testing and such. I don't think wine is reliable enough for that. With pyGTK the code itself is cross-platform, including the GUI.

Is this true with java as well?

---

### Post by lisati on 2008-05-20
I don't know the specifics of Java or pyGTK: in C or C++ one way would be to start it as a console program, and structure it in such a way that the necessary GUI elements could be easily added.

---

### Post by eragon100 on 2008-05-20
The "program" is just a small multiple choice test. And it's made for 12 year olds. I don't they want to use a @##!(#@!(#@#(!@#! terminal to make a test :lolflag:

BTW, I still have to test it on windows. Change of plans. I will use microsoft visual basic 6.0 professional, runs great under wine. Simple programs you make are also almost guaranteed to work, so this problem is solved :popcorn:

---

### Post by pdwerryhouse on 2008-05-20
Java is designed to be "write once, run anywhere". It doesn't have system specific APIs and libraries. Not that I know of, anyway. Write a program in Java on Linux and you'll have a very good chance that it'll work fine under Windows.

---

### Post by Phenax on 2008-05-20
Most high-level scripting languages and their GUI toolkit bindings are multi-platform. Using Glade Designer (GTK) or QT Designer (QT) you can easily carve out GUIs graphically, and then use associated tools to convert the code to your language of choice (Python, Ruby, etc).

Quite a few choices..

---

### Post by panayk on 2008-05-20
> **eragon100 said:**
> Java runs on all platforms, but is it possible to program java apps without using system-specifif API calls, libraries and stuff like that?

It can be done with pyGTK, so I guess java can do it as well. The point is that I have to write a windows program for school, and I need to do bug-testing and such. I don't think wine is reliable enough for that. With pyGTK the code itself is cross-platform, including the GUI.

Is this true with java as well?

I'm pretty sure that if
* you write your GUI in, say, Swing
* compile the program with e.g. "Sun's javac 1.6.0_03" and
* it runs successfully under "Sun's java 1.6.0_03" in Linux
then it is guaranteed to also run under the same JRE in Windows or any other platform where that virtual machine is available.

You will probably run into trouble is you use a different compiler and different JRE (like gcj+sun_java or sun_javac+gij) but if you stick to the standard APIs it should take no more that a recompilation to get around this.

---

### Post by Zugzwang on 2008-05-20
> **panayk said:**
> I'm pretty sure that if
* you write your GUI in, say, Swing
* compile the program with e.g. "Sun's javac 1.6.0_03" and
* it runs successfully under "Sun's java 1.6.0_03" in Linux
then it is guaranteed to also run under the same JRE in Windows or any other platform where that virtual machine is available.


As far as the OP's question is concerned: Yes, Java would fulfill your needs here. In fact, when you package your .jar file, it suffices to double-click on your .jar file in the Windows explorer to start the program provided that:
[LIST]
[*]A Java version is installed whose major version number (e.g. 1.6) is at least as high as the version number of the JDK you compiled your program with (ok, you can get around this, but that's not recommended)
[*]Your program doesn't consume too much RAM (16MB is default) - More memory-intensive programs you have to run it from the command line or use a starting script or use some JAVA-exe packager, which reduces cross-platformness and almost all such packagers do not allow command line arguments)
[/LIST]

Also, panayk is not totally right - To ensure cross-platform runnability, you also have to write your program accordingly, that means no unportable system() calls, using File.SeparatorChar whenever applicable instead of patching together filenames using '\' or '/' literals and so on. But this applies to Python as well (as far as I know, at least the first issue is definitely true).

---

### Post by vexorian on 2008-05-20
> Java runs on all platforms, but is it possible to program java apps without using system-specifif API calls, libraries and stuff like that?
That's like the only reason Java was invented for.

--
What I do:
virtualBox to host an IDE, compile and test there.

---

### Post by [h2o] on 2008-05-20
Python + pyGTK on Windows does work, but it does imply a few extra steps to build it on Windows.

No matter how much more I enjoy programming in Python over Java, I would choose the latter next time I do any GUI-based programs that need to run on Windows and Linux.

Also a bit of advice: Consider character encodings and line endings if you are looking at doing any kind of file operations.

---

