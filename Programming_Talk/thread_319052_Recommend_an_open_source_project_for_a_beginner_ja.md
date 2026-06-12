---
title: "Recommend an open source project for a beginner java developer?"
date: 2006-12-15
forum: Programming Talk
---

### Post by mark2741 on 2006-12-15
I'm 2/3rds of the way through a Java Programming certification at a local University. Here's my quick story:

I'm in my mid-30's. About 3 years ago I was asked to develop an elearning program for my company. I didn't know anything about web development or *any* development at all. I started with html and then shortly went to Flash and almost immediately started learning Flash's scripting language, Actionscript. I am very comfortable with most aspects of that language now but a while back I wanted to learn to code in a more object-oriented manner in Flash (in anticipation of eventually moving to Flex/Actionscript 3) and it just so happens that my company will pay for me to take evening classes so I found a local uni that offered a Java  curriculum.

Next week I'll be finished the "Level Two/Intermediate" course and will be taking the JSP course next month, followed by the "J2EE/Java Advanced" course in the Spring.

I still feel very much like a beginner to Java but am starting to really feel comfortable with the basics. I'd like to get involved with an open source project but there are so many and I'm not sure how to find what I'm looking for. Here's my only criteria:

1. a relatively small project. The smaller the better, so I can more easily understand and participate.

2. Written in java (obviously : )

Later next year I plan on learning Javascript (which is similar to Actionscript supposedly so I hopefully will pick up on fairly quickly) and then either Ruby or Python. If all goes well I think I'll be ready to possibly try to get a Junior developer/programmer position within my present company (preferrably). 

Any recommendations for an open-source project?

---

### Post by slavik on 2006-12-15
because it sounds like Java is your first language, I would recommend learning C (it is very small) and C++. Because no matter how fast computers get, there will always be applications that have to be as realtime as possible.

---

### Post by jan247 on 2006-12-15
Here's something nice if you're interested in Instant Messaging: [JiveSoftware]("http://www.igniterealtime.org/"). I haven't really contributed to the project, but I've been using their work for some Java projects.

Oh, and please do tell me that you're using Eclipse. In any case, have you tried [Web Tools Platform]("http://www.eclipse.org/webtools/") edition of Eclipse? It's really useful considering you're into web.

---

### Post by pmasiar on 2006-12-15
> **slavik said:**
> because it sounds like Java is your first language, I would recommend learning C (it is very small) and C++. Because no matter how fast computers get, there will always be applications that have to be as realtime as possible.

Learning C/C++ will not add much to his understanding programming. **You need to learn a language with different paradigm to realize that big part of what you think is "programming fundamentals" are just quirks of your first language.**

Many hackers suggest lisp, but it is too radical IMHO and not used too much. Scripting languages (with dymanic typing) might be easier way to add to your understanding what programming is all about. Obvious candidate would be **javascript **- for web applications, AJAX is the cool thing everybody does (but you need some JS library, like mochikit). JS has nothing common with java - name is just marketing trick.

Very productive language for prototyping is **python **- my favorite language. It comes also as **Jython**, fully integrated with java. But Jython seems to be on life support - main developer was hired by Microsoft to implement Python as scripting language for .NET (**IronPython**), integrated with C#. Kind of neat trick to hurt java without being too obvious, when you think about it :-) . Sun realized they lack dynamically typed scripting language in java stack, so they hired Ruby developers to implement JRuby on top of java libraries. Many good news for dynamically-typed languages. 8-)

You can see **Python and Ruby** mentioned as new darlings for agile web application development. Especially puthon is oriented to be readable, make learning it easy, but scale to powerful when needed, make easy thing simple, and hard things possible.

If you want to learn more about Unix/Linux administration, there is another language I would consider to learn: **perl**. It is ugly and not maintainable for big projects, but oh so powerfull for quick 10-liners. And/or bash script.

If you are more inclined to learn how hardware works, **FORTH is very different kind of language** and still very popular in that community. It is amazing language, defying all common sense: interpreter, but **extremely fast, and extremely compact** (typical code is 1/4 of what code size would be in assembler, hence the name). And FORTH can run on bare metal, with no support from any OS at all. It is a language aimed squarely at elite programmers: if you are guru, you can make incredibly amazing things. If not, don't even try to touch it, you will fail miserably.

If you want to participate in java-based project, I would suggest to learn **Eclipse **and try to participate in some plugin you find interested. Best project to get involved is something you can use for yourself. You *will* use Eclipse - you may as well try to learn insides of it. All open source is based  on scratching your own itch.

But will gain real understanding what programming is all about only after you learn at least one or two different languages beside java. IMHO. many people never will, and they never realize that Java is new and improved COBOL++. :-)

---

### Post by randomnumber on 2007-01-30
I suspect that you have not gotten to data structures. Our third programing class at college is data structures. Data structures include array, arraylist, linkedlist, tress, hashtables, etc. It is important to know the abilities of each and reason to use one over the other. There is on perfect data structure. When you teach your self the data structures, anything beyond an array you should write on your own so that you understand what is going on. You do not actually need to use your own code but it really helps to understand what goes on under the hood. 

I made the following. 
Solitaire that uses mouse input.  Sounds simple but I learned a lot from this.

Cell Phone tracking system that determines traffic congestion. 


I would like to see some good program of Tower of Hanoi. I acutally think it would be cool to see a version of this added a screen saver. There may be one already but I have not seen it.

Also I suggest learning a different level of programing. C/C++ is a good start but it is not different enough. I think that assembly programing teaches you much. You learn a lot when you write code that takes String and changes them to numerics. Again, this sounds simple but actually take some work.

---

### Post by Tomosaur on 2007-01-31
How about writing a nice plugin for JEdit. JEdit is a programmer's text editor written in Java, and it's very nice, quick, and fully featured. The interface could do with a little sprucing up though! The JEdit [dev page](http://www.jedit.org/index.php?page=devel) does state that they're looking for help, so maybe you could have a go at writing for the main app, but plugins are also a useful feature and they can make JEdit a truly awesome program.

---

