---
title: "Programming Ubuntu"
date: 2016-08-21
forum: Programming Talk
---

### Post by prole101 on 2016-08-21
Hi All,

Newbie here. A thousand apologies if my question has been asked a thousand times already, though I didn't see what I was looking for in the stickies, the first page or a rudimentary search.
I'm interested in programming apps for Linux. I have experience in embedded C and some knowledge of C++ (and object oriented design in general). 
I need a foundation in how Linux works and how to program applications for it (as in desktop apps). Will be eternally grateful for direction to good online resources to this end, and perhaps offline (i.e. books) ones too. (Whilst grateful for the sentiment, should it occur to you, I am not looking for a cout << "hello world" type app to get me going. A basic windowing app in C++ would be more like it, cheers in advance).

many thanks in advance.

Additional info: I have 16.04.1 installed. I am very much a Linux newbie. I know a few command line operations like ls, how to install a package and that sort of thing, but still very inexperienced with Linux. (I think I posted this in the wrong thread! doh!)

---

### Post by howefield on 2016-08-21
Hello and welcome to the forums.

Thread moved to the "*Programming Talk*" forum for a better fit.

---

### Post by prole101 on 2016-08-21
Apologies and thanks

---

### Post by prole101 on 2016-08-21
Ah this forum has a useful set of stickies. Cheers

---

### Post by Olav on 2016-08-21
For GUI applications you will probably use the GTK+ 3 toolkit (the toolkit provides all your basic windows, toolbars, menus, buttons etc.). This looks like a nice primer, but it uses straight C not C++: [https://developer.gnome.org/gtk3/stable/index.html](https://developer.gnome.org/gtk3/stable/index.html).

Of course GTK+ 3 can also be used with C++, Python and others.

wxWidgets is another cross platform, multi language toolkit (I like it a lot). And this is a proper tutorial with C++: [http://zetcode.com/gui/wxwidgets/](http://zetcode.com/gui/wxwidgets/).

Not sure if I can really help you much further than this, but at least now you have a few more keywords to try with Google.

---

### Post by prole101 on 2016-08-21
Thanks Olav,  Will have a look at GTK+ 3 and wxWidgets.

---

### Post by Olav on 2016-08-24
Cool, have fun.

---

### Post by coldraven on 2016-08-24
Not that I can do much programming these days but have a look at QT Designer, it's in the Software Centre. AFAIK you can link the actions with just about any code. I believe it's free for personal use.

---

### Post by prole101 on 2016-08-26
Thanks for that. I had a brief look at QT. The IDE looks really good,  but as I proceeded to attempt to get QT the rules and legals started to  feel over-bearing and scared me off. Thought I might try to get on with  whatever is available in the Ubuntu packages.

Have you used QT Designer?

---

### Post by spjackson on 2016-08-26
> **prole101 said:**
> Thanks for that. I had a brief look at QT. The IDE looks really good,  but as I proceeded to attempt to get QT the rules and legals started to  feel over-bearing and scared me off.

I feel your pain, but...
> 
 Thought I might try to get on with  whatever is available in the Ubuntu packages.

Have you used QT Designer?
Qt **is** in the Ubuntu packages.

---

### Post by prole101 on 2016-08-29
noob shame :oops: (and simultaneous joy :P)
time to open the package manager!

---

