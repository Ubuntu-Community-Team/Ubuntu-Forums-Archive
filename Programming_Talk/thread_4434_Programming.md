---
title: "Programming"
date: 2004-11-15
forum: Programming Talk
---

### Post by trivialpackets on 2004-11-15
I am planning to do a bit of programming, beginning with my learning of C++.  Any advice on compilers or text editors and where I can find them?  Thanks all, will be a busy Thanksgiving break if all goes well.

---

### Post by sfw5000 on 2004-11-15
You should install gcc in synaptic... my favorite editor is bluefish -- but i do mostly PHP and bluefish is geared towards web development. A lot of people use Eclipse... also gedit has good syntax highlighting, if that's all you need.

---

### Post by Viro on 2004-11-15
Just stick to a simple text editor(like GEdit,though I usually prefer Kate from KDE) and g++ which is the C++ compiler that comes with gcc.

---

### Post by ynef on 2004-11-15
If you just install build-essential you're good to go.

For your coding pleasure I recommend either getting a good GUI text editor like the ones already suggested, or my personal favourite, vim. You already have vim installed and almost any UNIX like system you'll ever encounter will also have it. Knowing your way around vim is worth the half hour or so that the "program" vimtutor will take you to complete.

---

### Post by Klunk on 2004-11-15
I like eclipse. You can use teh same IDE for nearly ALL you development with plugins. I use it for Java, C++, PHP, Perl, scripts. It integrates with CVS and other source control software, it can even use an FTP site as a source repository.

Eclipse with the CDT both available form [www.eclipse.org](www.eclipse.org) will allow you to build and debug your C++ application from the same environment, it uses gcc under the covers. And then when you move on to Java you will still be in the same IDE.

---

### Post by duff on 2004-11-15
[QUOTE=eric.proctor]I am planning to do a bit of programming, beginning with my learning of C++.  Any advice on compilers or text editors and where I can find them?  Thanks all, will be a busy Thanksgiving break if all goes well.[/QUOTE]
 if you're going to stick with just C/C++ development in GNOME, you could give Anjuta ([http://anjuta.sf.net](http://anjuta.sf.net)) a shot.  You'll have to add the universe repos to get it though.

---

### Post by jeffjj on 2004-12-31
I am an experienced Java developer. I am trying to learn C development with GNOME. I would like to use the Eclipse IDE. I cannot seem to include the #include <gtk/gtk.h> file. I am using CDT 2.1.

However, I cannot seem to get the simplest thing running. Well, I do have a Hello World program running, but I cannot seem to include any header files such as #include <gtk/gtk.h>. It just says it cannot find it. There is this a blue folder that says includes and does have the gtk.h header buried in there so I do not know why it cannot search there and find it.

I can get things to work with Anjuta fine, but not Eclipse. I think Anjuta is ok, but Eclipse already seems to offer everything Anjuta has and I really like Eclipse a lot.

Its been fun learning C/GNOME even though I have just started. I found a project I thought would be fun to learn and hopefully add to. I didn't expect to get so bogged down in learning the GNU make tools though. In Javaland we are spoiled with IDE's/ANT that just handle the whole compiling environment and just worry about the code.

---

### Post by zeroK on 2004-12-31
[QUOTE=eric.proctor]I am planning to do a bit of programming, beginning with my learning of C++.  Any advice on compilers or text editors and where I can find them?  Thanks all, will be a busy Thanksgiving break if all goes well.[/QUOTE]
 IMO it's best to start without IDEs and use normal editors like VIM or Emacs. You want to learn programming and not IDEs :)

---

### Post by jeffjj on 2004-12-31
>> IMO it's best to start without IDEs and use normal editors like VIM or Emacs. You want to learn programming and not IDEs 

I agree and I do not agree. An IDE can hide some of the complexity so when things do not work it is confusing on why they are not working (hence my post I imagine). However things like code completion and the ability to jump from a variable to its declaration, or a method call to its declaration can be excellent teachers. Plus once you know a language well there is no comparision of how fast you can get a project done with an IDE versus just a text editor. My initial apprehension with learning C/GNOME on Linux is losing all my development tools. I was happy to find Anjuta and I will probably just stick to that unless someone can give some pointers on why Eclipse cannot find the header includes.

