---
title: "common network programming for all operating systems"
date: 2012-08-22
forum: Programming Talk
---

### Post by vikkyhacks on 2012-08-22
i am trying to learn socket programming under ubuntu, i heard that socket programming is a lot different in windows and linux, is that true ??? are there any kind of network libraries which are available in both windows and linux such that my code remains the same !!!!   ,,,

---

### Post by SledgeHammer_999 on 2012-08-22
[Boost.Asio](http://www.boost.org/doc/libs/1_51_0/doc/html/boost_asio.html)

PS: don't worry about the huge size of Boost. Most libraries are header-only. This means that your code will pull in only what it uses and its size will be minimal.

---

### Post by juancarlospaco on 2012-08-22
QtNetwork

---

### Post by dwhitney67 on 2012-08-22
Java.

---

### Post by Hetepeperfan on 2012-08-22
Well socket programming under Linux and other operating systems is rather similar, but there are subtle, and likely frustrating difference eg under windows one must first initialize some data and return values are not always the same. As application programmer one should generally not program at the BSD socket level but at a higher level like the ones mentioned above.
Therefore like the others I would like to mention a higher level of network programming interface: [zeromq ]("http://www.zeromq.org")
I like because it's fast has a good elaborate tutorial on the website and is fun to work with.

---

### Post by vikkyhacks on 2012-08-23
Well thanks for the reply .... I am not interested in using libraries but instead like dwhitney67 i am planning to choose a different programming language keeping the default standard libraries, But instead of choosing Java i am planning in for Python ... Will that be a good choice ???

---

### Post by Bachstelze on 2012-08-23
I don't have much experience with network programming but for simple things my experience is that Python works well under both Unix and Win32. However keep in mind

[http://docs.python.org/py3k/library/socket.html](http://docs.python.org/py3k/library/socket.html)

> ***Note*** Some behavior may be platform dependent, since calls are made to the operating system socket APIs.

Since Java basically creates an entire machine and operating system of its own, it's virtually impossible to beat as far as multiplatform support goes.

---

### Post by juancarlospaco on 2012-08-23
> **vikkyhacks said:**
> i am planning in for Python ... Will that be a good choice ???

PyQtNetwork

---

### Post by Bachstelze on 2012-08-23
> **juancarlospaco said:**
> PyQtNetwork

Ah, selective reading...

> **vikkyhacks said:**
> Well thanks for the reply .... I am not interested in using libraries but instead like dwhitney67 i am planning to choose a different programming language **keeping the default standard libraries**, But instead of choosing Java i am planning in for Python ... Will that be a good choice ???

---

### Post by juancarlospaco on 2012-08-23
> **Bachstelze said:**
> Ah, selective reading...

Parse Error.

You DO keep the the default standard libraries,
you dont need to remove them   ...you add PyQt.

---

### Post by vikkyhacks on 2012-08-24
I don wish to take the trouble of adding extra libraries ... It is for a small mini project I need to do this network programming ... I CANT spend time on configuring the libraries used ... I can use only the default standard libraries available ....

---

### Post by Bachstelze on 2012-08-24
There is no need to "configure" anything, you just install a package and that's it. ;)

---

### Post by SledgeHammer_999 on 2012-08-24
As I said boost.asio is header based. It will add a few KBs in your program(although the entire boost source is in the MBs range). It only requires boost.system but that is extremely small too. You could try compiling the examples here(eg the various servers) and see how big the executables are: [http://www.boost.org/doc/libs/1_51_0/doc/html/boost_asio/examples.html](http://www.boost.org/doc/libs/1_51_0/doc/html/boost_asio/examples.html)

But you said that you wanted something in python and I dont know if boost has python bindings....

---

### Post by vikkyhacks on 2012-08-24
@Bachstelze : I understand that I need to install and not configure but still INSTALL would require administrator privileges ...

@SledgeHammer_999  :  Boost sounds good, but is it available for C, I hate objects and so hate C++ ...

---

### Post by juancarlospaco on 2012-08-24
On Python you dont need Admin privileges, they are just packages, you can include the files on your own program and import them from the folder within.

You dont care abotu Python version or packages if you using a virtualenv, its 3 bash commands as much.

PIP does not require root access or modify your system Python installation.

---

