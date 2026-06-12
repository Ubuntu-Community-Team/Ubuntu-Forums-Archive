---
title: "Cross-platform compatibility &amp; Python"
date: 2009-06-11
forum: Programming Talk
---

### Post by Mirge on 2009-06-11
I was also looking into somewhat cross-platform GUI libraries for use with C++, ran into lots of info regarding Qt 4, GTKmm, and FLTK... most were the usual "Linux vs Windows", "My dad can kick your dad's ***", etc junk that doesn't interest me... but one thing that I see consistently (mostly on these boards) is people recommending Python for developing GUI apps.

Why? If I were to take the time to learn Python (which I honestly have no interest in doing--YET), wouldn't each person I sent the program to need to install a Python interpreter to be able to run the program? Just wondering. Thanks.

---

### Post by Can+~ on 2009-06-11
> **Mirge said:**
> ... but one thing that I see consistently (mostly on these boards) is people recommending Python for developing GUI apps.

Most of those recommendations are to people who are developing C/C++ with a GUI. And seriously, 90% of the people that chose C/C++ for this kind of things are either lazy or don't know anything else and just sticked to C++ because "it's popular".

The thing about C and C++ is that both are fast languages, but it's tedious to write GUI apps on them. On the other hand, python has an easy syntax, garbage collector, lot of bindings, etc. But it runs slower than C/C++.

Then you have to think that your processor runs on the order of nanoseconds, meanwhile the average human user will fill a form in seconds/minutes. That's ages to the processor.

So, you save your time spent programming actual stuff rather than time lost handling your own memory for absolutely no gain, as your bottleneck is on user's speed.

> wouldn't each person I sent the program to need to install a Python interpreter to be able to run the program? Just wondering. Thanks.

If you're developing on linux, most linux distributions have Python, or you can add a .deb that will pull it from a repository if needed. On windows, they would have to install it, or use some of those alternatives like py2exe.

---

### Post by Mirge on 2009-06-11
That's helpful insight, and I am one of those people who plans on sticking with C++ to develop GUI apps, though it won't be anything public or too terribly serious. I just still have a hard time understanding why people constantly recommend Python for it. I understand that Python has grown tremendously in recent time, but the notion of having to install a Python interpreter just to run a program on Windows, ehh... just kinda turns me off.

I'm still quite curious about Python because of all of the hype, but I'm not sure I'll be able to get into it. From what I've seen (which is little, at most)... it kinda strikes me as odd. Then again, I've seen far weirder (is that a word? lol)..... I used to develop several scripts with Perl.

For now I guess I'm sticking with C++, and will investigate further into whether to use Qt, GTKmm or FLTK... /sigh.

---

### Post by Mickeysofine1972 on 2009-06-11
To be honest, C/C++ is still ok to do GUIs but being a C/C++ programmer as well as knowing enough Python to be dangerous, I see Python as the easy option to get the same job done with less effort.

Unless your doing a labour of love and want to make it with C/C++ as some form of art then your really making a mistake. Use a language that get the same results, and can still interface with your C/C++ if you need time critical stuff done.

Thats my 2p anyhow and while I'm at it if you really just like the C way of doing it then why not look at PHPGtk ?

Mike

---

### Post by Mirge on 2009-06-11
Well, the thing is, some applications I'll be developing are work-related, and will need to run on Windows and Linux... he's not going to install a Python interpreter just to run these programs. And other programs that I may develop, I want to expand upon my knowledge of C++... in addition to the above reasoning.

---

### Post by Can+~ on 2009-06-11
And how about using a web application? Could be used in any computer as long as it has a browser.

---

### Post by Mirge on 2009-06-11
Well, I build web applications for a living, but I'm really looking to expand my knowledge and experience with C++, and sometimes the programs will need access to files on the actual computer (making the person upload a file is a possibility, but I don't want to do that).

More than anything I was just curious about why Python is so highly recommended. Not putting it down or suggesting anybody to NOT use it. When time permits and my interest gets higher, I'm sure I'll be trying Python myself too.

