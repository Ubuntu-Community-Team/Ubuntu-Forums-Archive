---
title: "Pros and Cons between Python, C++, VALA, C#"
date: 2009-04-26
forum: Recurring Discussions
---

### Post by Lightbreeze on 2009-04-26
I'm looking for clear pros and cons between developing an application in Python, C++, VALA and C#. And to what areas each is suited. Thank you.

---

### Post by dwhitney67 on 2009-04-26
It would be helpful to know why you are looking for this feedback.  Are you searching for a job, or perhaps looking into becoming a programming hobbyist?  Maybe you are doing research for an entry level CompSci course, or just conducting a poll to determine which Ubuntu members will bite at your thread?

Frankly there are many reasons to choose one language over another.  If you would provide specific details of your level of programming competency, that of your team members (if any), and what your target system will be and what task you are attempting to accomplish, then perhaps you can obtain some feedback that is useful.

Otherwise, without the details, you are wasting everybody's time, because invariably, everyone will have a personal opinion that may or may not be suitable for what you are attempting to accomplish.

---

### Post by Lightbreeze on 2009-04-26
Thank you. I'm interested as a hobbyist. I have a few projects I'd like to do, and I'd like to contribute patches to the community as a part of my learning experience.
 So I'd like to learn a language to a level where I can actually contribute. I am about to start learning c because I think it is worth understanding that language, and I'd like to focus on an OO language also.. but there are so many options - ruby, python, c#, vala, c++... :confused:
 But I am actually inclined towards vala so I am going to narrow down my original question:P and ask whether applications written in vala can be compiled for other platforms?

---

### Post by dwhitney67 on 2009-04-26
Ok, well personally I have never heard of VALA.  I suppose I could educate myself with a Google-search, but I have no interest at this time.

Supposedly Python is an easy language for beginners.  C on the other hand, does have its nuances that make it challenging to grasp some of the concepts, especially if you are teaching yourself.  Ditto for C++.

However, for each of the languages, there is a wide support base to help you along the way should you encounter a road block.

Many apps in Linux are developed using Python; low level apps (libraries, kernel, etc) are generally done in C.  Python, if I understand correctly, is a wrapper-language around C.

C++ is used for gaming and other industries (ie. government/military/aerospace) because it can be programmed to interface directly with the "metal" (just like C), but at the same time offers the OO benefits.

Anyhow, I suggest you start with some simple like Python.  Concurrently, you can study K&R's C book for good examples, and compare the ease of one language versus the other.

---

### Post by nvteighen on 2009-04-26
> **dwhitney67 said:**
> Ok, well personally I have never heard of VALA.  I suppose I could educate myself with a Google-search, but I have no interest at this time.


Vala is a GObject preprocessor for C... It's nothing more than that.

---

### Post by Can+~ on 2009-04-26
Alternative title for this thread:

Pros and Cons between Apples, Oranges, Pineapples and Watermelons.

More than learning languages, what you should do is learn paradigms.

Python covers OO, functional and a bit imperative, it's a great learning experience. C and C++ can be painful to learn without any previous knowledge, due to the low level abstraction it uses, and very prone to errors when you don't know what you're doing.

---

### Post by juanp.contreras on 2009-04-26
Let me give you this an advice:

First: Before anything you have to know which problem are you trying to solve... solution has to be fast? solution has to be easily readable? solution needs graphics?, what kind of problem am I solving?... you have to know about the problem... that is 50% of any programming problem

Second: Choose a language suitable to the problem. ASM is generally used to optimize time and space, C is for "near bare-metal" and system programming, C++ has software design facilities but is closely related to C and system programming, Java is Object Oriented but slow since it runs on a virtual machine...

---

### Post by bapoumba on 2009-04-26
Welcome to the Recurring Discussions.

---

### Post by dwhitney67 on 2009-04-26
> **bapoumba said:**
> Welcome to the Recurring Discussions.
Yep, this is when it is time to unsubscribe from receiving update notices.

---

### Post by bapoumba on 2009-04-26
> **dwhitney67 said:**
> Yep, this is when it is time to unsubscribe from receiving update notices.
I should post in "Are you a thread killer?" :D

---

### Post by Kilon on 2009-04-27
> **bapoumba said:**
> I should post in "Are you a thread killer?" :D

Well moving it here is an effective way of killing it.

---

### Post by bapoumba on 2009-04-27
> **Kilon said:**
> Well moving it here is an effective way of killing it.
Why ? The discussion is still open, in an appropriate place as it has been rehearsed so many times.. Some threads here have been up for a long time.

