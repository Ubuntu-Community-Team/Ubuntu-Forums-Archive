---
title: "standstill..."
date: 2008-01-23
forum: Programming Talk
---

### Post by Alberio on 2008-01-23
Hello all..

Thing is, I'd like some help with what to do now....

I've taken AP Compsci (Java) and got an A. That really doesn't mean much at all. 

I've learned to implement graphics in Java through Swing and using panels for drawing. 
-Know the basic data structures and info (stacks, queues, maps, sets, graph theory (dijkstra) and the like.. (OO, polymorphism, inheritence, the multiple inheritence problems, etc.))

I'm bored, honestly.

I have been learning C++. So far I've done nothing more productive than messing with making libraries and making knights tour. (if you don't know what that is, it's programming the knight to touch all 64 squares of a chess-board without stepping on a square more than once.)

I made that a couple of hours in.

I got bored.

I wanted to learn something a little more interesting, or more advanced. (like, say, accessing file trees in C++, calling other programs within mine (not exactly sure how possible this is, or if a bash script is the way to do it.) 
But specifically, graphics. Well this turned out to be harder than I expected in C++. Honestly, I have no idea how to do it. In VC++6 in windows I've popped up a dinky little window. In here, I'm still stuck on the console, and don't really know how to even open a window, let alone calling up a canvas.) (btw, how would I clear the console screen, I could then make some more dinky console games :popcorn:)

Most of the C++ tutorials I find just talk at me again about data types, arrays, functions, return types,structs,header files,etc.

I know the basics, I'd like to learn to do something worthwhile, or interesting. (I did give an OK GUI to my knight's tour in Java, even that would be great to learn in C++).

(I really mean just about anything. Threads, networking, hell, printing to the console in color. clearing the console. GUI & graphics. Through Qt? just about anything. (how to play music, how to load and display pictures, etc.))

Honestly the reason I wanted to learn to program (back when I was 11?) was to make a game. That goal has never left my mind. I understand how complicated and hellish it is to make a decent game. I'm willing to go for it. I'm not afraid of a huge workload. The problem is, everything I read is either basic or over my head. (also focused on DirectX, when I want to learn OpenGL. I wont mind learning DirectX, but I'd like to later expand into 3d in different OS's, and I'm not exactly a fan of windows. (it's also terribly slow on my computer )))

I'm perfectly fine with learning 2D graphics too, as long as I'm doing something.

No I don't know where my KDE and QT install directories are, no I don't know my compiler inside and out. As for my choice of IDE, I don't have one (for C++. Though for java I use Eclipse, usually). I use Kate(and really liking it, btw). All I really want is something that indents for me, and maybe color-codes (though that's not necessary at all)


I don't know how to install a graphics library. (that would be great if somebody could explain).

Yes, there probably will be many steps on my way to these things. I'll take them, but I'm hoping that someone could show me a way. 

I'm sorry if this post ends up sounding like a rant, but I am at, as I said, a standstill. I know what I want to do. I don't know how to do it. 
If you can help with any of the problems here in any way,
whether it be links to a tutorial, recommendations for books, advice, or straight answers, they will be greatly appreciated.

Thank You, (very much, really)
     Alberio



p.s. How would I use and install Lisp? :S
- could I use it under Kate, or in another graphical environment? I'm not scared of the console, It's just that graphical is convenient.

---

### Post by LaRoza on 2008-01-23
> **Alberio said:**
> 
I'm bored, honestly.

I got bored.

I wanted to learn something a little more interesting, or more advanced. (like, say, accessing file trees in C++, calling other programs within mine (not exactly sure how possible this is, or if a bash script is the way to do it.) 
But specifically, graphics. Well this turned out to be harder than I expected in C++. Honestly, I have no idea how to do it. In VC++6 in windows I've popped up a dinky little window. In here, I'm still stuck on the console, and don't really know how to even open a window, let alone calling up a canvas.) (btw, how would I clear the console screen, I could then make some more dinky console games)

I know the basics, I'd like to learn to do something worthwhile, or interesting. (I did give an OK GUI to my knight's tour in Java, even that would be great to learn in C++).