---

### Post by soltanis on 2009-06-11
Python is 90% of the work for 10% of the effort. That's why people recommend it for GUI stuff.

---

### Post by Mirge on 2009-06-11
> **soltanis said:**
> Python is 90% of the work for 10% of the effort. That's why people recommend it for GUI stuff.

I can see that being very tempting, especially if on a Linux environment where Python is either already installed or easily installed. But it wouldn't really work for me.

---

### Post by lykwydchykyn on 2009-06-12
I'm using python and qt4 to develop a utility for work.  It would be a turn-off to have to install pyqt, python, and various python libraries to make it run on windows (and that doesn't just go for python, but also java, .NET, and the rest), but I've found a way around that using py2exe.

Yes, it does generate kind of a bloated mess of files, but it works; and these days, who cares if a program that could have been 1 MB is 10 MB?  It can be 100 MB for all it matters.  In this instance, what matters is that I get the program written quickly and that it's easy to update.

As the saying goes, processor time is cheaper than programmer time.  But that cuts both ways -- if you can crack something out using C or C++, why not?

If you're a hot dog with C++, I wouldn't try to sell you on Python arbitrarily.  But if you ask, I'd tell you it gets the job done for me and I'm happy with it.

---

### Post by Mirge on 2009-06-12
> **lykwydchykyn said:**
> I'm using python and qt4 to develop a utility for work.  It would be a turn-off to have to install pyqt, python, and various python libraries to make it run on windows (and that doesn't just go for python, but also java, .NET, and the rest), but I've found a way around that using py2exe.

Yes, it does generate kind of a bloated mess of files, but it works; and these days, who cares if a program that could have been 1 MB is 10 MB?  It can be 100 MB for all it matters.  In this instance, what matters is that I get the program written quickly and that it's easy to update.

As the saying goes, processor time is cheaper than programmer time.  But that cuts both ways -- if you can crack something out using C or C++, why not?

If you're a hot dog with C++, I wouldn't try to sell you on Python arbitrarily.  But if you ask, I'd tell you it gets the job done for me and I'm happy with it.

1MB, heck yeah.. 10MB, still fine by me! 100MB? Gonna pass lol... but I know what you mean. Hard drive space being so dirt cheap, 100MB isn't a big deal.. but if it was being distributed, that'd rack up bandwidth charges & take a while to download for slower connections. God bless 30Mbps cable... :)

And yeah, I can imagine developing a GUI in Python (assuming the programmer doing it has experience with Python) would be drastically faster than doing the same with C++.

I dunno.. I keep hearing about Python, which is fine... but it's almost to the point where it's like "Python > ALL"..... sort of like 99% of the people I know that own a Mac. They think Mac is GOD and that anybody who uses anything other than a Mac should burn haha.

I definitely want to TRY Python when I get some free time. Just kinda irks me when I read people saying stuff like "forget <insert any language but Python here>, use Python!!".

---

### Post by lykwydchykyn on 2009-06-12
> **Mirge said:**
> 
I definitely want to TRY Python when I get some free time. Just kinda irks me when I read people saying stuff like "forget <insert any language but Python here>, use Python!!".

Well, yeah, attitudes like that are irritating in any context (yes, even from Linux users).  

I mean, just like Linux newbies who discover the joys of free software after a lifetime of proprietary OS's get a little overbearing, those who have been finagling pointers and references all their life can be a bit obnoxious after finding they can do something in 10 lines of code that used to take 100.  

But you have to realize, on the flip side, that python coders are subjected to the "learn a real language" attitude from C/C++/Java coders.  So some folks are responding out of insecurity.

---

### Post by eilios on 2009-06-12
Python is preinstalled on a majority of distros, as well as Mac OS X, and as for Windows, py2exe will allow you to make standalone applications. Python is faster to write code with, and it's easier to bugfix in my opinion(the code is very readable).

---

