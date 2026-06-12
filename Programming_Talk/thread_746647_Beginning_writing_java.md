---
title: "Beginning writing java?"
date: 2008-04-05
forum: Programming Talk
---

### Post by Blacklife08 on 2008-04-05
I know basicly nothing about java, can anyone recommend a tutorial book/website/ebook?

Thanks

---

### Post by nandiana47 on 2008-04-06
Try Deitel & Deitel's Programming with Java. It is a very simple to understand book that explains the basics very clearly

---

### Post by LaRoza on 2008-04-06
See my wiki.

If you don't know another language, and are not learning this for a specific reason, I recommend another language to start with (you'll see on my wiki)

---

### Post by The Cog on 2008-04-06
Suns java tutorial is excelent. Huge but very thorough. It;s available for downloading and reading offline. 
[http://java.sun.com/docs/books/tutorial/](http://java.sun.com/docs/books/tutorial/)

---

### Post by Nepherte on 2008-04-06
Thinking in Java - Bruce Eckel

You have to pay for the 4th version, but every previous edition can be downloaded for free:
[http://www.mindviewinc.com/downloads/TIJ-3rd-edition4.0.zip](http://www.mindviewinc.com/downloads/TIJ-3rd-edition4.0.zip)

---

### Post by pmasiar on 2008-04-06
Thinking in Java is for advanced Java programmers who want to understand design on deeper level. Excellent book, but no way for beginner. 

This is common problem with advice on any forum - people with advanced knowledge suggest book they liked, instead of a book appropriate for a beginner.

"Head First Java" is the best book for beginner, no other book compares. Whole series is the best intro to any area it aims, I am looking forward for Python book soon.

But LaRoza is right, Java is not the best language for beginner - way too Object Obsessed to be easy to grasp basics. Python is **much** better for beginners. See my sig for links, see also poll in sticky FAQ.

---

### Post by Biggus on 2008-04-06
Dudes I don't want to hijack this thread, but I just thought I'd take the opportunity to ask, am I correct in thinking that the compiled 'binary' (or whatever the java equivalent is) would be portable across any OS which is capable of executing java code?

ie I could write a little app in java, in ubuntu, and then send it to the user of a different operating system for them to execute, dependent upon them having the requisite java environment installed?

---

### Post by SOULRiDER on 2008-04-06
I recommend Head First Java, its an excellente book!
[http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1207532010&sr=8-1](http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1207532010&sr=8-1)

---

### Post by pmasiar on 2008-04-06
> **Biggus said:**
>  the compiled 'binary' (or whatever the java equivalent is) would be portable across any OS which is capable of executing java code?

ie I could write a little app in java, in ubuntu, and then send it to the user of a different operating system for them to execute, dependent upon them having the requisite java environment installed?

Yes. This independence is one of beauties of Java. .class file is platform-independent. It is also a curse for Java: Java stands separate from all platforms, a platform by itself.

But all is not just roses: you have to have all libraries in classpath. And Java has so many of them. It is very flexible arrangement, but you have to manage it.

Other open-source languages do aim for that - they aim to be cross-platform at source level, having different versions of libraries (with same API) for different platforms. It is less work do it that way, if you don't mind sharing sources.

---

### Post by Chayak on 2008-04-06
> **SOULRiDER said:**
> I recommend Head First Java, its an excellente book!
[http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1207532010&sr=8-1](http://www.amazon.com/Head-First-Java-Kathy-Sierra/dp/0596009208/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1207532010&sr=8-1)

+1

Any of the Head First books are excellent

---

### Post by Inxsible on 2008-04-06
The Java Tutorial by Mary Campione, Kathy Walrath, Alison Huml. Published by Addison Wesley.



If it doesn't "have to be"  Java, then I would recommend you learning something like Ruby, which is great because you code a lot less or Scala which is also alot like Ruby, but with the added advantage that it is compatible with Java i.e. you can interchangeably use Java from scala and scala from Java classes.

---

### Post by vampiric_blade on 2008-04-07
I just started with java about a month ago, and having only limited experience with basic years ago,  I found wrapping my head around the concept of object orientation to be difficult.   As I persist, things are becoming much clearer, and easier.

I recommend not buying any books right off the bat.  The Head First book was losing me 100+ pages in with the "sink a dot com game".   I found that I had to get perspectives from 5 different books to get a firm grasp of some things, especially instantiation, constructors, and Array Lists.    My advice is to go to your public library and grab a few books.   If not, you'll likely end up plopping down $50 one one and being too confused and overwhelmed by everything that you'll likely stop reading it.

---

### Post by LaRoza on 2008-04-07
> **vampiric_blade said:**
> 
I recommend not buying any books right off the bat.  The Head First book was losing me 100+ pages in with the "sink a dot com game".   I found that I had to get perspectives from 5 different books to get a firm grasp of some things, especially instantiation, constructors, and Array Lists.    My advice is to go to your public library and grab a few books.   If not, you'll likely end up plopping down $50 one one and being too confused and overwhelmed by everything that you'll likely stop reading it.

Java is much easier if you already know programming. 

Taking the time to learn Python (just the basics) then learning Java would be faster I think that learning Java from the start.

Either way, I don't recommend buying any books for now. Use online resources, which are more up to date and free.

---

### Post by The Cog on 2008-04-07
> **Biggus said:**
> Dudes I don't want to hijack this thread, but I just thought I'd take the opportunity to ask, am I correct in thinking that the compiled 'binary' (or whatever the java equivalent is) would be portable across any OS which is capable of executing java code?

ie I could write a little app in java, in ubuntu, and then send it to the user of a different operating system for them to execute, dependent upon them having the requisite java environment installed?

Yes, but with provisos. There are ways to write portable code, and ways to write non-portable code. For example, when dealing with file paths, using "\\" or "/" to join filename to directory name is not portable. Using the system property file.separator is portable. Similarly, printing lines of text ending in "\n" or "\r\n" or "\r" is not portable, but using the system property line.separator is.

You also need to be careful of the default character encodings. Java defaults to using the platform default encoding for reading/writing text - unicode on Linux, something proprietary of course on windows, don't know about the mac, and EBCDIC on AS/400. This is fine but when writing apps that talk over the network, you need to specify the encoding or surprises will result when you port your app to a different machine.

These issues are of course not specific to java, but they are more specifically addressed and better supported in the java I/O libraries than they are in most languages.

---

### Post by SOULRiDER on 2008-04-07
> **LaRoza said:**
> Java is much easier if you already know programming. 

Taking the time to learn Python (just the basics) then learning Java would be faster I think that learning Java from the start.

Either way, I don't recommend buying any books for now. Use online resources, which are more up to date and free.

I found it harder to learn Python than to learn Java for one big important reason. Java is more strict, it makes you define variable types and what youre going to return in functions as well as atrobutes in objects. If youre learning OOP i think using a language that is strict will help you learn a lot faster.

---

### Post by The Cog on 2008-04-07
I have to admit I like that about java. You always know exactly where you stand. In comparison, python sometimes seems rather vague and wooly, especially some of the library documentation which doesn't bother to tell you what data type it expects or returns.

Yes Pamasir, we all know you disagree.

---

### Post by pmasiar on 2008-04-07
it is pmasiar : valid type but wrong value :-)

Not sure how strict typing helps you to understand loop, function, etc. But of course you are free to have your opinion. Did you ever tried learning Python in the shell? 

BTW "Python, then Java" approach was experiment done by teachers in school, not just personal anecdote. MIT also uses Python for intro, and not Java.

---

### Post by The Cog on 2008-04-07
Apologies for mis-spelling your name.

And actually, I think python probably makes the better introductory language. But I do find the python documentation lacking sometimes, and sometimes miss the determinism and certainty of java. I wasn't talking about strict typing, I was talking about having to write a test program to discover if a library function returns a string, list or dict. Or what it returns under error conditions - "", None, False or raising an Exception. You shouldn't have do that.

---

### Post by pmasiar on 2008-04-07
But you don't have to do that - you can try any function directly in the python shell.  For function foo() you can use help(foo) - will print help string (docstring). You can also instantiate object: 

[php]
import module1
x = module1.method(params)
dir(x) # will list all attributes and methods for this object
help(x.foo2) # will print docstring
[/php]

This is whole point why Python is more beginner friendly than Java - you can learn it one line at a time, in shell. [ One Day of IDLE Toying](http://hkn.eecs.berkeley.edu/~dyoo/python/idle_intro/) . You don't need to write scaffolding code to test a function, just try it in the shell.

---

### Post by The Cog on 2008-04-08
I know that.
I always do that before resorting to test code to discover what **should have been** documented.

---

### Post by tseliot on 2008-04-08
> **The Cog said:**
> I know that.
I always do that before resorting to test code to discover what **should have been** documented.
At the risk of seeming naive with this question, have you tried the [library reference]("http://docs.python.org/lib/")?

---

### Post by themusicwave on 2008-04-08
I think what The Cog is referring to is that Java's documentation is just way more detailed.

Pythons documentation is usually good enough, but sometimes it doesn't have quite as much information as Java's.  Java's documentation is almost too detailed sometimes, which in my view is a good thing.

Java's documentation is the best I have seen thus far in any language.

I like both languages and am currently writing applications in both of them.  But I have to agree with The Cog that Java has better documentation.  Python's is still pretty good though.

Although I also agree that the Python shell is a nice little place to test things out and try them.  When I am somewhat familiar with a language  I like to just look at the documentation and see exactly what is going to happen.  What exceptions do I need to handle, what are the return values to prepare for, etc.  This isn't an issue for a beginner I suppose.

Python is probably more beginner friendly with the shell and all.  I can definitely see both of your sides' of the argument.  I think in the end either can be a good choice depending on where you want to go and what you want to do.  For education, I think it is helpful to have ordinary procedural programming under your belt before you jump into OOP. 

I followed the path of:
TI BASIC(old TI 99/4A) --> C++ --> Java --> Assembly(Intel and embedded) --> C(embedded mainly) --> Python

I turned out just fine...I think...

---

