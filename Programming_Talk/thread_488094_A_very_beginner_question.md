---
title: "A very beginner question"
date: 2007-06-29
forum: Programming Talk
---

### Post by anewguy on 2007-06-29
I have looked at some of the things for programming languages to use in Linux, and I'm starting to learn towards learning JAVA.   Before I start that adventure, however, I have a couple of "dumb" questions:;)

(1) Is it easy to make a 'windowed" interface?  I want to have windows that open, buttons that can be clicked, text boxes, etc..

(2) Is it easy to interface to MySql?

Thank you for taking the time to answer some very basic questions!:D

---

### Post by pmasiar on 2007-06-29
all of it is easier in Python

1) Very simple "windowed" as you call it interface is EasyGUI: [http://www.ferg.org/easygui/](http://www.ferg.org/easygui/)

It is so simple it does not even have events :-) Real GUI would be wxPython. For games, go with pygame

2) yes. But even simpler SQL database is SQLite. It is just 1 library, without server, single-user. Just fine for developing any db/web app, when you have more than 1 user per minute, swith to real database.

Don't waste time with Java unless you have to (job, boss etc) - you can do almost anything simpler and faster in Python. What kind of app are you aiming for?

Have fun!

---

### Post by anewguy on 2007-06-30
;)Well, I've written a few personal things in Visual Basic that I want to move to a language that will allow it to run on both Windows and Linux - that's why I was thinking of Java.  However, I don't know a THING about it, and I don't know if it presents a GUI that is common across platforms.;)

These are just some little things I've written for presenting the slides and movies that my Dad took when we were kids (I scanned the 500+ slides 1 at a time, and transferred the movies using a project, a mirror box (I think it was called a Hollywood Video box or some such thing), a video camera and finally a usb device to capture the analog output of my old video camera to the computer.  My parents are still alive, but quite elderly.  They still use the computer everyday, and they look at these slides and movies through the program I wrote as a GUI front end.  There is also some family history things I have done,including a CD, which I would like to move also.  I don't want to move it to new programs, as then it would mess up my Mom and Dad, and my other relatives, who use the stuff I generate.

Long story, but maybe that gives you an idea what I'm looking for - something with a GUI that can be cross-platform.

Thanks for the replies!:D

---

### Post by ankursethi on 2007-06-30
Python is as cross platform as you can get. The GUI can be made using either PyGTK or wxPython. The native way to develop Python GUI's will be TKinkter but that looks a bit ugly if you ask me.

[http://www.python.org](http://www.python.org) to download the Windows version of the interpreter.
[http://www.diveintopython.org](http://www.diveintopython.org) to learn the language (this is for Python 2.4, but there haven't been many changes from 2.4 to 2.5 so you need not worry).
[http://www.wxpython.org](http://www.wxpython.org) for wxPython.

---

### Post by Tomosaur on 2007-06-30
Python is indeed cross platform, but if you wish to use create a GUI with Python, then Windows users will also need to download extra stuff.

Java, on the other hand, requires no extra downloads, it can create GUIs for both Windows and Linux, and although Python code looks cleaner, whether it is easier to program with is more or less a subjective matter, and you will basically just have to try both to see which you prefer. Java sounds like the language you need to me - cross platform, fairly straightforward, and can create GUIs with no extra baggage needed.

---

### Post by pmasiar on 2007-06-30
Python from activestate.com comes will most if not all extra modules needed for Windows. Because, as may know, it was even financed by MSFT for a while... :-)

While I possibly may agree with Tomosaur about using Java at large apps, Java is language preferred by Fortune 500 companies, and for good reason: it is not very agile. And it's API is enormous and has babylonian complexity. I would suggest to anewguy to try develop something simple (print the song "99 bottles on the wall") in both Python and Java to get the taste of both and compare. Starting with Python... :-)

I just do not see how OP's app is the F500 case, appropriate match for Java.

---

### Post by gpolo on 2007-06-30
You can do GUIs in Python with Tk too (just to answer for Java needing "nothing").
Also, don't forget about PyQT

---

### Post by samjh on 2007-07-01
Back to answering the OP's question, which was aimed at JAVA, **not Python** ;) :

> **anewguy said:**
> I have looked at some of the things for programming languages to use in Linux, and I'm starting to learn towards learning JAVA.   Before I start that adventure, however, I have a couple of "dumb" questions:;)

(1) Is it easy to make a 'windowed" interface?  I want to have windows that open, buttons that can be clicked, text boxes, etc..

(2) Is it easy to interface to MySql?

Thank you for taking the time to answer some very basic questions!:D

Yes, both are quite easy.

Java will take some time to learn, since your only experience is VB.  The syntax is different, and Java is more powerful than VB.

But after you've learnt Java basics, it is very easy to create a GUI and to communicate with databases, using the Swing GUI library and JDBC, respectively.

Swing GUIs have become even easier to create by using Netbeans ([www.netbeans.org](www.netbeans.org) ), and its "Matisse" GUI editor, which is similar to VB's Form Designer.

JDBC is probably the easiest and widely-supported database libraries I've ever seen.

Java's Swing GUI is uniform across all platforms, if you set it to the cross-platform Look and Feel, which is the default setting.

Java Tutorial: [http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)

Netbeans: [http://www.netbeans.org/products/](http://www.netbeans.org/products/)

---

### Post by pmasiar on 2007-07-01
> **samjh said:**
> Back to answering the OP's question, which was aimed at JAVA, **not Python** ;) :


Not so. OP was "leaning" towards java because he does not know any better. You do know, so failing to suggest equally valid but simpler solution (Python) is miss-advice to OP, IMHO.

There is difference between solving OP problem and answering question: I strive to respond to "spirit" of the question, not it's letters. It is like in programming: give users what they need, not what they ask for (and explain them all the options: don't let them design system, it is developer's responsibility).

---

### Post by Tomosaur on 2007-07-01
> **pmasiar said:**
> Not so. OP was "leaning" towards java because he does not know any better. You do know, so failing to suggest equally valid but simpler solution (Python) is miss-advice to OP, IMHO.

There is difference between solving OP problem and answering question: I strive to respond to "spirit" of the question, not it's letters. It is like in programming: give users what they need, not what they ask for (and explain them all the options: don't let them design system, it is developer's responsibility).

Yes, but there's also a difference between mindless evangelism, and sensible suggestions :P

**You** think Python is the best (seemingly in every situation!). This is not a bad thing, but the OP was actually asking questions about Java (how easy it is to make GUIs etc). It's all well and good recommending Python as a possibly better solution, but if you don't actually answer the questions he / she asked, then frankly, your response isn't all that useful. I find the best way to respond to such threads is to first and foremost answer the questions, then state opinions about alternative solutions. Python is not the best for every situation. Your approach is, frankly, a little egotistical. Give the OP what he asks for before going off on some personal tangent.

---

### Post by pmasiar on 2007-07-01
> **Tomosaur said:**
> Yes, but there's also a difference between mindless evangelism, and sensible suggestions :P

**You** think Python is the best (seemingly in every situation!). 

We had polls about that, and Python has usually 50% or more votes. So it is not only me. It is also Mark Shuttleworth and Ubuntu, and it Google.

Is it my problem that for kind of people asking question in this forum, Python usually *is* better choice? I cannot help it. :-)

> OP was actually asking questions about Java (how easy it is to make GUIs etc).  [ ... ] but if you don't actually answer the questions he / she asked, then frankly, your response isn't all that useful. 

I did answered second question. A "yes" is answer. :-)
I agree, I should mention also wxPython for 1st question.

> Python is not the best for every situation. 

I agree. If your college professor asks for Java, code, Python might not work :-)

