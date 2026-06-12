---
title: "Please offer programming language suggestions"
date: 2013-04-02
forum: Programming Talk
---

### Post by aqualion on 2013-04-02
I would like to learn to program.  What language should I begin with?  What IDE should I begin with?  What book or ebook should I begin with?

---

### Post by r-senior on 2013-04-02
You should begin with the sticky post at the top of the forum. The one entitled "Programming Guides and Basics - Read Me First".

It's only fair to warn you that, in the entire history of the internet, nobody who has ever asked this question on a programming forum has ever received a simple, unbiased answer that led them to a clear path of enlightenment and discovery.

---

### Post by iMac71 on 2013-04-02
I suggest python; it's preinstalled, hence you can invoke it simply typing```
python
```in a Terminal window.
You may install its IDE, called [IDLE]("http://docs.python.org/2/library/idle.html"), simply typing```
sudo apt-get install -y idle
```in a Terminal window.
And you should begin with its [tutorial]("http://docs.python.org/2/tutorial/index.html").

---

### Post by aqualion on 2013-04-02
> **r-senior said:**
> You should begin with the sticky post at the top of the forum. The one entitled "Programming Guides and Basics - Read Me First".

Thank you.  I followed several of those links (one is now a dead end) and came to the MonoDevelop IDE.  The Ubuntu Software Center says that it is a Gnome IDE.  Does that mean that I have to have the Gnome desktop environment running or does it mean something else?

---

### Post by iMac71 on 2013-04-02
> **aqualion said:**
> I followed several of those links (one is now a dead end) and came to the MonoDevelop IDE.  The Ubuntu Software Center says that it is a Gnome IDE.  Does that mean that I have to have the Gnome desktop environment running or does it mean something else?Ubuntu is GNOME-based, hence you may install MonoDevelop IDE without installing Gnome Desktop Environment.

---

### Post by slickymaster on 2013-04-02
I suggest you to read these two articles.

[Tips on choosing a programming language to learn]("http://www.techrepublic.com/blog/programming-and-development/tips-on-choosing-a-programming-language-to-learn/1950")
[Strategies for learning programming languages - what works and what doesn't ]("http://www.techrepublic.com/blog/programming-and-development/strategies-for-learning-programming-languages-what-works-and-what-doesnt/1159")

---

### Post by Mikeb85 on 2013-04-02
> **aqualion said:**
> I would like to learn to program.  What language should I begin with?  What IDE should I begin with?  What book or ebook should I begin with?

Javascript (Node.js), Python or Ruby.   All are easy to install, and there are plenty of free learning resources out there.   Codecademy, Rubymonk are two websites I used.

Don't worry about IDEs, start with the command line and Text Editor.

---

### Post by Habitual on 2013-04-02
> **aqualion said:**
> What IDE should I begin with?
[http://en.wikipedia.org/wiki/Integrated_development_environment](http://en.wikipedia.org/wiki/Integrated_development_environment)

---

### Post by aqualion on 2013-04-02
> **Mikeb85 said:**
> Don't worry about IDEs, start with the command line and Text Editor.

May I ask why not an IDE?

---

### Post by DaviesX on 2013-04-02
Cause linuxers typically don't use IDEs. But I don't care. IDEs makes your life easier. 
If you want to do low-level development, it won't go wrong to start with c and then c++. 
code::blocks is a good IDE for c/c++ available in ubuntu.

---

### Post by r-senior on 2013-04-03
I think there are three main arguments for not starting with an IDE:

[LIST=1]
[*]To better understand the build process so that you are more likely to develop the knowledge to fix problems that arise.
[*]To learn by looking at documentation and typing out the code rather than relying on code completion.
[*]To learn the shell and useful standalone tools like make, maven, bash.
[/LIST]
Taking Java as an example, it is beneficial to understand the process of turning .java files into .class files, where to put the .class files and how to build and incorporate libraries of code in .jar files. With C/C++ it is beneficial to understand compilation, linking, headers and libraries. With Python it is beneficial to understand imports, modules and precompilation. Because an IDE handles a lot of this, new programmers often get lost when they try something beyond the bounds of a tutorial based around an IDE. Or perhaps when they have to handle code that wasn't set up for a specific IDE.

As far as code completion goes, it depends on the person learning, and perhaps the language. Some people learn better by working methodically and digesting documentation. Others work better by experimentation and filling in details later. An IDE helps with the latter.

Learning the shell and standalone tools is always a good idea, but using an IDE doesn't necessarily stop you doing that.

Personally I think there are benefits to doing something without an IDE as part of the learning process. Programmers, particularly those coming from Windows, can get too reliant on the IDE environment and not explore features of the shell and standalone tools. But DaviesX is quite right that IDEs make working with some languages easier. I wouldn't like to work on a large Java or Objective-C project without an IDE because typing things like ClassPathXmlApplicationContext and NSUbiquitousKeyValueStoreDidChangeExternallyNotification is hard work. For C and Python I'm happier without an IDE.

As long as you reach the end point I don't think the path is important. That means learning the language, how projects fit together and how they are installed. If you choose to use an IDE, just make some effort to understand what it is doing for you and learn to appreciate the power of the command line environment (which is an IDE in itself).

---

### Post by tehcavil on 2013-04-03
Language: Scheme

Book (online version, free, although you can buy a copy):

[http://mitpress.mit.edu/sicp/full-text/book/book.html](http://mitpress.mit.edu/sicp/full-text/book/book.html)

Scheme interpreter:

[http://www.gnu.org/software/mit-scheme/](http://www.gnu.org/software/mit-scheme/)

---

### Post by Mikeb85 on 2013-04-03
> **aqualion said:**
> May I ask why not an IDE?

It hides and automates some processes which are useful to learn.  Plus, they only really give an advantage when you start working on decent-sized apps (or for languages like Java which have a ton of boilerplate code and will make you hate life).  For the scripts and small programs you'll likely be starting out with, they're just added complexity with no benefit.  Use an IDE when you make a GUI app or larger web app...

---

### Post by gordintoronto on 2013-04-03
Full Circle Magazine has a long series on Programming in Python, and the series has been extracted into a series of PDFs. Python is a decent choice as a beginning language. I always felt that BASIC on the Commodore 64 was a better entry point, though. fullcirclemagazine.org

My first programming language was Autocoder on the IBM 1401. If "Autocoder" sounds easy, it was a complete fraud: it was assembly language.

---

### Post by Moose on 2013-04-03
> **r-senior said:**
> You should begin with the sticky post at the top of the forum. The one entitled "Programming Guides and Basics - Read Me First".

It's only fair to warn you that, in the entire history of the internet, nobody who has ever asked this question on a programming forum has ever received a simple, unbiased answer that led them to a clear path of enlightenment and discovery.

Couldn't have explained it better myself.

It all depends on what sort of apps you want to make.

---

### Post by Stonecold1995 on 2013-04-03
> **aqualion said:**
> May I ask why not an IDE?
Basically, IDEs are for programmers who are only focusing on efficiency (such as in job setting), not focusing on learning the language.  Once you have everything down and you are very proficient (which takes years), you can use an IDE to do things as quickly as possible, because you only have to think about the bare minimum.

I suppose it's like giving someone an automated spell checker when they're trying to learn a new (human) language.  It would be a bad idea to do so because a spell checker assumes you already know it, so it will automatically correct words instead of letting you learn yourself because it thinks you only want to be able to type fast with minimal errors.

---

### Post by akvino on 2013-04-04
Before you do ANYTHING spend 45 minutes to see this:
[http://channel9.msdn.com/posts/C-and-Beyond-2011-Herb-Sutter-Why-C](http://channel9.msdn.com/posts/C-and-Beyond-2011-Herb-Sutter-Why-C)

---

### Post by akvino on 2013-04-04
> My first programming language was Autocoder on the IBM 1401. If "Autocoder" sounds easy, it was a complete fraud: it was assembly language.

Hhahaha well who said you can't get the real laugh out of the 'what language is the one that fits all' threads.

---

### Post by ofnuts on 2013-04-04
> **Mikeb85 said:**
> For the scripts and small programs you'll likely be starting out with, they're just added complexity with no benefit. 

I beg to differ... one big advantage of IDEs over plain editors for beginners is that they point out errors while you type...  You aren't left trying to guess where you forgot to close quotes or parenthese, assuming you notice this particular error among the 30 or so cascading errors this generated at compile time. For learned programmers this isn't a problem but we tend to forget this is an acquired skill.

---

### Post by edm1 on 2013-04-04
I couldn't recommend the [MIT opencourseware 6.00 course]("http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/6-00sc-introduction-to-computer-science-and-programming-spring-2011/") more. It uses python and is **very** well taught. If you treat it like a proper course and make your way through from start to finish, watching all the video lectures and doing all the reading and assignments then you will be very well positioned to begin learning more advanced stuff.

I learnt more doing this one module then I did in an entire year studying computational biology.

---

### Post by lisati on 2013-04-04
@aqualion: As you can probably tell, there's no "one answer fits all" solution for figuring out which programming language or IDE to use. 

The dialect of Fortran I used to write my first program back in the 1970s, using port-a-punch cards, probably suited the environment at the time, but it wouldn't suit the needs of today's programmers.

Many of the opinions you're likely to encounter in this forum can be summed up with the saying, *use what works*. Languages which have C as part of their heritage (or which provided some of the inspiration for their development) seem to be popular here. 

Don't shy away from reading up and learning what you can before you decide what to use.

---

