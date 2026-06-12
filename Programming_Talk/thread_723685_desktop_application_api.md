---
title: "desktop application api"
date: 2008-03-13
forum: Programming Talk
---

### Post by virtualcoder on 2008-03-13
I am looking for an api, in c++ or java (or even C), that I can use to make a free and flexible time management/task management software
for an everyday user. The OSes I am aiming for are windows (vista and XP) and Ubuntu (and as many other linuxes as possible).
Also if Mac would be supported would be nice but not necessary (I have one at home).

So I'm planning on learning a new api, but not sure which. And I will hopefully be able to start and complete this software in this summer (when I'm free of university).

Although I will be myself using it on Windows, since I havent yet been able to get the sound working on my ubuntu, I will ofcourse test it on ubuntu to make sure it works.

My previous experience is with xcode (mac api).
A little bit with wxwidgets, sdl, opengl.

Please discuss the advantages of your choice of api over others so that I may finally decide which one to choose.

---

### Post by slavik on 2008-03-13
the widget APIs are as follows

GNOME = GTK, KDE = QT
Windows = whatever they call it
OSX = Cocoa

I would suggest either WxWidgets or GTK

---

### Post by Fbot1 on 2008-03-13
I personally think Qt is the most portable and the easiest to use. 
> **slavik said:**
> Windows = whatever they call it
Win32

---

### Post by nanotube on 2008-03-14
> **Fbot1 said:**
> I personally think Qt is the most portable and the easiest to use. 


i don't know whether qt is "the most" portable - in what way is it more portable than gtk or wxwidgets? they are all portable. 
but indeed, i have heard (though i never used qt myself) that it is the "easiest" to work with.

---

### Post by LaRoza on 2008-03-14
The most portable is probably Tk, as it is the default GUI toolkit for Python and other languages. (Ruby and Perl have it, as well as Tcl of course)

Of course, it isn't the prettiest, but it has some neat features that other toolkits don't have.

---

### Post by dempl_dempl on 2008-03-14
For C++ ,  most commonly used are Qt, wxWidgets and FLTK as cross platform.  FLTK and   wxWidgets are native , i.e. they use Windows "native" controls on Windows ,  and GTK+ on  Unix-family .  They are also portable on Mac, but I haven't tried it yet.

Qt isn't "native"  on Windows, as I can recall, but it can really look like it is :-)  .

In Java , folks use Swing .


I would suggest Qt/Kdevelop for   C++ apps , and Eclipse/ RCP for Java.
The real flexibility of those two frameworks comes when application needs to get translated to another language.  If you won't gonna need translation, just pick any  framework, by throwing dice :-)

---

### Post by pmasiar on 2008-03-14
> **virtualcoder said:**
> make a free and flexible time management/task management software for an everyday user. 

I do not see why you restrict yourself to Java and C++. Python would be more appropriate - you don't need the processing speed, but flexibility. Do whatever you want of course, your project, your free time. :-) 

I would suggest finding any existing project in this area and join it - there are plenty and will not be easy to build userbase for your new project, while competing with already established ones. later, when you know what are you doing and what "they" do wrong, you can start new one - but first, you learn what works and how, on existing working code.

---

### Post by virtualcoder on 2008-03-15
Oh sorry, I made an embarrassing typo,
My experience is with Carbon (for mac), not xcode, lol.
That involves all C programming, I have no clue about objective-c
apart from the fact that its object oriented, something like c++.

Also in case of scripting for application help tools, I know basics of perl so in case of scripting, I should be good to go.

---

### Post by LaRoza on 2008-03-15
> **virtualcoder said:**
> Oh sorry, I made an embarrassing typo,
My experience is with Carbon (for mac), not xcode, lol.
That involves all C programming, I have no clue about objective-c
apart from the fact that its object oriented, something like c++.

Also in case of scripting for application help tools, I know basics of perl so in case of scripting, I should be good to go.

Objective C is not like C++. Objective-C is a super set of C. (C + Smalltalk like objects)