---

### Post by Kilon on 2009-04-27
> **bapoumba said:**
> Why ? The discussion is still open, in an appropriate place as it has been rehearsed so many times.. Some threads here have been up for a long time.

Agreed..... 

but it has the feeling of a punishment area.

---

### Post by bapoumba on 2009-04-27
> **Kilon said:**
> Agreed..... 

but it has the feeling of a punishment area.
You could see it another way: keep these discussions out of the regular help areas. This is what we set it up for. Some sub-forums were cluttered with dead horses (some of us even suggested we name the forum that way, but it would not have been much .. professional :D). Matthew's list in the sticky has been improved over time. I think it works pretty well, I see no need to have people fight over. With such an active forum, you will always find someone willing to argue :)

---

### Post by kumoshk on 2009-10-08
> **Lightbreeze said:**
> I'm looking for clear pros and cons between developing an application in Python, C++, VALA and C#. And to what areas each is suited. Thank you.

I've done a fair amount of coding with Python.
I have a little experience with C++.
I know a little about C#.
And, I just started learning about Vala.

Out of your options, I would most strongly encourage you to use Vala. It's pretty much as easy to program in as Python, but you get fast, small and native executables (since it translates everything to C before compiling). C++ is cool, but you have to deal with a lot more, and string functionality is impaired. Handling strings in Vala is about as easy as Python (which is saying a lot, for a compiled language). I mean, you get methods like up, down, strip and split out of the box&#8212;up and down are for making the strings uppercase and lowercase. Plus, string is actually a type&#8212;you don't have to do everything with the char type manually.

After only a small while of examining Vala code, I can already tell I like it more than most languages. If you do have problems coding something in it you can always convert it to C code and do it in C&#8212;or, you can embed Lua and use it to compensate (if for some reason you need to).

Python is a really cool language, and although it's not at all the slowest of the scripting languages, it's not nearly as fast as C (and consequently Vala).

C# seems kind of cool, but it's kind of weird, too, and from what I understand you need some sort of framework in order to use it, such as .NET or Mono (which, in my book, is a major downside&#8212;although some people might consider that an upside).

Here are some more things I like about Vala:
&#8226; You don't need to worry about header files
&#8226; Writing GUIs in it is really easy (probably easier than with WxPython, and since the code is native you don't need to bundle or require the GUI libraries /and/ the interpreter)
&#8226; It actually has a switch statement that works with both numbers and strings (don't know if it does ranges)
&#8226; You can both explicitly declare types, and have them determined by the type you assign (i.e. int x; x=1; or var x = 1)
&#8226; It allows for object-oriented programming
&#8226; Development on it seems to be going on strongly
&#8226; The libraries it supports are useful ones (even though it may not support just about 'everything' yet)
&#8226; The documentation, although it's not extensive yet, is actually comprehensible and works quite well (although the version you get with Ubuntu is old and the connect method doesn't work on it; so use += instead).
&#8226; You can have constants, public/private variables, etc.

I would definitely recommend Vala to beginning programmers who want lots of power. Python's a cool language for that, too, though, but in different ways. Lua is cool, although I'd recommend it for the intermediate since the documentation might be harder to understand for a beginner. I'd recommend studying C++ for a beginner in order to understand certain concepts (but I wouldn't recommend trying to make everything with it all at once). Personally, I don't recommend worrying about C# if you're not planning to work for a company that uses it&#8212;but others may have differing opinions.

I'd recommend learning about C while you learn Vala, seeing as it should be useful (seeing as you can turn your Vala code into C code).

There are a few cons for Vala, though (or at least the version that comes with Jaunty Jackalope):
&#8226; Error messages don't seem to mention which line the errors occur on (although they do give numbers, but I don't know what they're for)
&#8226; It doesn't have cross-platform scripts or bytecode. I wouldn't worry too much about this since you can just get it on the other platforms and compile for them. I think the code itself shouldn't need modification very often, if at all.
&#8226; You still have to specify packages on the command-line instead of /just/ in the program code, unlike with Python and most scripting languages. This sort of thing can throw beginners for a loop if they don't know or don't know how. Fortunately, it's pretty painless with Vala if you know how.

