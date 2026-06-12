---
title: "Introduction to Programming 101"
date: 2008-01-25
forum: Programming Talk
---

### Post by rosegarden78 on 2008-01-25
Guys...I took Intro to Programming at community college.  I know difference between compiler, source code, etc.  Textbook was Programming for Dummies.  Anyway I want to make first Debian program.  Is there a good GUI-type development for Ubuntu (I barely know about .exe) or should I use the free basic code that generates .exe programs?  I just want something where I can layout windows and set buttons, code, menu.  Then it will automatically compile.  Thanks in advance. :KS

---

### Post by LaRoza on 2008-01-25
> **rosegarden78 said:**
> Guys...I took Intro to Programming at community college.  I know difference between compiler, source code, etc.  Textbook was Programming for Dummies.  Anyway I want to make first Debian program.  Is there a good GUI-type development for Ubuntu (I barely know about .exe) or should I use the free basic code that generates .exe programs?  I just want something where I can layout windows and set buttons, code, menu.  Then it will automatically compile.  Thanks in advance. :KS

See the stickies, "New to Programming in Linux" and "Suggestions for Beginners"

.exe refers to the Windows format for binary files.

Read the Learning to Program FAQs also.

---

### Post by Joeb454 on 2008-01-25
Also by the sounds of it you used Visual Studio, which uses a sort of "drag and drop" feature to place the buttons etc. in the window.

In reality, coding this yourself would take quite a while to learn

---

### Post by LaRoza on 2008-01-25
Yes, learning with VB is a perfect example of how NOT to learn.

VB is a good RAD tool, but isn't good for learning programming.

In fact, I'd be inclined to say that VB is a tool only for advanced programmers, otherwise it is a bad crutch.

---

### Post by BertP on 2008-01-25
I am kind of in the same boat,  I am a complete newbie to Unbuntu and Linux but am interested in what development environments are available for various languages.

I did some C++ programs more than 5 years ago on Windows but my task at the moment is to alter a java script program to that generates DNA charts.  So my second question is: Is there some IDE available to Ubuntu with perhaps a debugger that I can use to step through the Java script code?

-----
more info:

The java script that I want to alter generates web pages with DNA charts.  This piece of java script is quite complex. 

 If anyone wants to see it in action, just go to [http://www.mymcgee.com/tools/yutility.html](http://www.mymcgee.com/tools/yutility.html)
Just scroll down below the check boxes then press the "Sample Data" then "Execute".  I'm in a similar group to Mr McGee and I would like to make a few customizations to the charts the utility produces.

The reason I don't want to customize the html  output instead, is because we will adding new DNA data often,  and I don't want to make dozens of  html changes by hand every time the data is updated.  

Thanks in advance!

---

### Post by LaRoza on 2008-01-25
Try Firebug for Firefox.

Although I am an Opera user, I use Firefox for the development and testing of pages.

[https://addons.mozilla.org/en-US/firefox/addon/1843](https://addons.mozilla.org/en-US/firefox/addon/1843)

---

### Post by BertP on 2008-01-25
Thanks!  this looks exactly like what I need!  \\:D/

---

### Post by LaRoza on 2008-01-25
> **BertP said:**
> Thanks!  this looks exactly like what I need!  \\:D/

[https://addons.mozilla.org/en-US/firefox/addon/60](https://addons.mozilla.org/en-US/firefox/addon/60)

Also useful.

---

### Post by rosegarden78 on 2008-01-25
> **Joeb454 said:**
> Also by the sounds of it you used Visual Studio, which uses a sort of "drag and drop" feature to place the buttons etc. in the window.

No it was freeware or shareware BASIC with GUI (what was the name) created .exe with libraries.  You are supposed to pay the author to activate gold features ... It came with the book or I downloaded from Tucows or something like that.  Why not make .exe prototypes if easier and cross-platform with a GUI development tool?  Thanks, LaRoza, for those suggestions I'll have to learn about Linux now.

---

### Post by LaRoza on 2008-01-25
If you use an interpreted language, you don't have to worry about compiling.

Python, Ruby, Perl, and Tcl scripts work without alteration on Windows, Macs, and Linux.

I suggest Python, my wiki has a lot on it.

---

### Post by clasificado on 2008-01-26
I have to second LaRoza,

Python + QT is a good team to start.

also, QT designer lets you to design graphically your window (with buttons, etc)

Dont worry about so many options. Just pick one and start programming.

clasificado.

---

### Post by rosegarden78 on 2008-01-26
Thanks guys I found the Qt Designer in kde-devel.  Looks like having Gnome, Xfce and Kde combined was a good iead after all.

---

### Post by rosegarden78 on 2008-01-26
Seems though if WINE uses .exe programs that use file access, and if that freeware is the only thing I can use, then start programming right away.  But then again maybe better to build it the right way to start with Python.  I like the idea of a stand-alone binary with libraries though not that compatibility isn't a problem anymore.  I'll check back when KDE and Qt Designer are done installing and let you know what I think.

EDIT: I found [this]("http://women.kde.org/articles/tutorials/kdevelop3/introduction.html") article how to make your first program with Qt Designer and KDevelop.

---

### Post by Majorix on 2008-01-26
I hardly understand anything from the OP. Can someone translate it for me?

---

### Post by LaRoza on 2008-01-26
> **Majorix said:**
> I hardly understand anything from the OP. Can someone translate it for me?
> 
Guys...I took Intro to Programming at community college. I know difference between compiler, source code, etc. Textbook was Programming for Dummies. Anyway I want to make first Debian program. Is there a good GUI-type development for Ubuntu (I barely know about .exe) or should I use the free basic code that generates .exe programs? I just want something where I can layout windows and set buttons, code, menu. Then it will automatically compile. Thanks in advance.

I took the class Intro to Programming, we used a compiled language based on BASIC. I want to learn how to program in Linux. I want a language with a good IDE that makes GUI's easier to make.

---

### Post by CptPicard on 2008-01-26
"... and I really need to be disabused of the notion that it's a good idea to produce Windows executable binaries on Linux, for running on Linux, using some Windows-specific tool."

---

### Post by LaRoza on 2008-01-26
> **CptPicard said:**
> "... and I really need to be disabused of the notion that it's a good idea to produce Windows executable binaries on Linux, for running on Linux, using some Windows-specific tool."

That was done I think.

I recommend Python (or another equally cross platform interpreted language with a good library) for the OP.

---

### Post by Majorix on 2008-01-26
> **LaRoza said:**
> I took the class Intro to Programming, we used a compiled language based on BASIC. I want to learn how to program in Linux. I want a language with a good IDE that makes GUI's easier to make.

Thanks LaRoza. I don't want to sound rude or anything, but the topic starter has some little problems explaining himself/herself :)

---

### Post by LaRoza on 2008-01-26
> **Majorix said:**
> Thanks LaRoza. I don't want to sound rude or anything, but the topic starter has some little problems explaining himself/herself :)

Yes, but we got through it. :)

(Plus, I coud tell the situation from the title almost)

---

### Post by CptPicard on 2008-01-26
Sometimes, admittedly, some of the opened threads here remind me of the [famous quote by Wolfgang Pauli]("http://en.wikipedia.org/wiki/Not_even_wrong"), and I get the feeling it's getting more and more common every day. Not to be taken as a slight at OP, he was actually coherent enough for the point to come across. :)

---

### Post by LaRoza on 2008-01-26
> **CptPicard said:**
> Sometimes, admittedly, some of the opened threads here remind me of the [famous quote by Wolfgang Pauli]("http://en.wikipedia.org/wiki/Not_even_wrong"), and I get the feeling it's getting more and more common every day. Not to be taken as a slight at OP, he was actually coherent enough for the point to come across. :)

As the French say "Such is life"

---

### Post by cprofitt on 2008-01-26
> **LaRoza said:**
> Yes, learning with VB is a perfect example of how NOT to learn.

VB is a good RAD tool, but isn't good for learning programming.

In fact, I'd be inclined to say that VB is a tool only for advanced programmers, otherwise it is a bad crutch.

I would think VB is a language and you are really labeliing Visual Studio as a tool for advanced programmers or a bad crutch for beginners; right?

---

### Post by LaRoza on 2008-01-26
> **PrivateVoid said:**
> I would think VB is a language and you are really labeliing Visual Studio as a tool for advanced programmers or a bad crutch for beginners; right?

Yes. 

The language is not good either, like almost all BASIC derivatives.

---

### Post by Majorix on 2008-01-26
Since the thread has already gone off-topic, I won't try to rescue it, but add to the current discussion.

VB stands for Visual Basic. It has a terrible syntax that is actually really hard to get used to for beginners. But for unknown reasons, beginners all around the world choose this language for their casual programming needs. Even we at the university for a software engineering course have to learn VB6.0 (there have been countless releases after that, but we still use this one, and believe me; most others do too, for some unknown reason again).

I really wish I was joking but I am not.

---

### Post by LaRoza on 2008-01-26
> **Majorix said:**
> Since the thread has already gone off-topic, I won't try to rescue it, but add to the current discussion.

VB stands for Visual Basic. It has a terrible syntax that is actually really hard to get used to for beginners. But for unknown reasons, beginners all around the world choose this language for their casual programming needs. Even we at the university for a software engineering course have to learn VB6.0 (there have been countless releases after that, but we still use this one, and believe me; most others do too, for some unknown reason again).

I really wish I was joking but I am not.

I will add some more...

BASIC [http://en.wikipedia.org/wiki/BASIC_programming_language](http://en.wikipedia.org/wiki/BASIC_programming_language) is really quite useless. Although it is a programming language, it isn't a good choice for a language, even in its day.

Visual Basic and Visual Basic for Applications and VBScript are used by Windows, and are useful in some areas. VB and VS are good for RAD, VBA is used for MS Office, and VBScript is good for administration of Windows systems and networks.

This doesn't mean you should use them though, Python has .NET bindings now (IronPython) and can do many Windows specific tasks. Python (and other languages) are good for RAD as well, and are cross platform.

VB is typically used in introductory programming courses, which I think is a bad move. There are BASIC dialects for Linux, if one where interested in them.

---

### Post by pmasiar on 2008-01-27
> **CptPicard said:**
> some of the opened threads here remind me of the [famous quote by Wolfgang Pauli]("http://en.wikipedia.org/wiki/Not_even_wrong"), and I get the feeling it's getting more and more common every day. Not to be taken as a slight at OP, he was actually coherent enough for the point to come across. :)

Excellent quote, thanks for that. 

At least OP mentioned his assumptions, so we can point them out, so it is not all lost yet.

---

### Post by pmasiar on 2008-01-27
Let's try to drag this thread back to topic, shall we? :-)
> **rosegarden78 said:**
> Anyway I want to make first Debian program.  Is there a good GUI-type development for Ubuntu (I barely know about .exe) or should I use the free basic code that generates .exe programs?  I just want something where I can layout windows and set buttons, code, menu.  Then it will automatically compile.  Thanks in advance. :KS

In Debian (and Ubuntu), BASIC is not widely used (and for good reasons, as previous poster mentioned). It is not even very good beginner's language, and it was just random artifact that it was so widely used. I guess interpreter was simple enough to implement (it was one of the first Bill Gates' programs for sale on PCs), and it snowballed from there.

Unix has different philosophy than MSDOS/Windows has (it is also older and more mature), and Python is substantially younger language, more modern and more advanced than BASIC.

But my advice will be not bother with GUI at the beginning, learn programming, design, data structures, algorithms, and learn how to solve useful problems first. If you need GUI badly, EasyGUI looks like a GUI without all the events and other complications. Python compiles code for you "behind the scenes", don't worry about it. It "just works" (tm).

Python is widely considered as best choice for beginners, see wiki in my sig for links to tutorials and training tasks. Later you may want to learn other languages (C, C++, C#, Java, Lisp etc) but trust me, start with Python.

---

### Post by rosegarden78 on 2008-01-27
Ok I see thread is starting the program I used was _Liberty BASIC_.  The class was _Intro to Programming_ and the textbook _Computer Programming for Dummies_.  Yesterday was the vodka talking anyway Qt Designer looks promising other than OP rest should be clear next time I use more articles better grammar.  Thanks again, guys for your help, I'll keep you informed of my progress.

---

### Post by rosegarden78 on 2008-01-27
> **pmasiar said:**
> Let's try to drag this thread back to topic, shall we? :-)

...

But my advice will be not bother with GUI at the beginning, learn programming, design, data structures, algorithms, and learn how to solve useful problems first. If you need GUI badly, EasyGUI looks like a GUI without all the events and other complications. Python compiles code for you "behind the scenes", don't worry about it. It "just works" (tm).

Python is widely considered as best choice for beginners, see wiki in my sig for links to tutorials and training tasks. Later you may want to learn other languages (C, C++, C#, Java, Lisp etc) but trust me, start with Python.

You're right about the algorithms, I had trouble at first understanding the recursive functions calls of QuickSort.  The other sort algorithms made sense.  Like Grey's Anatomy for doctors, I should learn the anatomical names for my computer's innards, as well as the ports pipes and processes.  But I think I'll take it easy to start.  All I hear about from Google and the forums is Python.

---

