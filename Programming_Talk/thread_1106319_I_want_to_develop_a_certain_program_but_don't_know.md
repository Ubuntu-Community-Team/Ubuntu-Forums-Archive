---
title: "I want to develop a certain program but don't know which language to choose"
date: 2009-03-25
forum: Programming Talk
---

### Post by Eugene_Bondarenko on 2009-03-25
Hi, guys.

I am a PHP ( + JS + other common web stuff) developer and the problem is that I already know absolutely everything here :KS (lol, I can't refrain from putting this smiley, it's so cute)

So I've decided to learn some other language. Also I've been thinking about developing a certain Windows PC application. The problem is that I really don't know which language suites this idea the best. 

I think the best idea of describing this application is simply comparing it to some abstract spammer software. So let's imagine that I am going to develop a spammer application that keeps thousands and thousands of emails and can send some text to all of them. Also it has accounts at hundreds of forums and can sign in to them and post spam messages there. So we're going to have intense work via HTTP and SMTP (and other protocols) and we will have to deal with a huge DB.

So let's say you're developing such a commercial product. What language would you choose? And where to store all that information? In web-development I work with MySQL but I wonder if it is a good idea for a Windows PC applications because every client that is going to buy our product will have to install MySQL server. So how do you solve this problem? Do you use MS Access or something else?

PS. I am not going to develop a spammer application and I hate spam; that was just an example that came to my mind :)

---

### Post by Can+~ on 2009-03-25
> **Eugene_Bondarenko said:**
> So let's say you're developing such a commercial product. What language would you choose? And where to store all that information? In web-development I work with MySQL but I wonder if it is a good idea for a Windows PC applications because every client that is going to buy our product will have to install MySQL server. So how do you solve this problem? Do you use MS Access or something else?

Or maybe just store it on a sequential file? Seriously, relational databases are a great way to store information, but no the only way, normal binary files or plain text files can cut it too, or a markup like xml. If you absolutely need a database, then you can check SQLite.

As for the language, any High-level language could do it, look for one with good libraries for handling connections and html parsing. Python comes to mind, but users would have to install the python interpreter, maybe C# if it's going to be windows only.

> PS. I am not going to develop a spammer application and I hate spam; that was just an example that came to my mind :)

Weird example.

---

### Post by lisati on 2009-03-25
When you say "Windows PC", does it mean that you are considering a project specifically for Windows, or would you be looking for something more portable? (This is, after all, a Linux/Ubuntu form)

Each language has its merits, and you'll probably find a variety of opinions and preferred languages here in the forums.

Java, Python, and several other languages come in versions for different platforms (Windows, Linux, etc). I don't have any experience of these languages beyond looking at the occasional code snippet on these forums. 

The "C" family of languages is a good all-rounder.

---

### Post by nvteighen on 2009-03-25
It depends on what your application does... :p but other factors like deployment, available libraries or licensing can alter that and force you to take routes harder than the ideal one.

If it's an application that needs to rely on manual management of the computer's work you should use a low-level language: C, C++, Assembly or Forth.

But you should use that only for the needed parts, otherwise, you'll making a lot of effort to make the language reach that certain abstraction level you need for mapping the concepts you have into the code. That's where high-level languages come in, but obviously they are slower and may be less efficient... for the computer, but much more for the programmer.

High-level languages you can consider and that are certainly cross-platform as well: Python, Perl, Ruby, C#, e.g. Maybe C# is a good choice, as it runs "natively" on Windows if the user has the .NET Runtime installed.

Again, it all depends on what you need.

---

### Post by cabalas on 2009-03-25
If you are writing an application for windows that will not migrate and it has a GUI I would use C#.  Hell even if it's a windows service I would use C#.  If you plan on porting it to other operating systems choose something like python or c if speed is hugely important to the project and then just find cross platform libraries to fill in some of the holes of functionality.

---

### Post by Eugene_Bondarenko on 2009-03-25
> **Can+~ said:**
> Or maybe just store it on a sequential file? Seriously, relational databases are a great way to store information, but no the only way, normal binary files or plain text files can cut it too, or a markup like xml. If you absolutely need a database, then you can check SQLite.

Yeah, I've been thinking of some XML or similar stuff but I do realize how much pain it will cause :)  So if SQLite doesn't require any hard installation and this can be easily included in the standard Windows installer (the one where you choose path and click "Next" for a couple of times), that's the perfect choise! :)

> **lisati said:**
> When you say "Windows PC", does it mean that you are considering a project specifically for Windows, or would you be looking for something more portable? (This is, after all, a Linux/Ubuntu form)
Well, I say Windows PC because Windows is still more common OS than Ubuntu. I personally use Ubuntu and like it more than Windows but there is no way I can change the above fact. And I am asking the question at this forum because it seems to be the place where chances of finding developers from different areas are the highest.