Nevertheless, there's still a ton about Vala I don't know. I hope it has Python-like support for metamethods. I hope exception handling is at least as good as Python's (hopefully better&#8212;especially with making your own) (espeically the error messages that occur, such that you don't need to look up the exception names elsewhere). It would be nice if functions could be objects, and treated as objects during declaration (that's a nice thing about Lua; you can make a function a member of a table while declaring it and by these means object-oriented programming is possible and practical in Lua). I know you can do associative arrays in Vala, but I hope you don't have to use third-party stuff for them.

---

### Post by LepeKaname on 2011-12-28
I'm learning VALA as well. I have to say that its pretty cool!
My experience is mainly in Java. I love Java but Vala looks a lot more logical and powerful to me (while C++ is more like a headache). 

It is a pretty new language so if the community likes it, we can expect very interesting things happening. For now, there are no solid IDE solutions but many very promising. 

I wish to see Vala integrated with QT (as it is mainly for GTK), but I guess it is just matter of time. Vala was exactly what I was looking for: a neat programming language with native compilation (through C), no VM as  Java or C#.

+1 for VALA!

BTW, **kumoshk** explanation about Vala is great!

---

### Post by directhex on 2011-12-28
This is a dead thread. Also, Vala for Qt seems unlikely when it's tightly bound to GObject (GTK+'s C-based object library, pretty much the opposite of Qt)

---

### Post by kumoshk on 2012-01-04
> **directhex said:**
> This is a dead thread.
I'm still listening. :)

> **LepeKaname said:**
> BTW, **kumoshk** explanation about Vala is great!
Thanks. :) After a good while of using it and making some programs, I still like Vala a lot, although I like Python (2.x) more for cross-platform solutions and things that require way too much text parsing (like my text adventure model). I'm still trying to get the Windows compiler to get my Vala e-book reader to work properly, though. There must be some difference in the way things are supposed to be coded&#8212;but it probably wouldn't have come up if my program were simpler.

Also, don't forget Genie. It's pretty much the same thing as Vala (uses the same compiler) but you use a different syntax (more like Python's). I think Genie is actually becoming more popular these days, but I'm partial to Vala for some odd reason.

Am I really still using Karmic Koala? I think so &#8230; That's what happens when you move and have to use dial-up.

---

### Post by LepeKaname on 2012-02-13
I have been learning so much about Vala recently. As I come from Java, the syntax seems more natural to me... That is one of the reasons I didn't completely got into Python (which BTW, I agree its a great language!).

I haven't tried to compile for Windows but I will need to learn that later... 

Cheers.

---

### Post by ssokolow on 2012-02-26
> **directhex said:**
> This is a dead thread. Also, Vala for Qt seems unlikely when it's tightly bound to GObject (GTK+'s C-based object library, pretty much the opposite of Qt)

Not necessarily. Vala does have somewhat experimental support for a GObject-free "no objects" mode.

If they have done that, it's always possible someone will do the abstraction necessary to write a C++ mode.

---

### Post by juancarlospaco on 2012-02-27
You can compile Python to C Binary if you want to     ...just saying

---

### Post by ssokolow on 2012-02-27
> **juancarlospaco said:**
> You can compile Python to C Binary if you want to     ...just saying

No, you can compile restricted subsets of Python to C. (See RPython and ShedSkin)

Pyrex and Cython don't even do that much unless you provide explicit type annotations.

The only thing you can do with the full Python language is use tools like freeze, cx_freeze, and py2exe to zip up your .pyc bytecode files and concatenate them onto the end of the Python runtime's binary.

---

### Post by directhex on 2012-02-28
> **ssokolow said:**
> The only thing you can do with the full Python language is use tools like freeze, cx_freeze, and py2exe to zip up your .pyc bytecode files and concatenate them onto the end of the Python runtime's binary.

See also mkbundle for Mono.

---

### Post by juancarlospaco on 2012-02-28
> **ssokolow said:**
> No, you can compile restricted subsets of Python to C. (See RPython and ShedSkin)

Pyrex and Cython don't even do that much unless you provide explicit type annotations.

The only thing you can do with the full Python language is use tools like freeze, cx_freeze, and py2exe to zip up your .pyc bytecode files and concatenate them onto the end of the Python runtime's binary.

No.

[http://nuitka.net/blog/nuitka-a-python-compiler/](http://nuitka.net/blog/nuitka-a-python-compiler/)

---

### Post by durand on 2012-03-26
> **juancarlospaco said:**
> No.

[http://nuitka.net/blog/nuitka-a-python-compiler/](http://nuitka.net/blog/nuitka-a-python-compiler/)

Sounds interesting!

I've just started learning Vala and while I do like it, I find that managing libraries is a bit annoying, especially having to manually include them during compile. I guess I'm just used to the python way with "import" statements. I kinda wanted to learn Genie instead but there is next to no documentation on it and I don't want to end up writing code that is unusable in the future...

---

