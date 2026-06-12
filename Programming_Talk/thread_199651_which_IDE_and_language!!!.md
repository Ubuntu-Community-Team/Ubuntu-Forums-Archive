---
title: "which IDE and language!!!"
date: 2006-06-19
forum: Programming Talk
---

### Post by javabien on 2006-06-19
Hello with you,      

I like to make development (but up to now I did it under Windows: vs, windev, etc…). In the world of linux, there is so much IDE which I do not know which to choose. Can you give me a blow of hand.    

Here approximately what I seek:   

- development under Linux but with portability under Windows 
- language with Doc. complete and especially of the totu and examples (to learn speedy)  
- a IDE with creator of interface    

I thought of leaning me on of GtK but I cannot too what choose.    
Thank you in advance      

Javabien      

PS: if there is no conceptor of interface it is not important as long as there is much Doc. and if possible in French tongue.

---

### Post by nythrix on 2006-06-19
Check out this thread: [http://www.ubuntuforums.org/forumdisplay.php?f=39](http://www.ubuntuforums.org/forumdisplay.php?f=39)
I was in a similar situation and went off with Java and Netbeans.

---

### Post by javabien on 2006-06-19
ok tks

---

### Post by nythrix on 2006-06-19
Sorry about that. I was logged when I copy-pasted the adress. Use this instead:
[http://www.ubuntuforums.org/showthread.php?t=196799](http://www.ubuntuforums.org/showthread.php?t=196799)

---

### Post by Revert on 2006-06-19
Java sounds like it'd be good for the portability and documentation.
Eclipse and Netbeans are the two biggest, full-fledged IDEs.  Both have available GUI creators and other features.
If you prefer something simpler, Scite and Jedit are pretty good, but more like text editors that can compile and such.

---

### Post by bieber on 2006-06-19
C/C++ and GTK+, along with one of many IDE's (I use Anjuta) will also work just fine, and won't make your applications dependent on a proprietary system.

---

### Post by LordHunter317 on 2006-06-19
Actually, they very well might.  Depends on what the application is doing.

---

### Post by G Morgan on 2006-06-20
C/C++ is more complex than Java but is also more powerful. I use Kdevelop myself. A comparitively easy language to get to grips with that is popular in Linux is Python. One thing to get to learn in Linux is GTK or QT (GTK is the standard) I believe GTK has Python bindings (it works in C natively). If you use Java this obviously become mostly irrelevant.

//edit - as for portability in C/C++ it depends what functions you use. Even the simplest of functions are slightly different between the GCC and say the Borland compiler (as I remember the getline() function is implemented differently). You can code around this but that is obviously an extra consideration. On the plus side there is very little you can't do in C/C++ (at least within reason).//

---

### Post by javabien on 2006-06-21
Ok thank all for your answer.

I'll see if I use python + wx or c++. Java is good but I don't know why I never use it:

Now I discover samlltalk and it's nice IDE squeak. It's very good for multimedia software, and for beginner.


May be later I use C++ and wx for use my soft on linux, maosx and windows.


Javabien

---

### Post by LordHunter317 on 2006-06-21
[QUOTE=G Morgan]C/C++ is more complex than Java but is also more powerful.[/quote]C++ might be.  C certainly is not.

> One thing to get to learn in Linux is GTK or QT (GTK is the standard) I believe GTK has Python bindings (it works in C natively).Neither is standard and both have python bindings.

> //edit - as for portability in C/C++ it depends what functions you use. Even the simplest of functions are slightly different between the GCC and say the Borland compiler (as I remember the getline() function is implemented differently).No one cares about the Borland compiler anymore.

---

### Post by Engnome on 2006-06-21
[QUOTE=javabien]
- a IDE with creator of interface    

I thought of leaning me on of GtK but I cannot too what choose.    
[/QUOTE]

Well since noone mentioned glade I will. It's not excactly an IDE but that is one of its finesses, you make a gui in glade and run it from c/c++ perl python whatever.

---

### Post by Daverz on 2006-06-22
[QUOTE=javabien]I like to make development[/QUOTE]

The Java/Swing/Netbeans suggestion is a pretty good one, though I find Java a rather tedious language to work in.  You won't find anything better documented, and there are tons of excellent open source libraries available for the JVM.     Deployment is also very easy (once your users have a Java runtime installed).
If only Java was a more expressive language... 

PyGtk works fairly well under windows, though there may be a few look & feel issues here and there (mainly feel issues).  There's an excellent tutorial and reference, and an extensive FAQ.  See 

[http://pygtk.org](http://pygtk.org)

The API is quite complete, though there's a certain clunkiness here and there given its C origin.  This is my own personal preference.

WxPython is more cross-platform, and has better native look & feel on each platform.  Works on OS X, too.  There's also a book, "WxPython in Action".  There's a certain old-style C++ mustiness about it (I believe it was somewhat based on MFC, so it may be a good fit for someone familiar with windows programming), but it seems to have a very complete and powerful API. 

[http://wxpython.org](http://wxpython.org)

For more on Python itself, see 

[http://www.python.org/doc/nonenglish/#french](http://www.python.org/doc/nonenglish/#french)

---

### Post by stani on 2006-07-18
Read my [howto install latest wxPython & SPE (Feature rich Python IDE)]("http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython").

---

### Post by Note360 on 2006-07-18
If portability is what you seek C# may be the language you want and MonoDevelop (#develop in Windows) to be the tool you greet.

(Did that make any sense? I was trying to talk in riddles)

---