### Post by Mirge on 2009-06-12
> **eilios said:**
> Python is preinstalled on a majority of distros, as well as Mac OS X, and as for Windows, py2exe will allow you to make standalone applications. Python is faster to write code with, and it's easier to bugfix in my opinion(the code is very readable).

Why isn't everybody developing with Python then? Word hasn't spread yet?

---

### Post by ibuclaw on 2009-06-12
> **Mirge said:**
> Why isn't everybody developing with Python then? Word hasn't spread yet?

Some HP OEMs use Python scripts as part of the process to reinstall Windows XP should things go wrong and you are required to boot from the recovery CDs/DVDs.

If I remember correctly, it is Python2.2 the name that I saw in Add/Remove Programs.

---

### Post by nvteighen on 2009-06-12
> **Mirge said:**
> Why isn't everybody developing with Python then? Word hasn't spread yet?
Er... people **are** developing in Python. Google, GNOME, Ubuntu and a lot of other projects you can take a look on Launchpad use it.

The issue is that Python in some issues targets to the same niche Perl targets to (e.g. web development, rapid general scripting, etc.). And inertia plays in favor of Perl, of course, being older, more established and also very solid... You just can't think on defeating Perl from one day to another, even when Python seems to have take some audience from it.

Another issue, which is common for all languages, is that Python can't be used for everything... If you want to code a system utility, chances are C or C++ is what you're looking for, for example.

---

### Post by lykwydchykyn on 2009-06-12
Now, if you're writing proprietary software, protecting your source code with an interpreted language is a little tricky.  Ok, it CAN be done, but...

---

### Post by Mirge on 2009-06-12
> **nvteighen said:**
> Er... people **are** developing in Python. Google, GNOME, Ubuntu and a lot of other projects you can take a look on Launchpad use it.

The issue is that Python in some issues targets to the same niche Perl targets to (e.g. web development, rapid general scripting, etc.). And inertia plays in favor of Perl, of course, being older, more established and also very solid... You just can't think on defeating Perl from one day to another, even when Python seems to have take some audience from it.

Another issue, which is common for all languages, is that Python can't be used for everything... If you want to code a system utility, chances are C or C++ is what you're looking for, for example.

Please, God, let Python take over Perl..... *shudder*.. I just don't like thinking about my years as a Perl/CGI developer haha.

Python definitely sounds cool. I'd love to try it. Might dabble with it a bit next weekend, gotta work this weekend :O.

---

### Post by Mirge on 2009-06-12
I don't know what I'm going to do if I don't have to enter semicolons to mark the end of a statement.. I'm so used to it lol.

---

### Post by benj1 on 2009-06-12
i started on python after coming from c++, basically i realised the most of the stuff wasn't speed critical, and wasn't overly low level. its realy nice only needing to write one statement, rather than 5 functions to do the same thing, it also stays nicely readable, and 9 times out of 10 if you think its possible to do something the way you want to do it, it probably is.
at the end of the day different languages are good for different things, you wouldn't want to program 3d games in python, you wouldn't try to do simple text processing in C.
my point is python is good for certain things, it just so happens that its good for a lot of certain things.

---

### Post by lykwydchykyn on 2009-06-12
> **Mirge said:**
> I don't know what I'm going to do if I don't have to enter semicolons to mark the end of a statement.. I'm so used to it lol.

Kind of like how I end up with stray ":wq"s in files I edited with something other than vim.

I have to bounce back and forth between PHP and Python a lot in my job, it always takes a day or two before I get all the builtin functions and syntax sorted.  At least the whitespace in my PHP ends up immaculate.

---

### Post by Mirge on 2009-06-12
> **lykwydchykyn said:**
> Kind of like how I end up with stray ":wq"s in files I edited with something other than vim.

I have to bounce back and forth between PHP and Python a lot in my job, it always takes a day or two before I get all the builtin functions and syntax sorted.  At least the whitespace in my PHP ends up immaculate.

Haha. Yeah, whitespace is my biggest pet peeve when it comes to programming.

---

