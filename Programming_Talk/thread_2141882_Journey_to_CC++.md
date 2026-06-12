---
title: "Journey to C/C++"
date: 2013-05-04
forum: Programming Talk
---

### Post by mmsmc on 2013-05-04
Hello
I am attempting to learn C++ and am looking for good free online books or other various sources that can help on my journey. I am currently proficiant in both java and matlab and have a strong background in object oriented progrmming. Any help would be appreciated. Also whiile on the topic, what Linux OS is most recomended for programming, that is small enough to fit o a usb drive, while leaing the smallest amount of trace on the host computer.

Thank you
mmsmc

P.S sorry for the horrible spelling!

---

### Post by MG&amp;TL on 2013-05-04
I learned primarily from Bjarne Stroustrup's *Programming: Principles and Practice Using C++*, which is excellent, although the chapters on graphical programming can, I feel, be mostly ignored. I felt it was worth buying it, but I can't really imagine it would be too hard to find it second-hand, loan it off someone, or find chapters on the internet.

Any linux operating system is good for programming, the one you're using now is likely fine, providing it can be installed onto a USB. You'll want to install a compiler (*g++* and *clang* are popular), which you invoke in a similiar fashion to the java compiler.

Quick hint: treat C and C++ as different languages, not C++ as a superset of C. (I notice the use of *C/C++* in your question). They are quite different in several ways that will provide gotchas later.

---

### Post by overcast on 2013-05-04
Robert Lafore has two good books on C++ and C++ OOPS. I have learned C++ using  these two books. I found them good so far.

---

### Post by SledgeHammer_999 on 2013-05-04
IMHO the best free online C++ tutorial: [http://www.cplusplus.com/doc/tutorial/](http://www.cplusplus.com/doc/tutorial/)

---

### Post by trent.josephsen on 2013-05-04
> **MG&TL said:**
> Quick hint: treat C and C++ as different languages, not C++ as a superset of C. (I notice the use of *C/C++* in your question). They are quite different in several ways that will provide gotchas later.
Quite so. I do not know C++, but I have seen C code written by C++ programmers, and it is not pretty. I won't discourage you from learning whatever language you choose, but if you do choose to learn C++, I will advise you to avoid C. They mostly live in different worlds anyway as far as application domains go; there's not as much overlap as there used to be, so knowing both would probably not be all that useful.

Another advisory: I don't need to be an expert on the subject to know that there are an awful lot of **really bad** C++ resources out there. It's the curse of popular languages, and C++'s complexity doesn't help. So be careful and don't pick up just any book because it has good reviews on Amazon; get the opinion of someone who knows the language. [Book reviews by ACCU members](http://accu.org/index.php?module=bookreviews&func=browse) are generally well-written and defended by experience.

(I am not affiliated with, nor do I endorse ACCU; but I have found the book reviews to be of high quality.)

---

### Post by mmsmc on 2013-05-04
Thank you all for your reply, i will be checking each of the sources.

---

### Post by nvteighen on 2013-05-05
OK, we're talking about C++ here, but I wanted to contribute by adding to list the C resource I think that is the best, the GNU C tutorial: [http://www.crasseux.com/books/ctutorial/](http://www.crasseux.com/books/ctutorial/) OK, it's not C99, not even C11, but it covers the basics you have to know, in a very very clean and concise way. If you become interested in C in the near future, please take a look on it :)

I agree with the other posts above that you **must** treat C and C++ as obviously related but **completely different** languages living in two completely different "worlds". C is much better suited for system utilities, kernels, writing libraries that you want to make them compatible with lots of programming languages, when you need to easily interface with Assembly, etc. C++ is primarily used when you need something as fast as C, but with OOP. Granted, I don't like neither C++ or its OOP model, but it has its uses.

Learning both won't hurt you at all, of course ;)

---

