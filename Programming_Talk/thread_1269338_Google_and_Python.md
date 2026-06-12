---
title: "Google and Python"
date: 2009-09-18
forum: Programming Talk
---

### Post by hoboy on 2009-09-18
What google used python for ? is it the main developement language/Tools ? what type of applications they develope in python ?

---

### Post by pepperphd on 2009-09-18
Youtube is written in Python.

---

### Post by phrostbyte on 2009-09-18
Apparently a lot of things, as it is one of the three languages you are expected to be familiar with as a software engineer at Google (C++, Java, Python).

---

### Post by Can+~ on 2009-09-18
Google also develops back to python, search for their project "[Unladen Swallow]("http://arstechnica.com/open-source/news/2009/03/google-launches-project-to-boost-python-performance-by-5x.ars")".

---

### Post by karlmp on 2009-09-18
if that project goes through, python will stomp java.

---

### Post by Can+~ on 2009-09-18
> **karlmp said:**
> if that project goes through, python will stomp java

Very unlikely.

---

### Post by falconindy on 2009-09-18
> **Can+~ said:**
> Very unlikely.
No, no. Hear me out. All I want my app to do is display a window that says 'hello world'. I'll just write an inordinately long if/else statement to identify the OS and then pull in the appropriate API calls to create the window and write to it! I CAN'T FAIL!!!!!

JAVA BE GONE!!

...yeah right. Just because you see the words "virtual machine" doesn't mean it has anything to do with Java.

---

### Post by angryfirelord on 2009-09-18
> **karlmp said:**
> if that project goes through, python will stomp java
Mmm, I don't think so. For all intents and purposes, Python is a RAD tool and a scripting language that allows you to build applications quickly. Java is a more traditional programming language that is heavily used on the server side of things (like J2EE and JSP). It does a lot more than display applets to web pages. :)

---

### Post by wmcbrine on 2009-09-19
> **falconindy said:**
> All I want my app to do is display a window that says 'hello world'. I'll just write an inordinately long if/else statement to identify the OS and then pull in the appropriate API calls to create the window and write to it!If that's meant to be the Python experience... just use Tkinter. Not necessarily the prettiest, but then neither are Java's GUIs.

Although I have actually written a dual PyGtk/Tkinter program, switching at runtime, which I thought was pretty sweet.

---

### Post by Can+~ on 2009-09-19
> **falconindy said:**
> No, no. Hear me out. All I want my app to do is display a window that says 'hello world'. I'll just write an inordinately long if/else statement to identify the OS and then pull in the appropriate API calls to create the window and write to it! I CAN'T FAIL!!!!!

JAVA BE GONE!!

...yeah right. Just because you see the words "virtual machine" doesn't mean it has anything to do with Java.

Care to explain? I'm not quite sure what you said there.

---

### Post by falconindy on 2009-09-19
My implication is that, unlike Java, Python scripts aren't going to work universally across every platform. I don't know a **lot** of Python, but I'd imagine that GUI elements in particular would cause some issues.

---

### Post by Can+~ on 2009-09-19
> **falconindy said:**
> My implication is that, unlike Java, Python scripts aren't going to work universally across every platform. I don't know a **lot** of Python, **but I'd imagine that GUI elements in particular would cause some issues**.

It would cause some issues, as GUI elements require the proper binding, except for [TK]("http://en.wikipedia.org/wiki/Tk_%28framework%29") which comes packed with python.

Both Python and Java are cross platform, both are interpreted (compiled locally), but that never implies that it will work completely right or being "universal", because some of the most subtle differences can have a huge impact. There's a recurring joke  "Write Once, Debug Everywhere".

In fact, I think I've rarely had any issues while porting python to other platforms, except for the wrongly hard coded paths, or that Windows requires having the open("filename", "rb") when opening binary files, and Linux is fine with both.

You sound like a blub programmer, some functional paradigm flakes in your breakfast could help you with that.

---

### Post by falconindy on 2009-09-19
> **Can+~ said:**
> You sound like a blub programmer, some functional paradigm flakes in your breakfast could help you with that.
It's not for lack of interest in learning other languages, it's just that there's only so many hours in a day.

---

### Post by wmcbrine on 2009-09-20
> **falconindy said:**
> I don't know a **lot** of Python, but I'd imagine that GUI elements in particular would cause some issues.You'd imagine wrongly. A Python program using Tkinter will work without modification on all major platforms.

Next time maybe learn about it rather than just imagining, eh?

---

### Post by nvteighen on 2009-09-20
What that project seems to be about is about replacing implementation rather than interface. The language will be unaffected... The VM will be. So, whatever Python code you have will still work there... maybe faster and more efficiently, but nothing else.

---