I'm perfectly fine with learning 2D graphics too, as long as I'm doing something.

I don't know how to install a graphics library. (that would be great if somebody could explain).

p.s. How would I use and install Lisp? :S

For clearing the console, you can use "system" or use Ncurses. Ncurses might interest you.

I was going to say you need Lisp. I recommend GNU Common Lisp or Scheme.

```

sudo aptitude install gcl

```
For Common Lisp, don't know for Scheme, search in synaptic.

See my wiki.

It looks like you are might like using Python and PyGame. You can get 3d game engines for Python also.

For the graphics libraries, you can almost always install them in Synaptic.

---

### Post by Alberio on 2008-01-23
Thanks for the reply.

I touched python a few years ago. never learned to do too much. Maybe I will try it again.

heh, I just looked into System, this seems to be very useful, thank you.

do you know of any specifically good graphics library?



-does anybody have the answers to the rest of the questions?

---

### Post by LaRoza on 2008-01-23
> **Alberio said:**
> do you know of any specifically good graphics library?

For GUI's, I usually recommend wxWidgets, because it works in a lot of languages, and is cross platform.

GTK, QT, and Tk are big ones, with a long history and good docs.

My wiki has links for these for each language (at least, the ones I have listed)

---

### Post by Alberio on 2008-01-23
how would I read in a keypress? not just the pause, actually know what key has been pressed

---

### Post by LaRoza on 2008-01-23
> **Alberio said:**
> how would I read in a keypress? not just the pause, actually know what key has been pressed

I don't do much GUI programming, you'll have to investigate that for yourself. See my wiki.

---

### Post by pmasiar on 2008-01-23
Learn different language, something what will blow your mind. Schema, Forth.

For games, the best toolkit I found is Game Maker (it is windoes only, thats why we are doing Linux clone). It is so simple that 10 years old can create games with it.

For more "hands-on", try Python and Pygames. Substantially more fun that wrestling with Java (I know I do Java in my day job). But learn programming in commandline first (text mode, no GUI). See wiki in my sig for links to training tasks.

---

### Post by wolfbone on 2008-01-23
> **Alberio said:**
> Hello all..

p.s. How would I use and install Lisp? :S
- could I use it under Kate, or in another graphical environment? I'm not scared of the console, It's just that graphical is convenient.

The modern (and canonical) environment for FOSS Common Lisp development on GNU/Linux is the trinity: Emacs, SLIME and a supported Lisp (e.g. SBCL or CLISP).

---

### Post by Alberio on 2008-01-25
> 
Learn different language, something what will blow your mind. Schema, Forth.

For games, the best toolkit I found is Game Maker (it is windoes only, thats why we are doing Linux clone). It is so simple that 10 years old can create games with it.

For more "hands-on", try Python and Pygames. Substantially more fun that wrestling with Java (I know I do Java in my day job). But learn programming in commandline first (text mode, no GUI). See wiki in my sig for links to training tasks.


Learning C++ and Lisp, currently. 

I don't want to use Game Maker. I want to make everything. (by the way, you don't think the Torque engine is better than game maker?)

so, I achieved something a couple of hours ago. I finally got some Qt code I wrote following a tutorial, working. stupidly, I didn't realize that I had to change the links of uic and qmake to qmake-qt4 and uic-qt4 for it to work. 

So I'm currently exploring Qt, reading through the API, and going to more tutorials. This really isn't as far away from Swing as it first seems. It's actually a little easier (the Qt Designer, specifically ).


As for Python, I used to know it a little. that was a few of years ago. It was my first language, I believe. I never got good at it. I might look back into it, but not just yet. 


[quote=wolfbane]The modern (and canonical) environment for FOSS Common Lisp development on GNU/Linux is the trinity: Emacs, SLIME and a supported Lisp (e.g. SBCL or CLISP).[/quote]

Thank you, I just found out this morning that we're expected to use LispWorks. I will still look into Emacs & SLIME.

---

