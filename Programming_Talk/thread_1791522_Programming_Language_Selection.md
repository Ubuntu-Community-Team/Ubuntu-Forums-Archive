---
title: "Programming Language Selection"
date: 2011-06-26
forum: Programming Talk
---

### Post by scott-ian on 2011-06-26
What programming language would be best for an open source program?  I was thinking C or C++, but I am willing to take other suggestions.

---

### Post by myrtle1908 on 2011-06-26
You should select the language best suited to the task, not the open source community.  Providing you don't pick a obscure language, and the project is interesting to others, you shouldn't have trouble finding help in the open source community.

---

### Post by scott-ian on 2011-06-26
C and C++ are similar enough that they would be good for the same tasks.  Which do most programmers use?

---

### Post by myrtle1908 on 2011-06-27
> **scott-ian said:**
> C and C++ are similar enough that they would be good for the same tasks.  Which do most programmers use?

It depends on the task :)  For example;

A text-munging/data-mining app you might choose Perl.
A enterprise wide web application you probably want Java or .NET.
A GUI app for linux you might go Python.
A GUI app for multiple operating systems you might go C++ or Java.

---

### Post by simeon87 on 2011-06-27
As myrtle1908 said, you have to describe what kind of program you want to write. If you were developing a program 15 years ago then C and C++ would have been decent choices. Now, there are various other languages that can make life easier and that do the job just as well, such as Java and Python.

---

### Post by Pierrick584 on 2011-06-27
Actualy, for a standard linux GUI app, TCL/TK is better, C++ with wxWidgets is quite easy too

When you just wana pickup a language and do various things with it, C++ is the best bet, harder to learn, but perform much better in everything (beside development speed, beacause its a litle more complex)

---

### Post by simeon87 on 2011-06-27
Performance is not everything. If it's a standard GUI app that does some average things then you probably won't need C++. Python will be fast enough and you can write the program a lot easier and faster. For many things, the user won't notice the difference anyway. Even so, you can always write the performance-critical parts in C and call them from Python, that's not very difficult.

---

### Post by cgroza on 2011-06-27
What are the target platforms for you application?
Many times, this is a decisive factor.

---

### Post by scott-ian on 2011-06-27
Only Linux.  I guess the best options for a GUI program would be Python and C++.  I don't know which I'll go with, because both would be good for the job, but I can figure that much out myself.  Thanks.

---

### Post by boast on 2011-06-27
> **scott-ian said:**
> Only Linux.  I guess the best options for a GUI program would be Python and C++.  I don't know which I'll go with, because both would be good for the job, but I can figure that much out myself.  Thanks.

for GUI programs, I think using Qt is the best ;) . And thats based on C++

---

### Post by cgroza on 2011-06-27
For GUI programs I suggest wxWidgets, fits in with Windows, GNOME, KDE and Mac.

I would go for Python or Ruby for desktop applications and C++ for more speed needy tasks.

---

### Post by Pierrick584 on 2011-06-27
you might want to look at wxSmith, plugin of Code::Block, it is definitively an awesome tool, and there is some great tutorials about it

---

### Post by JupiterV2 on 2011-06-27
> **boast said:**
> for GUI programs, I think using Qt is the best ;) . And thats based on C++

Qt is the best? The best for what? Is it the prettiest? Most versatile? Fastest? Portable? Wide-spread?

You need to decide your audience and language to start. How broad do you want your program to be used? Linux? Windows? Mac? I think you said Linux. Ok, so do you intend to have it available to low-end hardware? Dumb terminals? Do you want the GUI with the largest install base or the one with the most features? Does it matter if the library is native to your language of choice or will a language binding suite you just fine? Do you plan on implementing custom widgets? Is your application intended for experienced or inexperienced users? Are you targeting enterprise or desktop users?

Ambiguous questions with equally ambiguous answers...so irritating.

---

### Post by trizrK on 2011-06-27
I wouldn't use python for bulky programs. Just my preference

---

### Post by cgroza on 2011-06-28
> **trizrK said:**
> I wouldn't use python for bulky programs. Just my preference
Bulky programs on other language (Java or C++) go even more bulky.
Blender is a bulky program, it is written in Python...

---

### Post by mourt on 2011-06-30
> **JupiterV2 said:**
> Qt is the best? The best for what? Is it the prettiest? Most versatile? Fastest? Portable? Wide-spread?

You need to decide your audience and language to start. How broad do you want your program to be used? Linux? Windows? Mac? I think you said Linux. Ok, so do you intend to have it available to low-end hardware? Dumb terminals? Do you want the GUI with the largest install base or the one with the most features? Does it matter if the library is native to your language of choice or will a language binding suite you just fine? Do you plan on implementing custom widgets? Is your application intended for experienced or inexperienced users? Are you targeting enterprise or desktop users?

Ambiguous questions with equally ambiguous answers...so irritating.

More than half of your question seem already answered by the previous response ;-)

---

### Post by mourt on 2011-06-30
> **Pierrick584 said:**
> Actualy, for a standard linux GUI app, TCL/TK is better, C++ with wxWidgets is quite easy too ...

One dead, the other dying:

[http://www.google.com/trends?q=tcl%2Ftk%2C+wxwidgets&ctab=0&geo=all&date=all&sort=0](http://www.google.com/trends?q=tcl%2Ftk%2C+wxwidgets&ctab=0&geo=all&date=all&sort=0)

---

### Post by llanitedave on 2011-06-30
> **mourt said:**
> One dead, the other dying:

[http://www.google.com/trends?q=tcl%2Ftk%2C+wxwidgets&ctab=0&geo=all&date=all&sort=0](http://www.google.com/trends?q=tcl%2Ftk%2C+wxwidgets&ctab=0&geo=all&date=all&sort=0)

That's not convincing.  It's a "news reference" trend,not an installed base trend.  As each platform becomes more standard and more established, it becomes less newsworthy.

By your search, ALL the open source GUIs are dying:

**[COLOR="DeepSkyBlue"]tcl/tk[/COLOR]    [COLOR="Red"]wxwidgets[/COLOR]    [COLOR="DarkOrange"]qt4[/COLOR]    [COLOR="SeaGreen"]wxpython[/COLOR]    [COLOR="Blue"]pyqt[/COLOR]**
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=196470&stc=1&d=1309491135[/IMG]

---

