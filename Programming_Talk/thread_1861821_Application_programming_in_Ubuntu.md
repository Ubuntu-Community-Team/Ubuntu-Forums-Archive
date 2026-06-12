---
title: "Application programming in Ubuntu"
date: 2011-10-16
forum: Programming Talk
---

### Post by rwslippey on 2011-10-16
Hello,

I want to try something new.. so I'd like to jump in and learn a new programming language, in linux of course.

I'd like to learn to program applications with a GUI interface that'll run across multiple linux variations as well as be simple to port to windows. At first Java came to mind, but would java be the best solution here?

I've search the web and came up with a lot of results and I am just looking for clarification of the pros VS Cons or different languages.

Also noticed GTK+ any suggestions their?

Just looking for somewhere to start, maybe a book anyone would suggest?

Thanks

---

### Post by krishnandu.sarkar on 2011-10-16
Depends on which programming language you prefer.

You can use Qt if you prefer C++
You can use GTK+ if C is your choise
Or Java as you said.

Other than these, you can also use other language bindings like Java, Python for Qt and GTK+

---

### Post by gsmanners on 2011-10-16
GTK doesn't really look that great in Windows. I think I'd use either Qt or wxWidgets. It's really that crossplatform GUI that you'll want to choose first, I think. Then pick a good language for that.

---

### Post by rwslippey on 2011-10-16
My issue right now isn't so much the compiler or IDE, (please excuse me if I'm wrong that that's what you were suggesting) It's that I don't know where to start and which language to start with.

So I guess to rephrase the question, what is a good language to learn for linux in general, particularly ubuntu?

Thanks for the reply
Rob

---

### Post by gsmanners on 2011-10-16
IMO, a good language to start with is Python. It's very simple and straight-forward, so you can get up to speed quickly and with a minimum of frustration, so long as you don't mind doing stuff in terminal and mostly doing console apps to begin with.

---

### Post by rwslippey on 2011-10-16
Sounds good, I'll give it a shot, You've got to learn to crawl before you can walk right?

thanks for your input

---

### Post by cgroza on 2011-10-16
You must know that Windows does not include Python, so if you want to distribute it on Windows you have these choices:
1. You bundle python with your installer.
2. You use py2exe.
3. You ask the user to install the interpreter for you.

In Linux, this is not an issue because almost every distro out there includes python.

---

### Post by pbpersson on 2011-10-17
I have used Java for my projects - write once, run everywhere.  You never have to worry about "porting" it to Linux, Windows, or Macintosh.  Once you create the application, it will run on any platform.  You can use it for console apps, GUI apps, web apps, whatever you want.  Once you know Java, you can even write apps for an Android phone.

The first time I wrote an application on Linux and saw it run on a Windows machine it was quite a special feeling.

---

### Post by juancarlospaco on 2011-10-17
Python

---

### Post by 11jmb on 2011-10-17
Python programming is a lot of fun and making GUI apps is pretty easy compared to a lot of languages.

You also mentioned portability, which brings up Java. JRE is available for almost any conceivable system, and for GUI programming, SWING is very good about adapting to its environment. Also, Java's documentation is incredible

---