Yes, of course I want to make it as portable as possible. But the first goal is to make it maximum easy for Windows users to use. So I don't want to abuse them with requests to install Java environment, Python interpreter, some DB server. Yes, for guys like us it sounds like piece of cake but if I e.g. tell my sister that she needs to install Python interpreter she'll look like this :shock:. And I guess most of the people that hang at the computers will have the same face. :)

> **nvteighen said:**
> It depends on what your application does... :p but other factors like deployment, available libraries or licensing can alter that and force you to take routes harder than the ideal one.

If it's an application that needs to rely on manual management of the computer's work you should use a low-level language: C, C++, Assembly or Forth.

But you should use that only for the needed parts, otherwise, you'll making a lot of effort to make the language reach that certain abstraction level you need for mapping the concepts you have into the code. That's where high-level languages come in, but obviously they are slower and may be less efficient... for the computer, but much more for the programmer.

High-level languages you can consider and that are certainly cross-platform as well: Python, Perl, Ruby, C#, e.g. Maybe C# is a good choice, as it runs "natively" on Windows if the user has the .NET Runtime installed.

Again, it all depends on what you need.
Let's forget about licensing as for now. :) I do realize that some languages are commercial but let's forget about this as for now. I'll later open a separate thread about licensing because I have another heap of questions about this. :)
Yes, I know about the abstraction levels you mention and I perfectly understand what is involved here. So my vote is for "The easier for developer the language is the better" 

> **cabalas said:**
> If you are writing an application for windows that will not migrate and it has a GUI I would use C#.  Hell even if it's a windows service I would use C#.  If you plan on porting it to other operating systems choose something like python or c if speed is hugely important to the project and then just find cross platform libraries to fill in some of the holes of functionality.
Yes, GUI is the must here. 
Well, as I said above in long-term perspective I'll migrate it to Linux but right now I want to concentrate on Windows. In the worst case we always have WINE ready to save the sitiuation :)
About speed. Yes, it's quite important. But looking at the example I think the largest slowdown will be received from the HTTP (and other) communication. So I guess if an application signs in to 100 forums and posts a message, the application slowdown won't be noticable in comparison to HTTP slowdown we have here.



