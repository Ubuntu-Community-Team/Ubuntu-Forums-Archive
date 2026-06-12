---
title: "Best GUI programming language"
date: 2009-04-22
forum: Programming Talk
---

### Post by sasaqe on 2009-04-22
I want to learn to make some GUI's.
Ill mostly use them to make some simple simulations, and models . 
i want to know which language should i use to do so.
I am currrently thinking of using python or java but having learnt  C, the C GTK libraries also is an option.
Id like your opinions about it.
thanks.

---

### Post by cabalas on 2009-04-22
To be honest that is a very loaded question you are asking, it's a bit like asking what colour should you paint the bike shed everyone can have a different opinion which if not careful can degenerate into a flame war pretty quickly.

As to an answer to your question about which should you use what platform are you targeting?

[LIST]
[*]If it's gnome use the Gtk binding to whatever language you choose.
[*]If it's KDE use QT it has bindings in most languages I believe
[*]If you choose java you can either use the platforms bindings or swing, last time I used swing its look didn't quite fit into any platform but I hear that it has come a long way since then (admittedly this was about 2 - 3 years ago) so I'm not sure if that's true anymore.
[*]If you are targeting every platform I'd consider looking a WxWidgets as (someone correct me if I'm wrong here) it uses the underlying platforms widgets where ever possible (e.g. - on gnome it uses Gtk, windows it uses winforms, etc)
[/LIST]

Of all of the above WxWidgets is the least sure I'm on as I've just been going on what I've heard - never actually used it myself.

---

### Post by Jiraiya_sama on 2009-04-22
Fortran.

---

### Post by Pollox on 2009-04-22
> **cabalas said:**
> [*]If you are targeting every platform I'd consider looking a WxWidgets as (someone correct me if I'm wrong here) it uses the underlying platforms widgets where ever possible (e.g. - on gnome it uses Gtk, windows it uses winforms, etc)
[/LIST]

Of all of the above WxWidgets is the least sure I'm on as I've just been going on what I've heard - never actually used it myself.

Yes, wxWidgets does do that.  I recently used it with a python app (using wxPython) that I wanted to look good on all platforms, and it really does work well for that purpose.  Not too complicated either.

---

### Post by samjh on 2009-04-22
> **sasaqe said:**
> I want to learn to make some GUI's.
Ill mostly use them to make some simple simulations, and models . 
i want to know which language should i use to do so.
I am currrently thinking of using python or java but having learnt  C, the C GTK libraries also is an option.
Id like your opinions about it.
thanks.

You're asking the wrong question.  The better question is what GUI library to use for languages you already know.

You already know a programming language, so leverage your existing knowledge.  If you already know C, then use GTK.  If you know other languages, then Google for GUI libraries for those languages.

---

### Post by Kilon on 2009-04-22
> **sasaqe said:**
> I want to learn to make some GUI's.
Ill mostly use them to make some simple simulations, and models . 
i want to know which language should i use to do so.
I am currrently thinking of using python or java but having learnt  C, the C GTK libraries also is an option.
Id like your opinions about it.
thanks.

Best GUI and RAD language I have used is DELPHI , but now DELPHI is .NET and thus you may have some issues porting it into Linux and especially macos. Lazarus is open source variant of Delphi supporting linux as well. Lazarus uses the FreePascal programming language

