---
title: "Which would be the best language for my project?"
date: 2009-04-21
forum: Programming Talk
---

### Post by lovinglinux on 2009-04-21
I have created a Firefox add-on, which is a media center extension (see link in my sig). It basically relies on bash scripts using several Linux tools like xmlstarlet and sqlite3 for database related stuff and other common tools like sed, sort, find and others.

I want to take this project a little bit further and make it platform independent. So I was wondering which programming language would be the best to perform the same functionalities on different OSs? It doesn't have to be dependent on Firefox, but would be nice if I could keep it as an extension.

Python is in the top of my list, but I also have personal interest on learning C++. Is Python capable of doing the same stuff as those cli tools I have been using so far? If I use python scripts instead of bash scripts, it would be possible to run the same code on a Windows machine?

---

### Post by Anthon on 2009-04-22
I have been using PYthon as a cross platform tool for over 10 years now. It can certainly do what you need. There are several approaches to that.
XML handling and sqlite are libraries that come with Python, so does regulare expression searching/replacing (it is not a part of the language). Sorting is build in. 
What I sometimes have done is use Python as a direct replacement for bash, by calling all the original programs bash was using, and capturing and passing on the output. This requires little effort if the output fits in memory. The syntax for that is slightly more verbose in Python as in bash, but once you have done it once it is mostly copy and paste. After that you can clean up, until you no longer feel like doing so.
As long as you use Python included libraries that are available on all the platforms that you want to target (don't worry, most are, except those targetting OS specific functions) programs will be portable.

---

### Post by lovinglinux on 2009-04-22
Thanks.

---

### Post by Kilon on 2009-04-22
> **lovinglinux said:**
> Thanks.

choosing python wont mean that you are going to turn your back to c++. Python loves C++ and can work hand in hand with it in many different ways. Afterall Python is written in C++ and so is most of its libraries. There are also tools that can make the whole process almost automatic (or even entirely automatic). 

The only platform that can be a bit demanding is MACOS , but fortunately both java and python are fully supported by Apple. C++ is not actually supported by Apple as it uses Objective C , which of course is very similar to C++. It is something you have to keep in mind if you decide to go 100% C++. Maybe there is a workaround to bring C++ code unchanged in macos and still be able to access native MACOS libraries, I do not know any but I assume there should be some.

---

