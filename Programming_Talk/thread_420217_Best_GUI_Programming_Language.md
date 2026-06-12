---
title: "Best GUI Programming Language"
date: 2007-04-23
forum: Programming Talk
---

### Post by wiebers10 on 2007-04-23
I am looking to create a media jukebox program with my spare time this summer.  I was wondering what GUI programming languages people prefer.  I have taken classes in C and Java.  I've been thinking about using python after reading a few guides but I keep hearing things about Ruby and wondering what the advantages or disadvantages of each are or if I should just use something else.

---

### Post by pmasiar on 2007-04-23
> **wiebers10 said:**
>  I was wondering what GUI programming languages people prefer.  I have taken classes in C and Java.  I've been thinking about using python after reading a few guides but I keep hearing things about Ruby and wondering what the advantages or disadvantages of each are or if I should just use something else.

There are many "ruby vs Python" threads, last one: [ Ruby & Python, which has the future?](http://ubuntuforums.org/showthread.php?t=419889), check also my link (comment #5) to previous thread.

Python and Ruby are very close to each other. Ruby was beating Python in web apps 2 years ago with Rails, since then Python closed the gap (in web apps) via Django and TurboGears. Outside web apps, Python was always ahead of Ruby: because is little older, Python has more libraries, more support, bigger acceptance. Python was widely used *outside* of web apps - thats why web app area was neglected and Ruby moved there :-)

Python is more readable, and used as main language for Ubuntu (and is strong in Google), I recommend it over Ruby. I do web apps, so I cannot recommend GUI from my own experience but wxPython is going strong.

There are couple Python projects like you plan to do, you may consider joining one instead of starting new, IMHO. But either way, good luck!

---

### Post by Tesiph on 2007-04-23
Python is indeed a very usable language. For creating GUI interfaces with it you can try wxWidgets . If you want to stick with java you can use SWT (wich has eclipse support). Both provide cross-platform native controls for you applications.
I personally find Glade to work perfectly for creating gnome applications.

---

### Post by Max_Might on 2007-04-23
You can try with PyGTK ... :)

---

### Post by maddog39 on 2007-04-27
Hey, whatever happened to PHP lol. PHP is like the C of web app languages, or no maybe thats perl and PHP is the C++, lol whatever. I never liked ruby and find that it wasnt really accepted as a web development platform. As far as web development I prefer PHP over anything, perl is a disaster and python is terrible in my opinion for making websites.

Now for GUIs, your probably better off with C or C++ for desktop applications really. If you want something easy, Python is definetly the way to go with easy-to-build desktop apps on any platform. PHP is getting there but PHP-GTK is a big pain to install under any system and ubuntu doesnt have a package for it yet so, I'd recommend Python. You get just about the same speeds/performance as C++ and the same amount of freedom on which GUI toolkit you'd like to use.

---

### Post by Eric_T on 2007-04-27
If you already know Java, why not just use that? I think it's pretty easy to create GUIs with Java.
Definitely easier than first learning a new language and then learning a new GUI toolkit.

---

### Post by Tuna-Fish on 2007-04-27
Eric_T: but if he only knows C and java so far, learning a new language has plenty of value in it's own right, and imho, still the best way to learn a language is to write a program in it and learn along the way.

I'd also suggest python. If you want to create the gui graphically, perhaps glade might be of help?

---

### Post by pmasiar on 2007-04-27
I also advice trying Python first. Java was designed for enterprise-level applications, where dozens of replacable coders crank millions of lines of code according to corporate standards. It is not for quick fun hacking.

[RAD](http://en.wikipedia.org/wiki/Rapid_application_development) languages Like Perl and Python were designed for quick hacking.

IMHO: if OP is *NOT* steeped-in Java expert with deep knowledge of myriads of Java objects and libraries, learning Python syntax (one week max) and relevant python libraries will be faster than doing same in Java. Flexible Python data structures will greatly simplify coding. Especially for beginner. Thats all I do in my day job: trying to navigate between subtly different Java data objects, trying to cast one object into another, to massage data and squeeze my output. Not easy.

Python makes simple things easy and hard things possible. Java makes hard thing possible, but simple things hard.

You may want also look into [PyGame](http://en.wikipedia.org/wiki/PyGame) for simplified GUI.

---

### Post by laxmanb on 2007-04-28
I'd say go for Java... It's incredibly simply to build GUIs using a Java IDE...

Plugin your GUI with a light weight DB like Java DB/SQLLite for media library... (JDBC)

...there are lots of APIs for Media Playback... for eg. Java Media Framework or Java VLC Bindings(jvlc)...

No matter which language you choose, Best of luck!!

---

### Post by iblis on 2007-04-28
I'm admittedly bias, but I'd go with Python.  It's clean, it's easy, and most importantly, it's really **fun** to develop in. And if you need modules, head on to the [cheese shop]("http://cheeseshop.python.org/pypi/"). But again, I'm bias. :D

Perl is also a nice one to use. It's got a strong user base,  friendly community (i.e., perlmonks.org), and you have all the power of [CPAN]("http://cpan.org/") on your side for your module pleasure.

Both have GTK libraries out the wazoo, both have Glade support, and both lean towards ease of use. 

Of course, if you're looking for raw speed,  or are using an older machine (400mhz, etc) stick with C. But most modern machines can run Perl and Python applications with no problem. (Ubuntu makes use of both)

Just my opinion. Use whatever you fancy. :D

---