As far as I see lots of people advise me to use C# (which frankly speaking I was thinking about too). So may be anybody could tell me some nice book? Lots of books have loooong discriptions of basics (how FOR, IF,... functions) and even loooooonger description of OOP. May be you know about some book that doesn't have all that (or has minimum) and which describes only C# specific stuff instead. With some good examples. I adore learning programming on examples with short description.
And please don't send me to google or some sites. If you tell me about some online course, I'll highly appreciate this but I still prefer good old paper books. (:

---

### Post by cabalas on 2009-03-25
Learn to love the [MSDN]("http://msdn.microsoft.com") it will make your life so much easier.  Granted I didn't learn c# from a book, I just mashed it together out of my knowledge of C like languages and the MSDN and it went ok for me.

However seeing as you asked for a book recommendation I recently picked [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries]("http://www.amazon.com/Framework-Design-Guidelines-Conventions-Development/dp/0321545613/") and found it to be really good, also in that series is [The C# Programming Language]("http://www.amazon.com/gp/product/0321562992") which if it is as good as Framework design guidelines should be very useful to you.

---

### Post by scottuss on 2009-03-25
You can't go wrong with Python, it will run on Windows, Mac and Linux and has loads of really cool libraries to do pretty much anything.

And I have to say your example was very strange. You haven't been commissioned to write such an app have you? Strange that you would mention it being a commercial product too... :s

---

### Post by Eugene_Bondarenko on 2009-03-25
> **cabalas said:**
> Learn to love the [MSDN]("http://msdn.microsoft.com") it will make your life so much easier.  Granted I didn't learn c# from a book, I just mashed it together out of my knowledge of C like languages and the MSDN and it went ok for me.

However seeing as you asked for a book recommendation I recently picked [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries]("http://www.amazon.com/Framework-Design-Guidelines-Conventions-Development/dp/0321545613/") and found it to be really good, also in that series is [The C# Programming Language]("http://www.amazon.com/gp/product/0321562992") which if it is as good as Framework design guidelines should be very useful to you.
Thanks much! I'll check out those books :)


> **scottuss said:**
> You can't go wrong with Python, it will run on Windows, Mac and Linux and has loads of really cool libraries to do pretty much anything.

And I have to say your example was very strange. You haven't been commissioned to write such an app have you? Strange that you would mention it being a commercial product too... :s
LOL, no. To start with I am more than 100% sure the programme from the example exists and is already polished to run perfectly. We all know what a huge problem spam is.
It's just the first example that has intense internet use and heavily loaded DB that came to my mind. And to continue this subject I know quite some of web security so if I were to join the dark side I'd already be there. :biggrin:  However I don't see any point in this. I can use my skills on creating safer websites instead of making harm to Internet. :)
About me mentioning that the product is commercial. I simply wonder how this works in real life. And I am trying to play in developing a real product. :) You see, all the Windows applications I installed required just a few clicks on next button. And I never saw something like "And now you need to install MySQL server (pls read this long manual) and Python compiler (here is another long manual)". However if there is a way to run Python apps without that compiler, it will make me to think about C# vs Python :)

---

### Post by Can+~ on 2009-03-25
> **Eugene_Bondarenko said:**
> However if there is a way to run Python apps without that compiler, it will make me to think about C# vs Python :)

[http://www.py2exe.org/](http://www.py2exe.org/)

Although, I've never used it. I guess it embeds the python interpreter with the program. And python comes with it's own sqlite library at hand.

---

### Post by Eugene_Bondarenko on 2009-03-25
Wow, thanks. I guess now it's time to make intense googling for C# vs Python. :)
However knowing that the holy Google uses python makes it hard to be objective. But I'll try. :mrgreen:
By the way, any books you can advise?
Oh, and another question. Does Python have any GUI? I mean all that pretty windows and buttons and so on that Windows apps have? :)


Also it's time to start licensing thread. While creating PHP apps I've faced some of such questions and I really wonder how GNU GPL and commercial licenses compile together. I had to forward those issues to my boss but I now I want to fill up this gap :D

---

### Post by janfsd on 2009-03-26
What about qt4?

---

### Post by Eugene_Bondarenko on 2009-03-26
Wow, judging from their demos it looks very very nice. Did you have any experience with it? Are there all cool libraries (like regular expressions, DBs) inside. And how hard is it to learn and use it vs C# and vs Python. And what is the situation on the market? Isn't this some exotic language that is not widely used in real life?

[http://www.qtsoftware.com/qt-in-use/story/app/google-earth](http://www.qtsoftware.com/qt-in-use/story/app/google-earth)
Is google earth really developed in QT4? :shock: It's just the first time I hear about this language and I didn't expect it to be used in such an epic product.

---

### Post by Sinkingships7 on 2009-03-26
> **Eugene_Bondarenko said:**
> Wow, judging from their demos it looks very very nice. Did you have any experience with it? Are there all cool libraries (like regular expressions, DBs) inside. And how hard is it to learn and use it vs C# and vs Python. And what is the situation on the market? Isn't this some exotic language that is not widely used in real life?

[http://www.qtsoftware.com/qt-in-use/story/app/google-earth](http://www.qtsoftware.com/qt-in-use/story/app/google-earth)
Is google earth really developed in QT4? :shock: It's just the first time I hear about this language and I didn't expect it to be used in such an epic product.

Qt4 isn't so much a language as it is a library that interfaces with several languages, C++ being it's first choice. It has bindings for many languages, including Python of course.

I highly recommend it.

---

### Post by Eugene_Bondarenko on 2009-03-26
So they just took C++ (and other languages) and built up their nice and easy-to use interface around it. Do I understand it correctly?

---

### Post by Eugene_Bondarenko on 2009-03-26
By the way are there any weighty arguments in QT4 vs C# competition?

---

### Post by Delever on 2009-03-26
> **Eugene_Bondarenko said:**
> By the way are there any weighty arguments in QT4 vs C# competition?

Qt4 is GUI library, and can be used from many languages, including C#: [http://techbase.kde.org/Development/Languages/Qyoto](http://techbase.kde.org/Development/Languages/Qyoto)
and here
[http://imaginary-project.net/wiki/qyoto](http://imaginary-project.net/wiki/qyoto)

---

### Post by crush304 on 2009-03-26
if you go the c# route don't forget to check out the free visual studio

[http://www.microsoft.com/Express/](http://www.microsoft.com/Express/) there is a version for c# and a seperate version for the web development (which you can also use c# for)

also take a look at the sql server compact, [http://www.microsoft.com/Sqlserver/2005/en/us/compact.aspx](http://www.microsoft.com/Sqlserver/2005/en/us/compact.aspx) it is more or less microsofts version of sqlite but generally compatible w/ MS Sql Server you should get an option to install it with Visual Studio Express

---

### Post by Sinkingships7 on 2009-03-26
> **Eugene_Bondarenko said:**
> So they just took C++ (and other languages) and built up their nice and easy-to use interface around it. Do I understand it correctly?

Sort of. It's more like... for example, nobody could properly say "I wrote a program in Qt4." They'd have to say "I wrote a program in <insert language here> using the Qt4 library."

You use your language of choice (provided that Qt4 has a binding for it) and use Qt4 like you would with a built in library.

This example should help make it clear. Keep in mind that this is **NOT** valid Qt4 usage -- just an example.

In Python, there's a library called **sys**. Well, we call them modules, but anyway. In this library is a function called **exit()**, which quits the currently running program. You use it like this:

[php]
import sys

print "I'm a Python 2.6 program, and I'm currently running!"
sys.exit(0)  # I'm a comment, here to tell you that the code to the left stops this program from running.
[/php]

Well, lets say that Qt4 has a function that allows us to exit even better! :lolflag:

This is how we'd accomplish this task:
[php]
import qt4

print "I'm a program!"
qt4.exitEvenBetter()
[/php]

See? It's just a library with a lot of useful classes and functions. Mostly for building GUI interfaces. I've also heard great things about Qt4 creator, so you might wanna look into that.

---

### Post by Eugene_Bondarenko on 2009-03-26
Wow, thanks, I've almost managed to get the pieces of puzzle together. :) The last question I am curious about:
Is there any actual difference between QT4 <language of choise1> and QT4 <language of choise2>? So let's say if we now work in QT4 PHP, we'll have absoultely the same result but we'll have to use another syntax instead? Something like:
[PHP]
include_once 'qt4.lib';

print "I'm a program!";
qt4::exitEvenBetter()  
[/PHP]
Is that right? And then how do they allow us to build that nice GUI I saw in the demo videos? Is that possible to do with their editor and some built in QT classes? Will that work even for languages such as PHP (and I guess Python goes here too) that do mostly server backend work and don't have anything that can be called GUI?

---

### Post by Can+~ on 2009-03-26
QT4 is a system of it's own, like OpenGL, SDL, GTK+. Everything inside QT4 is not of your business, but to work with it you need a binding with a  language, from the user's standpoint, there's virtually no differences between a QT4+C++, QT4+Python or a QT4+PHP (as long as there are bindings available).

Any language is capable of doing anything, as long as it has a binding library for it. Some languages might be easier than others for this task.

(And Google Earth is not just QT, it also sports OpenGL to create the big blue sphere (aka. Earth))

Now, with interpreted languages (PHP included), the user will need a PHP interpreter installed, same goes for Python.

I think your choice narrows down to:
-C# with Visual Studio (Express available for free) and stick to windows (and mono or wine for linux)
-Java + SWT, it's kinda common to see Java installed.
-Python + GTK+/QT4, and pack the python interpreter with the app.
-C/C++ + a graphic cross-platform library. (Although, I personally think that Low level languages with GUIs is kinda painful to program)

PHP could also work, but I don't think it's very popular on the client side.

---

### Post by directhex on 2009-03-26
> **Eugene_Bondarenko said:**
> Wow, thanks, I've almost managed to get the pieces of puzzle together. :) The last question I am curious about:
Is there any actual difference between QT4 <language of choise1> and QT4 <language of choise2>? So let's say if we now work in QT4 PHP, we'll have absoultely the same result but we'll have to use another syntax instead?

Your choices for languages outside the default (Qt4 is C++) are those provided by the kdebindings source package: Python, Ruby, and CLI (.NET languages like C#); languages provided by other bindings projects: Java. As is usually the case, the quality of the bindings is tiered - i.e. C++ Qt is MUCH faster than, say, C# Qt, due to limitations of the bridge library used to allow non-C++ languages to talk to Qt.

Not to say it can't be done - take [http://synapse.im/](http://synapse.im/) as an example of a Qt app written in C#. Additionally, the toolchains are usually built around a single language (other languages take extra work)

Other windowing toolkits may change your language choices - e.g. GTK+ is C, and has bindings for C++, Python, Ruby, OCaml, Java, Scheme, Haskell, Perl, CLI (.NET) and more

---

### Post by wrtpeeps on 2009-03-26
Go for C#. It's a good one to know in terms of employability too.

---

### Post by janfsd on 2009-03-27
> **Eugene_Bondarenko said:**
> Wow, judging from their demos it looks very very nice. Did you have any experience with it? Are there all cool libraries (like regular expressions, DBs) inside. And how hard is it to learn and use it vs C# and vs Python. And what is the situation on the market? Isn't this some exotic language that is not widely used in real life?

[http://www.qtsoftware.com/qt-in-use/story/app/google-earth](http://www.qtsoftware.com/qt-in-use/story/app/google-earth)
Is google earth really developed in QT4? :shock: It's just the first time I hear about this language and I didn't expect it to be used in such an epic product.
Well, I can't say much, since I just started learning qt4. Here's a good free book: [http://cartan.cas.suffolk.edu/oopdocbook/opensource](http://cartan.cas.suffolk.edu/oopdocbook/opensource)
About regular expressions, qt4 supports them.

---