---

### Post by kknd on 2007-07-01
> **anewguy said:**
> I have looked at some of the things for programming languages to use in Linux, and I'm starting to learn towards learning JAVA.   Before I start that adventure, however, I have a couple of "dumb" questions:;)

(1) Is it easy to make a 'windowed" interface?  I want to have windows that open, buttons that can be clicked, text boxes, etc..

(2) Is it easy to interface to MySql?

Thank you for taking the time to answer some very basic questions!:D

1) Yes. You can use the bundled Swing (that its great) or other GUI toolkits (including gtk with the proper bindings).

2) Yes.

---

### Post by anewguy on 2007-07-02
;)Indeed, I was just asking about Java.  I appreciate the other input, but I really didn't want things to become a p***ing contest about who thinks what is better.  Having my background, I know that everyone finds a language that is "the" language as far as they are concerned.  Please just remember it is only your opinion - please don't quote surveys, etc., as I could come up with similar results for all of the languages I mentioned earlier.

What I specifically wanted to know is that since Java is cross-platform can you easily access MySql and can you create a GUI that is accessable from Windows and Linux.  Additionally, I like to know if the GUI is top-down or if it is event driven (I'd much prefer event driven).

Thanks for all of the replies!:)

---

### Post by samjh on 2007-07-02
> **anewguy said:**
> What I specifically wanted to know is that since Java is cross-platform can you easily access MySql and can you create a GUI that is accessable from Windows and Linux.  Additionally, I like to know if the GUI is top-down or if it is event driven (I'd much prefer event driven).

It's event-driven.

---

### Post by Tomosaur on 2007-07-02
Here is some information about using MySQL with Java:
[http://dev.mysql.com/usingmysql/java/](http://dev.mysql.com/usingmysql/java/)

However, Java does have database stuff in its API. The framework is all there, but you may need to fiddle (or follow the information on the page I just linked to) to get the exact results you need.

---

### Post by Praill on 2007-07-02
> **Tomosaur said:**
> Python is indeed cross platform, but if you wish to use create a GUI with Python, then Windows users will also need to download extra stuff.

Java, on the other hand, requires no extra downloads, it can create GUIs for both Windows and Linux, and although Python code looks cleaner, whether it is easier to program with is more or less a subjective matter, and you will basically just have to try both to see which you prefer. Java sounds like the language you need to me - cross platform, fairly straightforward, and can create GUIs with no extra baggage needed.
I'd have to agree with Tomosaur. While many prefer python, the windows install for any GUI app written in it is messy and unorthadox to say the least. This is why many people concerned with platform compatibility choose java. While java is.... java... and its not the funnest thing to work with, it still makes things easier for the end user than python does.

---

### Post by runningwithscissors on 2007-07-03
> **anewguy said:**
> What I specifically wanted to know is that since Java is cross-platformJava is "cross-platform" in its own special way. Please take that claim with a hint of salt. It's not a bad language to program in, however.
> **anewguy said:**
> Can you easily access MySql and can you create a GUI that is accessable from Windows and Linux.Yes.
> **anewguy said:**
> Additionally, I like to know if the GUI is top-down or if it is event driven (I'd much prefer event driven).All modern GUI's are event driven. That includes the ones that are distributed as Java libraries.

---