[http://www.lazarus.freepascal.org/modules.php?op=modload&name=StaticPage&file=index&sURL=about](http://www.lazarus.freepascal.org/modules.php?op=modload&name=StaticPage&file=index&sURL=about)

I cannot vouch for lazarus , I can only vouch for delphi but I am sure it will work just fine for you. 

If you are after the most popular easy to use choice, then wxPython is the way to go. It uses Python. 

[http://www.wxpython.org/](http://www.wxpython.org/)

I will have to agree that pretty much all programming languages can do GUI efficiently. GUI is considered a fundamental feature after all. For example I worked comfortably with SWING in JAVA and Jython both fully supporting linux. I have heard that many people used C# with linux as well.

WxWidgets works as well with C++ as it does with python.

Obviously it is personal taste that matters most, but I prefer the compact and very easy to understand coding of python . I now work with wxPython and pysqlite and I am very happy with what I am seeing.

---

### Post by sasaqe on 2009-04-22
> **cabalas said:**
> 

As to an answer to your question about which should you use what platform are you targeting?


I wiill use it in linux(xubuntu 8.10) which is gnome.
I will generally make programs for my own use, so i dont have an issue if its not portable or cross-platform compatibility.

> **samjh said:**
> 

You're asking the wrong question.  The better question is what GUI library to use for languages you already know.


I know C/C++ but was wondering whether python / Java would be better than GTK libraries of C and whether it would be worth learning them.

---

### Post by JK3mp on 2009-04-22
> **sasaqe said:**
> I wiill use it in linux(xubuntu 8.10) which is gnome.
I will generally make programs for my own use, so i dont have an issue if its not portable or cross-platform compatibility.



I know C/C++ but was wondering whether python / Java would be better than GTK libraries of C and whether it would be worth learning them.

C/C++ are great but Java would work too. Pythons good and easy but not very powerful for GUI apps

---

### Post by ajackson on 2009-04-22
> **JK3mp said:**
> C/C++ are great but Java would work too.
I agree with those but this one.
> Pythons good and easy but not very powerful for GUI apps
I'm curious as to why you feel Python is not as good for GUI apps because it has compatibility with a lot of the GUI libraries (GTK/Tk/QT/etc).

---

### Post by CptPicard on 2009-04-22
> **JK3mp said:**
> Pythons good and easy but not very powerful for GUI apps

Actually, Python is very enjoyable to hack KDE/Qt stuff in... I have been considering giving one of my toolkits a proper GUI frontend, and a combination of Python for driving GUI and user interaction code and C on the algorithms side seems like a good solution.

GUI code is often very tedious, repetitive especially in languages like Java and C++. Anything that alleviates that is a big win.

---

### Post by JK3mp on 2009-04-22
> **ajackson said:**
> I agree with those but this one.

I'm curious as to why you feel Python is not as good for GUI apps because it has compatibility with a lot of the GUI libraries (GTK/Tk/QT/etc).
I guess so I just havnt evaluated it's power In GUI programming personally. :-p

---

### Post by sakabato on 2009-04-22
I recommend C# or any .NET/mono language you like. If you use GTK# or windows forms , your application will be cross platform too.

---

### Post by Kilon on 2009-04-22
> **JK3mp said:**
> I guess so I just havnt evaluated it's power In GUI programming personally. :-p

I use wxPython , it is very very powerful. And very popular too.When I first used it I find it a bit tedious , probably because the documentation that it came with was far from being best , but I have given it a second try. Download loads of tutorials and how tos and now everything is much more clear. 

I making a Database app with PySQlite( I actually started with MySQL , I even bought a huge book for it but later decided that SQlite was much more power than I thought and much easier. The book was not wasted as it taught me SQL. ) and WxPython and so far it has been a piece of cake. Very impressed with Sqlite as well. I love open source. 

An Wx is very cross platform too, win, mac, Linux, pocket cp , paml os well if they make a iphone and ipod touch port will be just perfect . Then I will be able to take my database app anywhere I go (I recently bought a ipod touch).

I always advice people to try thing for themselves. Afterall nothing you are going to learn is going to be wasted.

---

### Post by directhex on 2009-04-22
I'd use the nice clicky GUI designer in MonoDevelop. But that's just me.

---

### Post by namegame on 2009-04-22
In my experience, handcoding a Swing GUI in Java is very tedious and rather time consuming. Especially if you get into LayoutManagers such as SpringLayout or GridBadLayout. However, on the other hand, I absolutely despise the way IDEs such as Netbeans generate Swing GUI code. 

So from my perspective, you can either handcode a GUI by hand, which can take a while, but it will work. Or you can bang your head against a wall fighting the way Netbeans works... 

I prefer handcoding...

---

### Post by scourge on 2009-04-22
> **CptPicard said:**
> Actually, Python is very enjoyable to hack KDE/Qt stuff in... I have been considering giving one of my toolkits a proper GUI frontend, and a combination of Python for driving GUI and user interaction code and C on the algorithms side seems like a good solution.

The problem with PyQt is its uncertain future and lack of maintainers. It now seems to be pretty much a one-man project, the documentation is a half-assed conversion of the original Qt (C++) docs, it's not available under LGPL (at least according to the PyQt website), etc.

---

### Post by CptPicard on 2009-04-22
Well, what you generally want to do with Swing is to use a visual editor to get your layout straight -- it really is nice how you can fiddle with all the properties and the way you nest things and then see what you get.

When you get your components arranged pretty much how you want them, you just start hand-hacking the rest, the editor be damned.

---

### Post by Wybiral on 2009-04-22
> **JK3mp said:**
> I guess so I just havnt evaluated it's power In GUI programming personally. :-p

Perhaps you should (especially before making any statements about it).

---

### Post by happysmileman on 2009-04-22
I would say GTK if you already know C, mainly because there exist binding for every language, so if you learn GTK for C you can just as easily code GUIs in Python, Perl, Ruby, etc. using the same libraries.

Exact same can be said for Qt (And personally I much prefer Qt to GTK), but you can't use C for it AFAIK, only languages with OOP (which is almost all modern programming languages), and if you're a GNOME user GTK would be better integrated

---

### Post by scourge on 2009-04-22
> **happysmileman said:**
> 
Exact same can be said for Qt (And personally I much prefer Qt to GTK), but you'd need to be using C++ for it...

...or Python, C#, Ruby, Java, Ada, Pascal, Perl, PHP, or Haskell.

---

### Post by happysmileman on 2009-04-22
> **scourge said:**
> ...or Python, C#, Ruby, Java, Ada, Pascal, Perl, PHP, or Haskell.

Yes sorry, updated post to reflect that

---

### Post by mshipman on 2009-04-22
If you're coding in C, use GTK... C++? Well... GTKmm is the wrapper that's out there.

In my humble opinion, java's swing toolkit is the simplest GUI toolkit to use that is available (but obviously you need to have experience with java).

Happy GUI-ing!

---

### Post by Kilon on 2009-04-23
Java swing is not that bad . The reason why is more difficult than other GUI APIs is because it follows a more modular apprach, because java is very strict about being cross platform and tries to support tiny screens as well. And that can create some extra coding with GUIs. But I will have to agree that is very well made GUI API, also it provides alot more features than other GUI APIs, like skinning, alot of 2d functionality etc. 

Also IDEs are very important tools as well as they cut down coding to minimum. Which can be bad for learning the APIs but is very good for speed of development.

So many options so little time. ;)

---

### Post by directhex on 2009-04-23
Try to distinguish between the GUI toolkit, the tools you use to create it, and the language you use to program with it.

Toolkits means things like GTK+, Qt, WxWidgets, Swing

Tools means things like Glade, Stetic, Qt Designer

Languages means things like C, Python, Java, C#

You can mix-and-match many, but not all, of these.

Your choice of toolkit defines the "look and feel" of your app, and how "out of place" it does or does not feel on different platforms. For example, even though Swing with Java has skinning abilities, it does NOT feel like the "real thing" - for that, you need to use Qt or GTK+ from Java directly using QTJambi or SWT directly.

---

### Post by Kilon on 2009-04-23
> **directhex said:**
>  For example, even though Swing with Java has skinning abilities, it does NOT feel like the "real thing" 


In the case of MAC OS and Windows and Ubuntu Java uses the default native theme as well its own. 

all you have to do is add this little code

```
UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName()); 
```

Both Windows and MACOS look and feel is flawless (or almost flawless).I cannot vouch for linux as I have not investigated deeply but from what I have seen ( from some of the test code I made ) it looks exactly the same as any app out there. 


I know that this has been an issue with previous version but I do not think it is anymore. Also the Nimbus look and feel is very impressive.

[http://blogs.sun.com/CoreJavaTechTips/entry/swingset3_nimbus_and_java_se](http://blogs.sun.com/CoreJavaTechTips/entry/swingset3_nimbus_and_java_se)

and of course there are third party themes to choose from too

[http://javabyexample.wisdomplug.com/component/content/article/37-core-java/65-20-free-look-and-feel-libraries-for-java-swings.html](http://javabyexample.wisdomplug.com/component/content/article/37-core-java/65-20-free-look-and-feel-libraries-for-java-swings.html)

---

### Post by directhex on 2009-04-23
> **Kilon said:**
> (or almost flawless)

In a curious arrangement similar to the Uncanny Valley, the closer something looks to "native", the more noticeable the glitches.

---

### Post by Kilon on 2009-04-23
> **directhex said:**
> In a curious arrangement similar to the Uncanny Valley, the closer something looks to "native", the more noticeable the glitches.

That is very true ... but only if you re a purist ;)


is it not glitches part of life? You gain something , you lose something. Nothing is perfect.... obviously.

---

### Post by samjh on 2009-04-23
> **directhex said:**
> In a curious arrangement similar to the Uncanny Valley, the closer something looks to "native", the more noticeable the glitches.

Even Gtk can feel out of place in Gnome or Xfce.

But I agree that Java's Gtk LAF is... lacking.  It's improved a lot since Java 1.5, but still not authentic enough.

---

### Post by mssever on 2009-04-23
I've never used Swing, or evaluated any Swing apps. Does "nearly flawless" L&F include things like whether dialogs auto-apply?

In Gnome, I'm used to most dialogs auto-applying, and any app that doesn't do that feels out of place. Windows, however, is still stuck in the world of manual apply buttons, so native L&F should follow that in Windows.

---

### Post by Kilon on 2009-04-23
> **mssever said:**
> I've never used Swing, or evaluated any Swing apps. Does "nearly flawless" L&F include things like whether dialogs auto-apply?

In Gnome, I'm used to most dialogs auto-applying, and any app that doesn't do that feels out of place. Windows, however, is still stuck in the world of manual apply buttons, so native L&F should follow that in Windows.

google says yes ;)

[http://209.85.129.132/search?q=cache:mlLQQ3xG62YJ:www.java2s.com/Code/Java/Swing-Components/SwingAutoCompleteComboBox.htm+auto+apply+swing+java&cd=2&hl=en&ct=clnk](http://209.85.129.132/search?q=cache:mlLQQ3xG62YJ:www.java2s.com/Code/Java/Swing-Components/SwingAutoCompleteComboBox.htm+auto+apply+swing+java&cd=2&hl=en&ct=clnk)

Of course swing is fully customizable , so it is only a matter of coding. What you asking is just simple event catching.

---

### Post by SpyroViper on 2009-04-23
I'd go with Java personally.  But then I'm comfortable with Java so naturally I'd pick that.

You could use a toolset to help you like GTK+ but using a language gives you more flexibility imo.

---

### Post by sasaqe on 2009-04-23
Thanks to everyone for all the advice.
I think i'll stick to C and use the Gtk toolkit for now.

---

