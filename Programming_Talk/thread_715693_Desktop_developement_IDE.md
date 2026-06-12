---
title: "Desktop developement IDE?"
date: 2008-03-05
forum: Programming Talk
---

### Post by shinems on 2008-03-05
I am into ERP.Is there a Desktop development IDE in Linux? PHP cant be used and I have worked on that.Are there other alternatives?Also the professional development of DotNet applications in Ubuntu is a success?Pls reply.I am a die hard Ubuntu fan.

:popcorn:


:KS

---

### Post by shinems on 2008-03-05
I am into ERP.Is there a Desktop development IDE in Linux? PHP cant be used and I have worked on that.Are there other alternatives?Also the professional development of DotNet applications in Ubuntu is a success?Pls reply.I am a die hard Ubuntu fan.

---

### Post by shinems on 2008-03-05
java is an answer?or python?


:popcorn:

---

### Post by Caduceus on 2008-03-05
Depends on what you want to make, "desktop development" isn't very clear.

---

### Post by shinems on 2008-03-05
Windows application/desktop application.

For ex: exe applications in Windows like mspaint etc.

Reply.

:popcorn:

---

### Post by Caduceus on 2008-03-05
It's not a good idea to make Windows programs in Linux. Going by your previous topic, you'd best stick with Windows.

---

### Post by shinems on 2008-03-05
I mean not windows OS.In fact, standalone programs unlike that runs on browsers.Can we develop that in linux?It should be portable in all OS.

:popcorn:






:lolflag:

---

### Post by akudewan on 2008-03-05
> **shinems said:**
> I mean not windows OS.In fact, standalone programs unlike that runs on browsers.Can we develop that in linux?It should be portable in all OS.

:popcorn:






:lolflag:

Portable? Maybe Qt or GTK with C++, or Java. Python is a good option...

---

### Post by jespdj on 2008-03-05
There are lots of IDEs for writing software.

For Java, [Eclipse](http://www.eclipse.org/) or [NetBeans](http://www.netbeans.org/) for example. [Anjuta DevStudio](http://anjuta.sourceforge.net/) is a good IDE for C / C++ which has useful tools for developing GNOME / GTK+ applications. Many desktop applications for Linux are written in Python. I'm not a Python expert but I'm sure there are good IDEs for Python available also. There is an implementation of .NET called Mono, and there's [MonoDevelop](http://www.monodevelop.com/Main_Page) for developing software in C# and other programming languages.

[SIZE="1"](p.s. try searching with Google for "linux programming ide" or something like that...).[/SIZE]

---

### Post by mssever on 2008-03-05
A combination of Python, wxPython, and wxGlade might be what you're looking for. Don't worry too much about an IDE. You don't really need one for Python.

---

### Post by shinems on 2008-03-05
In java, can we make stand-alones?

In python, can we do big RDBMS projects?

---

### Post by LaRoza on 2008-03-06
> **shinems said:**
> In java, can we make stand-alones?

In python, can we do big RDBMS projects?

You can make programs in Java and Python.

In fact, you can use Python on the Java platform (Jython) and you can use Python on the .NET platform (IronPython).

Both can be used with database servers.

---

### Post by Tsega on 2008-03-06
> **shinems said:**
> In java, can we make stand-alones?

In python, can we do big RDBMS projects?

Sure you can, I can name you one the bit torrent client, Azureus - [http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)  (made with Java  i.e. platform independent)  and if you need an IDE pick Netbeans (netbeans.org). It is excellent! 
I don't know much about Python but it is said that it is the language of choice on Ubuntu. I am going to look into that soon.

---

### Post by shinems on 2008-03-06
How can ERP be developed in Linux?


:popcorn:

---

### Post by pmasiar on 2008-03-06
Check [http://en.wikipedia.org/wiki/Tiny_ERP](http://en.wikipedia.org/wiki/Tiny_ERP) - opensource ERP in Python

---

### Post by shinems on 2008-03-11
i donno python.i know java,php.

in fact, i have created an online shopping cart in java.

can u say wat are the options in ubuntu for java?

---

### Post by shinems on 2008-03-11
i guess java is really robust and cool.wanna go to java one day.

:popcorn:

---

### Post by LaRoza on 2008-03-11
You can use Java in Ubuntu, it works the same as it does in Windows.

See the sticky for using Java in Ubuntu.

---

### Post by shinems on 2008-03-12
thanx pal.its gr8 that u r doing a gr8 service free of cost.........

keep up the spirit.........


:popcorn:

---

### Post by shinems on 2008-03-14
i am switching into python.the syntax of it has really amazed me.just a few lines!i had an opportunity to view the seminar on python by Swaroop of Yahoo! fame.


              i have worked on java before.but i think python is great.in India, we have less opportunities in python.what about in other parts of world?is it a complete language?

:popcorn:

---

### Post by shinems on 2008-03-22
I recently switched to kubuntu from edubuntu.Is that a right decision as far as developement esp in python is considered?I think kubuntu interface is more professional.Also which is best IDE for python?I found many.

:)

---

### Post by LaRoza on 2008-03-22
> **shinems said:**
> I recently switched to kubuntu from edubuntu.Is that a right decision as far as developement esp in python is considered?I think kubuntu interface is more professional.Also which is best IDE for python?I found many.

:)