When I first started to learn Java I made the game donkey kong in notepad. I do not want to go back to that environment again.

I would also really like to know what people use on the really big open source projects. I mean what does the Ubuntu team use? Are they really hacking in VIM? If so I guess I would be shocked...and then I guess I would have to go fire up VIM and give it a shot :).

I appreciate your comments though.

-Jeff

---

### Post by jeffjj on 2005-01-02
I fixed my problem. I had to include every source folder in the project paths source tab (Properties --> C/C++ Project Paths --> Source). Once I had my Source option set up correctly the auto discovery found all my libraries. This is cool. Now I can do my Java and C programming all in one IDE. The C plugin has a mere fraction of what I have in Java for IDE functionality, but I guess its enough. I can even run the project from within Eclipse now.

---

### Post by Quest-Master on 2005-01-02
Once you get into large and expansive projects, Anjuta is a godsend. With lots of automated stuff and GNOME integration, it's great tool on Ubuntu.

---

### Post by sah on 2005-01-08
[QUOTE=jeffjj]I fixed my problem. I had to include every source folder in the project paths source tab (Properties --> C/C++ Project Paths --> Source). Once I had my Source option set up correctly the auto discovery found all my libraries. This is cool. Now I can do my Java and C programming all in one IDE. The C plugin has a mere fraction of what I have in Java for IDE functionality, but I guess its enough. I can even run the project from within Eclipse now.[/QUOTE]
 Try vim agian, but this time take a look at it's man pages to learn how to configure it. You can config vim to do most things IDE editors do for you. Jumping to instances of a variable is as easy as jumping to an instance of an expression in vim..just use vim's expression search :) .
```

/pattern <enter>

```
Then hit "n" to skip to the next instance of the expression (and thus every time that variable is referenced, or whatever expression you searched for).

---

### Post by jeffjj on 2005-02-20
I have been working with Eclipse for quite a few weeks. Unfortunately the C/C++ plugin is not even close to as feature rich as the Java plugin. Plus it seems to have memory issue with the C plugin...after working for a while the whole IDE just starts slowing up to  where its not usable. So I decided to give Anjuta another shot. I have to say that it is a much stronger IDE than I expected. It does lack most of the power tools that I have grown used to in the Eclipse Java plugin, but yet Anjuta is a pleasure to work with. Everything works like it is supposed to. Plus I kind of like how it splits my project up with the headers in one place and source in another. I'm glad I went back and tried it again.

Well, really starting to get how to program in C with the GTK toolkit. The GTK toolkit is very strong. So far everything just works.

---

### Post by drasko on 2005-02-20
I agree with jeffjj - Anjuta is a great IDE! Great thing for C/C++.
As cocncerning the editors I would reccomend a Scite - the best editor I've seen so far...

---

### Post by waratah on 2005-02-20
C++ is a fairly complex language so be prepared to spend some time with it.   Firstly why C++ as opposed to other OOo oriented languages.   A scripting type language is much easier to deal with and does not require the miriad of details that you must with C++, great for control lousy for learning.   Smalltalk offers a simpler pure OOo environment and will force you to learn OOo properly, C++ is to easy to program in procedural code breaking the OO paradigm.

g++ is the compiler for C++.    There are others however I think that this is the easiest to install and it is #2 in terms of compliance to the standards.

Regarding editors there are a definite range that you can choose from.   gedit is a simple editor and good for starters,  emacs or xemacs is an advanced editor with some real power but really requries some time to learn,  vi is the editor of choice for Administrators because it is small and fast and always available.   I use vi but I recommend that you look at emacs as a powerful editor.

I wish you luck with you quest into programming.

---

### Post by Quest-Master on 2005-02-21
For smaller projects, mostly done in either PHP, Ruby, or Python, I've really begun to love ScITE. It's fast, lightweight, takes no time to load, is filled with all the features needed of an editor, and is pretty much perfect all around. :D

---

