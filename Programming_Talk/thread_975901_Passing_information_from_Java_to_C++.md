---
title: "Passing information from Java to C++"
date: 2008-11-08
forum: Programming Talk
---

### Post by pcman312 on 2008-11-08
I have quite a bit of experience with Java and C++ separately, however I am looking to write a program using OpenGL (which I also have experience with). It is going to involve file manipulation, and I'd like to make the program cross-platform. I'm wondering if there's an effective way to pass information from Java to C++. I know there is JNI (which I don't have experience with, but I do have a book with some information on it) however I'm not sure if that's the most efficient & effective method.

My question is, is there a way to pass information from a Java program to a C++ program? I'm thinking either running the C++ program, which then executes a Java program that waits for information from the C++ program, then gives some file information back to the C++ program and then continues to wait. Or, start the C++ program, which then executes the Java program whenever it needs to be run.

There is also JOGL, but I'd like to have the program run as quickly as I can get it to, which is why I'd like to use C++ for the storing and displaying of the OpenGL information.

---

### Post by doorman on 2008-11-08
Maybe I missed your point, but you say you want to make an application using Java and C++, but C++ is not a cross-platform language.

Answering your original question, have you considered System V messages?

---

### Post by pcman312 on 2008-11-08
> **doorman said:**
> Maybe I missed your point, but you say you want to make an application using Java and C++, but C++ is not a cross-platform language.
True, and I intend to write the C++ portion as system-independent as possible and ultimately compile it on my Ubuntu machine as well as my XP machine. I want to use Java to extract information about the file structure of a computer and then pass that information to a (faster running) C++ OpenGL program.

> **doorman said:**
> Answering your original question, have you considered System V messages?
If you're referring to using system(), or even using P_OPEN(), I have, but that would require the Java program to output information to the console or to a file, then parsing that information again in C++, which is slower than I'd like it to be.

---

### Post by slavik on 2008-11-08
what about using OpenGL from within Java?

---

### Post by pcman312 on 2008-11-09
> **slavik said:**
> what about using OpenGL from within Java?
You mean JOGL that I mentioned in my first post? ;-)

---

### Post by SeanHodges on 2008-11-10
> **pcman312 said:**
> My question is, is there a way to pass information from a Java program to a C++ program? I'm thinking either running the C++ program, which then executes a Java program that waits for information from the C++ program, then gives some file information back to the C++ program and then continues to wait. Or, start the C++ program, which then executes the Java program whenever it needs to be run.

We use a simple TCP socket in one of our products at work for this, which is a simple but effective way of achieving IPC. There are plenty of options for communicating between processes (DBUS and CORBA spring to mind...)

> There is also JOGL, but I'd like to have the program run as quickly as I can get it to, which is why I'd like to use C++ for the storing and displaying of the OpenGL information.

I don't know much about JOGL, but bear in mind you should consider the possible performance penalties of IPC as well. You *may* find that the communication mechanism between the 2 programs (including transport latency, shared resource blocking, race condition handling, etc) results in a bigger performance penalty than just writing the whole thing in a single program.

---

### Post by slavik on 2008-11-10
> **pcman312 said:**
> You mean JOGL that I mentioned in my first post? ;-)
I didn't read the WHOLE post. :oops:

you could use pipes (fifos), or what you could do is port the library over. C++ isn't that much worse than Java when it comes to parsing text.

---

### Post by snikrot on 2008-11-10
You might want to learn CORBA. This middleware can program from C to Java or from C to Delphi however you'd want it.

---

### Post by SeanHodges on 2008-11-10
Out of curiosity, I looked up JOGL and what it comprised of. From Wikipedia:

> The base OpenGL C API is accessed in JOGL via Java Native Interface (JNI) calls. As such, the underlying system must support OpenGL for JOGL to work.

... and the JOGL user documentation:

> Jogl is a Java programming language binding for the OpenGL 3D graphics API. It supports integration with the Java platform's AWT and Swing widget sets while providing a minimal and easy-to-use API that handles many of the issues associated with building multithreaded OpenGL applications. 

From my understanding, JOGL implements pretty much what you are trying to achieve here; it provides a JNI binding to the base OpenGL API. The low-level work is still being computed by the highly optimised OpenGL-compatible driver or software renderer...

I might be missing a trick here, but writing a program in Java which drives OpenGL through a C++ wrapper seems like it completely overlaps the purpose of JOGL, and any performance benefit would be essentially down to your choice of binding language (e.g. performance of CORBA compared to JNI), which would be marginal and probably not worth the extra effort of writing a whole new wrapper for...

If your intent is to write the majority of the program in C++ in pursuit of performance, I'd then have doubts about the purpose of using Java at all. Writing the whole thing in C++ would be far simpler, and bypassing the whole concept of wrappers and IPC would improve both performance and memory footprint.

---

### Post by pcman312 on 2008-11-10
> **SeanHodges said:**
> Out of curiosity, I looked up JOGL and what it comprised of. From Wikipedia:



... and the JOGL user documentation:

 

From my understanding, JOGL implements pretty much what you are trying to achieve here; it provides a JNI binding to the base OpenGL API. The low-level work is still being computed by the highly optimised OpenGL-compatible driver or software renderer...

I might be missing a trick here, but writing a program in Java which drives OpenGL through a C++ wrapper seems like it completely overlaps the purpose of JOGL, and any performance benefit would be essentially down to your choice of binding language (e.g. performance of CORBA compared to JNI), which would be marginal and probably not worth the extra effort of writing a whole new wrapper for...

If your intent is to write the majority of the program in C++ in pursuit of performance, I'd then have doubts about the purpose of using Java at all. Writing the whole thing in C++ would be far simpler, and bypassing the whole concept of wrappers and IPC would improve both performance and memory footprint.
Yea, that's pretty much what I discovered after I looked into JOGL in more depth. I think I'm going to stick to one or the other, but I haven't decided which yet. I think I'm going to do a mockup of the program in each and see if Java is too slow for what I want it to do.

Thanks everyone for your help!

---

### Post by SeanHodges on 2008-11-11
> **pcman312 said:**
> I think I'm going to do a mockup of the program in each and see if Java is too slow for what I want it to do.

Sounds like a good plan, I'd be interested to hear your conclusions as well.

---