Linux is Linux. Python works the same (mostly) on any platform. It doesn't make a difference.

The best IDE is the one you like the most.

---

### Post by shinems on 2008-03-22
Cool answer....

I saw somewhere while surfing that kubuntu is used more for developement.is it true?or is it another hoax?


:popcorn:

---

### Post by LaRoza on 2008-03-22
> **shinems said:**
> Cool answer....

I saw somewhere while surfing that kubuntu is used more for developement.is it true?or is it another hoax?


QT has great documentation, and some good tools (I hear, I never used QT) and KDE uses QT, so it would have an appeal to people using QT.

It is likely just a general statement based on a few cases.

Linus himself uses many distros, and likes usability I think. RMS uses gNewSense (which is Ubuntu 6.06 altered to reflect the FSF's philosophy to a tee).

I have never actually used Kubuntu, but I have installed the Kubuntu packages on Ubuntu before. Personally, I either install Ubuntu, or do a base install and add only what I want.

(I am also a fan of OpenSUSE, Arch, and Slackware)

---

### Post by pmasiar on 2008-03-22
Original ubuntu is gnome-based, so I would expect it is still more supported than kubuntu. I recall recently Canonical hired some kubuntu developers, so K-people rejoiced that kubuntu will not be second-class citizen anymore.... It suggests that it **was** before, at least in KDE community perception. :-)

It is true that KDE is very active in development tools and customization, but I prefer GNOME approach (the "less is more" approach): I don't want to tweak every imaginable dial in my GUI, give me reasonable defaults, and let me change it if I need, but only important setting (those likely be changed) should be on the surface. The more obscure setting, the deeper it should be hidden. Ideally, fresh install needs just couple touches and is usable in a minute.

Your preference is in what GUI toolkit you want to use for your Python desktop app development: If Qt, use kubuntu of course. If you are not developing desktop app, it does not matter, use what gives you tools you prefer.

Edubuntu is different in sense it is targeted not to developers like k/ubuntu is, but to school children. Which might not be compatible with your interests.

---

### Post by shinems on 2008-04-03
Is there something similar to standalone exe of windows in linux?and what about DLLs?

:popcorn:

---

### Post by Zugzwang on 2008-04-03
Of course there are exucutable in linux, they normally just don't have the .exe extension (no need to have it - their executable flag is just set).

There are shared libraries as well (.so is a commonly used extension but there are others AFAIK) - these do normally have a .DLL extension in Windows.

However, most of the people will tell you here that making (binary) executables is not so important. It doesn't matter what's behind the scenes if they can just start the program by clicking or typing the command in the console. You might want to read some stuff on deployment for Linux, the preferred way is to use the package manager. Second best is distributing source packages. But somehow I'm guessing that you have commercial interests, so the latter option might not be what you want.

---