You can use many GUI toolkits, see my wiki for references. (C + Perl is a good combination, if messy :))

---

### Post by virtualcoder on 2008-03-15
Thank you everyone for giving me a boosted headstart.

> **pmasiar said:**
> I do not see why you restrict yourself to Java and C++. Python would be more appropriate - you don't need the processing speed, but flexibility. Do whatever you want of course, your project, your free time. :-) 

I would suggest finding any existing project in this area and join it - there are plenty and will not be easy to build userbase for your new project, while competing with already established ones. later, when you know what are you doing and what "they" do wrong, you can start new one - but first, you learn what works and how, on existing working code.

I agree with you, except that I really wanted to make something of my own. But I should follow the wise choice of atleast seeing what else is out there before I make something of my own.

I wanted to do the application in an object oriented language, and having experience with c++, and dealing its headaches with memory management, and synchronization issues, I'm considering my newly developed java skills as well.

But I should mention that I am best with c++ and java, and I am confident in my skills in these two languages, so all choices I make will depend upon my strength around that api.

As much as python is concerned, I don't know much about it (only know that it is somewhat of a scripting language similar to perl). It might as well take me that much time to learn python that I want to invest making the application itself.

Also, I've tested wxwidgets with mac before, OSX 10.39, and it works fine.
wxWidgets was my entry door to the world of gui apis and hence I wasnt able to go completely deep into it, and completely shifted to Carbon. Ahh, the memories of wxwidgets :).

I ofcourse cant go for win32, since that would mean I'm restricting my application to windows.
I have heard mostly about gtk+ (gtkmm, java-gnome is not available from windows) and qt (but still dont know much about them), so if I am going to learn a new API, its probably going to be one of them.
I have read about qt that its license is more restricted than that of gtk+, please can someone clearify this, thanks!

Due to my lack of knowledge, I dont know much about what the java libraries offer (just know the language itself), so there might be something in store for me there.

Since I'm jumping into this application project head-first (not knowing what exactly I'm going to deal with),
for example like if it involves a database language, which I dont know about yet, but I do know that due to my personal incompetency of task management, I feel I know the needs of what a person would truely want in such an application, and I believe that is what really matters in terms of what a project should actually have.

From my personal perspective, a project should be driven by uniqueness, user-friendliness, usefulness, and very importantly creativity. Please correct me if I am wrong.

Assessing the different alternatives, it seems that I should refresh my wxwidgets knowledge to reduce my spent time, unless someone can clearify any advantages of gtk+ and qt over wxwidgets.
Personally, I found wxwidgets to be a little slow (quite slow when compared to carbon, but thats because carbon is native to mac).

I wont close any options, so need to a bit more research before I pick my api and language.
I am definitely looking towards the long-term, since this is not the only project I want to do.
Audio is important to me.

This is a side story and hopefully should not affect my decision but I should mention that the other half of my interest lies in game development. Probably I will use sdl (for 2d) and opengl (for 3d) for that but having a gui api such as gtk or something as an alternative would be nice. As game applications require speed and efficiency, java seems to be out of the picture.
I made a very simple arkanoid based game in wxwidgets, and it was really really slow, for a simple ball moving across the screen and hitting non-animating blocks. But my programming knowledge was much narrowed then so I might have used the wrong part of wxwidgets to implement that; meaning that it might have been my fault that the wxwidget application was so slow.


I apologize to all viewers for this very long and tiring post, even my hands are tired :) .
I give a big thanks to all viewers in advance who can find my questions in this long post !

---

### Post by LaRoza on 2008-03-15
Use wxWidgets if you like it and are familiar with it. It is cross platform and available for many languages.

It would probably be best to use Swing with Java.

---

### Post by mssever on 2008-03-15
wxWidgets is a good choice for a GUI toolkit. And there's a good chance that you'll more than make up the time you spend learning Python. It isn't hard, and it requires a lot less code than C++ or Java. I'm a bit biased against Perl, but you might even be better off there than C++ or Java. Work at the hghest level that will allow you to accomplish your task.

---

