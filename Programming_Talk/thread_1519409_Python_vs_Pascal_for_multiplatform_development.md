---
title: "Python vs Pascal for multiplatform development"
date: 2010-06-28
forum: Programming Talk
---

### Post by johnkyp on 2010-06-28
Hey guys,

I have a quick question regarding programming languages and most specifically Python vs Pascal. I have decided to learn a bit of programming after a course I took in University in my final semester last year, and would like your opinions about whether I should learn Python or Pascal.

Before you provide me with an answer please know that I am interested in multiplatform development and that Linux is my main OS, so I am wondering which of the two is better for programming under Linux but is easy to compile on other OSes as well. So far my research suggests that Pascal is the way to go, especially since Lazarus lets me design GUI interfaces with the benefit on working on windows and mac. However at the same time I'm also using Blender for 3d animation and the scripting language used in the software is Python. One more thing to keep in mind is that I plan to be doing programming as a hobby and not professionally. I also know that python is multiplatform but I haven't been able to find a good RAD for it. 

Thanks in advance for all your help :-)

---

### Post by unter on 2010-06-28
I amonly new programmer like you myself but I am sure I can answer this question.

Python!

Pythons is one of most portable languages available. Pascal is less portable and a dying language. 

also python is interpreted language and pascal is compiled. not relevent to your question but still to consider. 

:)

---

### Post by simeon87 on 2010-06-28
For programming under Linux, I would say Python. Isn't Pascal on the way out or have I not caught up with that area of software development?

---

### Post by unter on 2010-06-28
I believe pascal is now Delphi on windows and is declined.

---

### Post by lisati on 2010-06-28
There's "[FreePascal]("http://www.freepascal.org/")" which is cross platform. It's in the repos.

---

### Post by DanielWaterworth on 2010-06-28
python has a huge following so the community support is great. I'd recommend it so long as you stick to multi-platform libraries.

---

### Post by 23dornot23d on 2010-06-28
The fact that you are using Blender and the scripts are written in python ...... plus it is widely used 
and there is plenty of help available here ......

  and if you can master one language fully instead of jumping between them - it can make life a lot easier on your brain .....


___________________________________________________

Once you master a language - Python ...... then move onto Pascal and other languages ..........

Just my 20 cents........ I love it and all the Blender Scripts ...... 

(Qt4 is also good for the front end GUI display and it allows the Qt4 to be easily converted to Python too ...)

Also try a     [Search]("http://www.google.com/cse?cx=002683415331144861350%3Atsq8didf9x0&q=python+is+multiplatform+but+I+haven%27t+been+able+to+find+a+good+RAD&ie=utf-8&sa=Search") to see what else you can find out about it ..........

---

### Post by -grubby on 2010-06-28
Python is quite platform agnostic, and does not need to be compiled. For easy packaging, check out [Python Packager](http://python-packager.com/) ([py2app](http://svn.pythonmac.org/py2app/py2app/trunk/doc/index.html) for Mac.) For GUIs, see [PyQt4](http://www.riverbankcomputing.co.uk/news). There is a cross-platform GUI designer as well (which generates ui files. Use pyuic4 to convert them to code.) You could also use PyGTK, but GTK isn't exactly great on the Mac (it requires X11, and renders it's menus as it does on other operating systems.)

---

### Post by juancarlospaco on 2010-06-28
[I]Python have bindings to toasters and lawn mowers... 
and with standard and abtracted coding is cross-platform[/I]

---

### Post by Simian Man on 2010-06-28
There is almost no reason to use Pascal for new code.  It is a dying language, lacks a lot of modern features and, worst of all, doesn't have a well-observed standard or a de-facto standard implementation.

---

### Post by trent.josephsen on 2010-06-28
I was not in the industry during Pascal's heyday, but from what I understand it was never much outside of academia.  Not really a dying language; rather a language that was never fully alive.  There have been attempts to use Pascal and Pascal-based languages for real projects, but it just doesn't have the framework or the industry support for heavy lifting (not that people haven't tried).  Python on the other hand is a great language that is easy to learn but incredibly powerful at the same time.  Python daily gains more support in exciting and quickly growing areas like robotics, as well as tested technologies like regular expressions and socket programming.  I think it's a shoo-in for Python.

---

### Post by wmcbrine on 2010-06-28
> **trent.josephsen said:**
> I was not in the industry during Pascal's heyday, but from what I understand it was never much outside of academia.Actually it was huge in the early PC (DOS) scene, in the form of Turbo/Borland Pascal, and did OK for a while in Windows as Delphi (another flavor of Borland). IIRC, it was a big part of early Mac development, too. But I think it's time to let it die. C beats it on the low end, and Python (and many others) on the high end.

Back in my Turbo Pascal days, I was always running into frustrations at the limitations of the language, and I'd end up doing inline assembly to get around them. Then I found C, and I didn't have to do that anymore.

Nowadays, my machine is a thousand times faster, so I'm not as focused on code speed as on coding speed, and I find Python more rewarding. In some small ways, it reminds me of Pascal. But it's much freer than either Pascal or C.

---

### Post by xefix on 2010-06-28
I don't know if the two are necessarily comparable. You always have to choose the right tool for the job, and neither of the two languages you listed will be right for every job. In fact, I don't recommend that you limit yourself to a single language at all...when you know the logic of programming, you can pick up new languages (especially higher-level languages) fairly quickly. That said, I'd still go with Python just because it's so damn elegant (can't speak for Pascal, having never used it)

---

### Post by trent.josephsen on 2010-06-28
> **wmcbrine said:**
> Actually it was huge in the early PC (DOS) scene, in the form of Turbo/Borland Pascal, and did OK for a while in Windows as Delphi (another flavor of Borland). IIRC, it was a big part of early Mac development, too.

Popular, yes, but was it ever used for real programming?  When I think about Pascal I imagine rows of coding peons studying for their CS exams, not software engineers working for Microsoft.  Correct me if I'm wrong.

---

### Post by wmcbrine on 2010-06-28
> **trent.josephsen said:**
> Popular, yes, but was it ever used for real programming?Yes.

> *Correct me if I'm wrong.*You're wrong.

In the late 80's PC scene, C was nowhere near as dominant as it later became. I think the largest portion of shareware was written in Turbo Pascal. (Microsoft of course had their own Pascal.)

---

### Post by trent.josephsen on 2010-06-28
> **wmcbrine said:**
> Yes.

You're wrong.

In the late 80's PC scene, C was nowhere near as dominant as it later became. I think the largest portion of shareware was written in Turbo Pascal. (Microsoft of course had their own Pascal.)

Okay... examples, maybe?  Something that typical PC users of the time might be familiar with?

---

### Post by unter on 2010-06-28
Skype is written in Delphi. Fruity loops written in delphi. Dev C++ written in Delphi to i think?

---

### Post by wmcbrine on 2010-06-28
I don't know what a "typical PC user" is. I don't know what you might be familiar with. But, here's a quote:

[url=http://www.taoyue.com/tutorials/pascal/history.html]"Soon, Turbo Pascal became the de facto standard for programming on the PC. When PC Magazine published source code for utility programs, it was usually in either assembly or Turbo Pascal.

At the same time, Apple came out with its Macintosh series of computers. As Pascal was the preeminent structured programming language of the day, Apple chose Pascal as the standard programming language for the Mac. When programmers received the API and example code for Mac programming, it was all in Pascal."[/url]

If that doesn't satisfy you... do your own research. I'm not particularly interested in defending Pascal. But as you note, you weren't around in its heyday. I was; I remember it.

---

### Post by trent.josephsen on 2010-06-28
Thanks; my curiosity has been satisfied.

---

