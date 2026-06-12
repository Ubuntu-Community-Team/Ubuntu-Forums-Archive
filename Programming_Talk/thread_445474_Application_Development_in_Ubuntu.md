---
title: "Application Development in Ubuntu"
date: 2007-05-15
forum: Programming Talk
---

### Post by acb5042 on 2007-05-15
Hey guys!

I'm happy to say that this is my first day using Ubuntu! :) I've been a Windows user my entire life, but I got a spare computer so I decided to try it out. I don't plan on switching soon since Microsoft Office is just that good, but I've been slowly migrating to free software since I'm a penny-less student haha. In fact, most of my Windows apps could also run on Ubuntu. At any rate, I had used some variant of Linux before and I remembered how complicated it was -- Ubuntu looks good, works good, and seems easy enough for the average user. I'm very impressed!

Well, please don't flame me for my pretty newbish question because I'm definitely not new to programming. Application development on Windows is pretty straight forwards. You boot up Visual Studio and there you go. Visual Studio and the .NET Framework do an amazing job at everything. It's programmer friendly to the max.

Let's say I wanted to play around with some Ubuntu application development. Where should I start? What IDE should I download? What libraries should I get? How come there are *dozens* of different GUI libraries? What's the difference? How do I package my application for distribution? Where are user application profiles kept? Is C++ the choice language for development? Would Ruby work well too?

I guess need some pointers to set me in the right direction. I've searched for this topic but found nothing useful.

Note: I've coded some C++ tools in Solaris/UNIX (multi-threaded even) so I know a bit about the file system and command line. And oh yeah, Java is a no-no. :)

---

### Post by foresth on 2007-05-16
I have only one thing to say:

[http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

:).

---

### Post by pmasiar on 2007-05-16
> **acb5042 said:**
> Visual Studio and the .NET Framework do an amazing job at everything. It's programmer friendly to the max.

Let's say I wanted to play around with some Ubuntu application development. Where should I start? What IDE should I download? What libraries should I get? How come there are *dozens* of different GUI libraries? What's the difference? How do I package my application for distribution? Where are user application profiles kept? 

You are experiencing shock from too much freedom of choice. :-)

Windows development was "simpler" because it was "one size fits all" proposition. Which is obviously not true.

Your language of choice depends on application area. Python becomes increasingly popular, and is preferred for Ubuntu development.

Very good strategy is creating prototype of your application in a RAD (Rapid app development, check wikipedia) language like Python, where you can use multiple strategies of implementation, profile your code to find bottlenecks ("don't guess: measure") and reimplement those in C.

Forum's sticky and my sig has many links to Python resources. wxPython is very popular GUI thing. Multiple IDEs are available, but hardcore hackers prefer creating own environment using customizable editors (vi/emacs).

Apps are distributed as (debian/redhat etc) packages.

---

### Post by samjh on 2007-05-16
> **acb5042 said:**
> Well, please don't flame me for my pretty newbish question because I'm definitely not new to programming. Application development on Windows is pretty straight forwards. You boot up Visual Studio and there you go. Visual Studio and the .NET Framework do an amazing job at everything. It's programmer friendly to the max.

If you are good at working with .NET, the Mono project should fit well for you.  Look at the link Foresth has posted earlier.  It's basically an open-source effort at producing a .NET-compatible development framework.  Works quite well.

Or you can take Pmasiar's advice and try Python.  A worthy language.

---

### Post by acb5042 on 2007-05-16
Thanks guys for your replies.

I guess my next question is, how popular is Ruby in these circles? For various reasons, I would not like to use Python; Ruby is a near equivalent and I personally think its a lot nicer.

Are interpreted languages that popular in Ubuntu development? Why not use straight C/C++? For the ease of use? Don't users care about performance? I suppose it's not that critical for most applications?

Next, which GUI library do you recommend? I've found TK, GTK, Fox, wxWidgets, FLTK, etc. There are way too many and they seem to have orthogonal features. Which one is most often used? Is wxWidgets the way to go, as pmasiar stated?

Sorry guys for my basic questions. I'm just trying to get started with Ubuntu.

---

### Post by acb5042 on 2007-05-16
I think I answered my own question about the GUI libraries. [Here's](http://www.rubygarden.org/Ruby/page/show/ComparingGuiToolkits) a great resource detailing the different GUI libraries available for Ruby, for future reference. I suppose wxWidgets is the way to go.

---

### Post by pmasiar on 2007-05-16
Ruby is younger, slightly less popular  (and has less libraries) than Python. Although Ruby is universal language like Perl and Python, is mostly used (on Rails) for web app development. Ubuntu uses Python as standard development language (Mark likes it :-) ).

IMNSHO Ruby is less readable than Python - it is closer to Perl - which is *bad* :-) 

Performance? Most important speed is *speed to market*. Ease of enhancing is important too - the more lines of code, the harder is to find bugs and fix them. See thread [ What language is used in the professional world](http://ubuntuforums.org/showthread.php?t=443418) for most recent discussion - language comparision is all-time favorite :-)

Of course you are free to use any language you prefer. 

Just curious: Do you dislike significant whitespace in Python?

---

### Post by theDentist on 2007-05-16
If you are used to VS in microsoft or used MFC libraries, then wxWidgets is a good one to try, If you buy the book (there is only one that I know of), you get a copy of the excellent IDE, DialogBlocks, which I find easy to use and extremely good at rapid development of the GUI.  It is very similar to Microsoft's MFC i.e. VC++ 6. It's not perfect, but what is! It's fulfilled my needs for writing apps for Ubuntu. It supposed to be cross-platform but I've discovered that you have to decide which platform you intend the target to be, and write for that. The same code doesn't behave the same way when you switch from Linux to Windows.  Dialogblocks lets you build a static executable which is useful as I've found the binary to run on most distro's with no library problems, just run it straight from the command line.

---

### Post by acb5042 on 2007-05-16
I like Ruby because I use Ruby on Rails. I have a lot of code on Rails and I really, really like ActiveRecord. Ruby's message-passing object oriented scheme seems to flexible. Python doesn't seem that way. Plus I don't like the idea of whitespace being significant -- too much room for error. Nonetheless, I'm not writing off Python or dissing it; I just prefer Ruby.

---

### Post by pmasiar on 2007-05-16
OK, if you are heavy RoR user, Python is not as big improvement as it is for Java/C# coders :-)

Significant whitespace means that your code has correct indent (wrong indent is syntax error) - and also that your colleague uses the same indent coding standards, so it is easier to share code.

---