### Post by pmasiar on 2008-03-15
If you know programming, learning Python syntax will take you one weekend. It is all very obvious. Rest are libraries, which you confessed you don't know that well - and Python libraries, because of dynamic typing, are known to be order of magnitude simpler than Java. :-)

Python is dynamically typed like Perl - but, unlike Perl, is strongly typed (no behind-your-back string to number and back conversions), and has exceptions - but not the static kind like Java does. Many people (including me) feel like ython is order of magnitude more productive, compared to Java or C++.

I understand you want to have something of your own - but for a beginner, it might have god-awfull design, and for you and you alone will be making very slow slug towards something releasable. Compare it to joining existing project, where you can learn from existing working design (most likely not the first draft version), you can add code and see it released and tested by others. When you understand project deep enough, and will feel like you want to move it in different, better direction, you can fork - and maybe part of users and developers will like your idea more than the main trunk. Or not, but then you still have trunk of original (and running) code, where you just need add your own features.

---

### Post by virtualcoder on 2008-03-15
Well I guess I am a beginner, not having any experience with a complicated gui application like this one.

[QUOTE=pmasiar]
I understand you want to have something of your own - but for a beginner, it might have god-awfull design, and for you and you alone will be making very slow slug towards something releasable. Compare it to joining existing project, where you can learn from existing working design (most likely not the first draft version), you can add code and see it released and tested by others. When you understand project deep enough, and will feel like you want to move it in different, better direction, you can fork - and maybe part of users and developers will like your idea more than the main trunk. Or not, but then you still have trunk of original (and running) code, where you just need add your own features.[/QUOTE]

I seem to undestand that joining another project is the best option, but since I have not done that before, I kinda of feel nervous about it :). Now thats definitely a priority for me to find out if I can join any of the existing projects.
Is there any place other than sourceforge where one can join existing projects??

I am surprised by the amount of support I see for python in these posts, and they seem very convincing too.
I will be taking a programming languages course in the summer, and one of the languages taught might be Python, so that will be a benefit. I will learn it either way.

I remember how easy it is to do anything in perl (that was the last language I learned), and completing tasks in perl were shocking when compared to doing the same in c++. From that experience, I can imagine comparing the use of something like perl and use of c++ to do this project, lol.

Does python have the same kind of library support as perl does, perl's library support really impressed me, you can do almost anything by calling just one function or a very few functions and you do not have to worry about anything (strings, freeing memory, pointers, malloc, buffer overflows, a whole lot of detailed stuff).

Considering if I go for python, which would be better: wxPython, PyGTK, or PyQt.
For ease I am considering simple interface, larger library (like a native library always allows you to do more things than a cross-platform library), other things my brain can't think of right now because I have a test on monday :).

Too many choices just makes life more complicated.

[QUOTE=mssever]
Work at the hghest level that will allow you to accomplish your task.
[/QUOTE]

I like your way of thinking, working towards the goal, thanks for helping me focus.

[QUOTE=LaRoza]Use wxWidgets if you like it and are familiar with it. It is cross platform and available for many languages.[/QUOTE]

If I am going to join an existing project, then I will have free time on my hand to be able to do some other stuff as well. Maybe I will revise wxwidgets in that time.

---

### Post by LaRoza on 2008-03-15
> **virtualcoder said:**
> 
Does python have the same kind of library support as perl does, perl's library support really impressed me, you can do almost anything by calling just one function or a very few functions and you do not have to worry about anything (strings, freeing memory, pointers, malloc, buffer overflows, a whole lot of detailed stuff).

Considering if I go for python, which would be better: wxPython, PyGTK, or PyQt.
For ease I am considering simple interface, larger library (like a native library always allows you to do more things than a cross-platform library), other things my brain can't think of right now because I have a test on monday :).


Python seems to have a standard module for everything. [http://docs.python.org/lib/lib.html](http://docs.python.org/lib/lib.html)

(You can do a lot with standard Python, unlike C++...)

I would use wxPython, as that works well and is meant to be cross platform (easy to install for Windows users, just use the installer, and ActivePython)

---

