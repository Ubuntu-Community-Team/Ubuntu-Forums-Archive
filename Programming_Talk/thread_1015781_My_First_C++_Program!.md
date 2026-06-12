---
title: "My First C++ Program!"
date: 2008-12-19
forum: Programming Talk
---

### Post by iampriteshdesai on 2008-12-19
Hi!
I am currently doing Computer Engineering and my exams will end soon. After my exams I would like build my first software in C++
I have never built any real application except for the noob stuff like "Pascal's triangle, patterns, fibonacci, classes, inheritance, etc"
However I would like to build a real application which will have it own window, be a proper app.
Plz give me few suggestions.
Which program should I try?
Where should I begin?
How should I begin?
Should I code for Windows or Linux?
thanks!

---

### Post by ajcham on 2008-12-19
> **iampriteshdesai said:**
> 
Should I code for Windows or Linux?


Why not build something cross-platform?

---

### Post by iampriteshdesai on 2008-12-19
It is my first program, I want to do something which I can do, I dont want to chew more than I can....

---

### Post by Bachstelze on 2008-12-19
Moved to Programming Talk.

---

### Post by jpmelos on 2008-12-19
Man, building cross-platform applications is easy, because all you need to do is write it in ANSI C++... Any program that follows the standard guidelines and uses the standard library only is cross platform because can be compiled in any.

---

### Post by ankursethi on 2008-12-19
I see you're from India (which part, BTW?), so before I suggest *anything* I'd like to tell you this : if you're using Turbo C++, you're shooting yourlsef in the foot. Turbo C++ is an old, non standard, 16 bit DOS IDE that went out of fashion in 1995. It's a shame Indian universities still use it. I don't know what compiler you're using, but I included this bit of information for the sake of completeness. If you're using GCC, just ignore this paragraph.

For cross platform development, get the GNU Compiler Collection (or GCC). In Ubuntu :
```
sudo apt-get install build-essential
```

To compile C++ :
```
g++ <FILENAME>.cpp -o <OUTPUT_FILE_NAME>
```

My exams also end tomorrow, and I'm learning Qt for cross platform development. It's the toolkit of choice for KDE development and is also heavily used by Skype, Google Earth and VLC, to name a few. Probably the best choice for cross platform GUI development using C++. Why don't you take a look?

I'm going to spend the next 15 days building small applications. A few ideas I have are :
1. A media player (made dead simple, thanks to Phonon)
2. Sticky notes (I recently switched to a Mac and I really miss Tomboy)
3. A simple text editor
4. An RSS reader

None of these are particularly difficult since Qt provides several libraries for networking, XML, databases etc.

---

### Post by mali2297 on 2008-12-19
Hi iampriteshdesai.

> **iampriteshdesai said:**
> 
Which program should I try?

Is there some app that you miss yourself as a user?
...or do you have a favorite app that you think can be improved in some way?
...or an app that would be just fun to clone?

> 
Where should I begin?
How should I begin?

Look for similar apps ([http://freshmeat.net/](http://freshmeat.net/)) and fetch the source code. Try to understand how the program works. A small program would be easier. I think the big obstacle would be to understand how to use gtk+ or qt. Find a tutorial.

> 
Should I code for Windows or Linux?

You're asking this on a Linux forum?

---

### Post by iampriteshdesai on 2008-12-19
Hi, yeah I'm an Indian.
You are right about TC++, our college uses it too, I'll use Code Bloks if that is required.
I will write an tutorial to run TC++ in Ubuntu for other students like me on my blog.
Is there any GCC variant which has GUI?
Thanks!

---

### Post by iampriteshdesai on 2008-12-19
Thanks for the site mail2297
Do you have any experiance about it?
It is too tough?
Thanks!

---

### Post by jimi_hendrix on 2008-12-19
> **iampriteshdesai said:**
> .
Is there any GCC variant which has GUI?


that would be an ide...which you dont need but if you insist then use the one that you like the best

---

### Post by WaeV on 2008-12-19
If you want a suggestion for a C++ GUI, I use Geany.  The class I'm taking comes with Visual C++ 2005, but I prefer Geany anyways.

As for *what* you should program... Hmmm...

---

### Post by jimi_hendrix on 2008-12-19
> **WaeV said:**
>  The class I'm taking comes with Visual C++ 2005

have you had the problem yet about some error about some long pointer to a string when you try and put "hello world" in a message box or something like that?

when i ran into that i stopped coding on windows

---

### Post by Trail on 2008-12-19
Please don't touch the Windows API for the sake of your own sanity.

---

### Post by mali2297 on 2008-12-19
> **iampriteshdesai said:**
> 
Do you have any experiance about it?

My experience with C++ is related to scientific computing. I am not a professional programmer (rather a mathematician/statistician). On my free time though, I have been working on a PDF viewer written in plain C and GTK+. The latter took some time to get a grip on, especially OO programming in C via [GObject](http://en.wikipedia.org/wiki/Gobject). It would probably have been easier to use C++ with [gtkmm](http://www.gtkmm.org/) (but then I would have learned less :-)).

> 
It is too tough?

No, but it will probably take some time and commitment.

---

### Post by ajackson on 2008-12-19
> **Trail said:**
> Please don't touch the Windows API for the sake of your own sanity.
Sanity is highly over-rated but I'd have to agree with avoiding the windows API if possible.

As for what to program, if you can't think of anything ask friends or relatives, see if they need a fairly simple app for doing something. Or if you are a member of a club, see if they need a simple membership system (if they haven't got one) or other such system.

---

### Post by ankursethi on 2008-12-19
@pritesh
Code::Blocks uses GCC behind the scenes :) In fact, any development environment that runs on a UNIX (Linux, Solaris, Mac OS X, the BSDs etc.) system probably uses GCC as the default compiler. So it doesn't really matter if you're using Geany, Code::Blocks, Eclipse, KDevelop, Anjuta or anything else. Your code is ultimately compiled by GCC.

Although you don't *need* to know what goes on behind the scenes, but it's always helpful knowing what your compier is doing. That's why I mostly code in a plain editor and compile from the command line when I write C++.

---

### Post by hessiess on 2008-12-19
You should also learn how to build probrams from the command line aswell, IDE's hide a lot, and if something IDE related goes wrong you need to know how to fix it.

Pearsonally I *HATE* IDE's, they massivly overcomplicate everything.

---

### Post by wmcbrine on 2008-12-19
I haven't used an IDE since Turbo Pascal. That was when I realized I could work a lot better with a dedicated text editor and command-line compilation.

But I do wonder sometimes if I'm missing anything, since I wouldn't even know where to start with a modern IDE.

---

