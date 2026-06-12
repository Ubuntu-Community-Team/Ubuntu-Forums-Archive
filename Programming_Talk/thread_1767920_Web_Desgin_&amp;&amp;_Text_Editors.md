---
title: "Web Desgin &amp;&amp; Text Editors"
date: 2011-05-26
forum: Programming Talk
---

### Post by xyjames1488 on 2011-05-26
Hello Forums,

I am working on a project, and am mid-deadline. Trying to make a switch to Linux while doing this. I am having a few issues, as my main software was a plug-in bloated Notepad++. I am looking for a good multi-language editor, (Not a WYSIWYG) with quick indexing(I make tons of files.), tag support(Why not save time?), clean UI(a clean page, is a good site.) and organized for use(If I can not see it, it doesn't exist.). I have other issues, but one at a time.

I thank anyone who helps, and am looking forward to the advice and recommendations

James.

---

### Post by r-senior on 2011-05-26
I've not used it much, but try Bluefish. It's in the repositories:

```

sudo apt-get install bluefish

```

---

### Post by satanselbow on 2011-05-26
Komodo Edit is my long time fave - Netbeans is also a goodie although is a tad heavier. Very much what languages you need support for? Both cover all the web bases though ;)

---

### Post by psusi on 2011-05-26
I would recommend NOT trying to learn new tools in the middle of a project with a deadline.  Save that for when you have some spare time.

Emacs has a bit of a steep learning curve, but is extremely powerful.  Be prepared to spend hours and hours reading the manual.  It is built to be fast and flexible, not easy or flashy.

---

### Post by Mr. Picklesworth on 2011-05-26
> **xyjames1488 said:**
> Hello Forums,

I am working on a project, and am mid-deadline. Trying to make a switch to Linux while doing this. I am having a few issues, as my main software was a plug-in bloated Notepad++. I am looking for a good multi-language editor, (Not a WYSIWYG) with quick indexing(I make tons of files.), tag support(Why not save time?), clean UI(a clean page, is a good site.) and organized for use(If I can not see it, it doesn't exist.). I have other issues, but one at a time.

I thank anyone who helps, and am looking forward to the advice and recommendations

James.

Two from me:

The default text editor (gedit) has lots of plugins available that you might like. First, you'll probably need to [install the gedit-plugins package]("apt:gedit-plugins"). In gedit, go to Edit&#8250;Preferences and you can enable (and configure) plugins. For me, Draw Spaces (configured to only draw tabs), Bracket Completion and Word Completion are indispensable. It doesn't have all the bells and whistles like automatic closing tags, but I have found it quite effective.

My other favourite editor is [Scribes]("apt:scribes"), which is a delightfully simple little editor that is excellent for Python and does just as well with web front-end stuff. All those things that gedit has through plugins are built in, and it does a really good job staying out of the way. It does templates (though you'll have to add them manually in the Template Editor) and you can process text through arbitrary Unix commands by pressing Alt+X. Find & Replace support regex (yay!) but is otherwise terribly broken.  If you like it, you may want to add the repository from [their website]("http://scribes.sf.net/") so you get updates as they happen.
Scribes saves files immediately as you edit them (there is no such thing as an unsaved file) and it doesn't do tabs (instead leaving that job to the window manager), so there's a bit of a learning curve but for some strange people (me!) it fits perfectly.

---

### Post by xyjames1488 on 2011-05-26
Wow, Linux community to the rescue! You folks are social engineers. 

Going to stick with Windows until I launch the project. Sounds like solid advice. lol Okay for my languages; Basic line-up, xhtml, Java, SQL, soon(next project will need C). So anything with those would be good.

You all sent down some good ideas, so come time to jump into this. I will have a good line-up for editors. 

I am also looking for a code compiler for C, I use Bloodshed, Visual Studios 2010, and Notepad++ at the moment.

---

### Post by heyandy889 on 2011-05-26
I use gcc in the terminal for compiling C code. I use gedit as the editor, it has built-in syntax highlighting

say you are in the folder w your source code

% gcc mycode.c
% ./a.out
Hello, world!
% exit

That's what might happen. :-D

---

### Post by psusi on 2011-05-26
THE C compiler for linux ( and also available for windows, mac, just about every platform and cpu architecture ) is gcc.  One usually uses GNU Make to build the whole project, invoking tools like gcc as needed.  Emacs can run make for you and displays the output in its own window where you can put the cursor on any errors and hit enter and it will open the file and jump to the offending line of code.  It also integrates with just about any version control system under the sun.

---

### Post by lordadi on 2011-05-26
Just thought I'd mention a code-editor I find lightweight, fast and flexible (I redid my school website in this - PHP, MySQL and xHTML). It's called Geany:

```
sudo apt-get install geany
```

Their website is [http://www.geany.org/](http://www.geany.org/)

---

### Post by xyjames1488 on 2011-05-26
Well, in Windows I never could get much chatter on the forums. I appreciate all the help and I think I might go with Scribe, come the time. 

So, here is a little more depth into the 'ek' of xyjames1488.
I am actually new to code editing and my current project is my first ever. It is also my heaviest, current struggle. The reason I delve into my more personal self, is because you all seem to be much more experienced than I am.

So my question is, how did you all learn your 'ropes'? I thought I knew coding and the needs for handling a serious project, but now that I am thrown into the arena and met to make words meet action. I am left without a clue where to start and how to end.

I have ideas for where I am going, but what are the crawling steps I must have missed to actually get to that destination.


Wow, what a change of topic. Well, like I said, I will no doubt have more information I seek to pry from the minds of Ubuntu Forums.

---

### Post by Gerontion on 2011-05-27
I'm using gEdit at the moment and one plugin I've found useful for switching between languages is the EditShortcuts plugin, which you can get from [http://empty.23inch.de/pmwiki.php/Main/EditShortcuts](http://empty.23inch.de/pmwiki.php/Main/EditShortcuts)

edit:

> I am actually new to code editing and my current project is my first ever.Ha! Me too. As the local computer expert (i.e. I can write a formula in Excel), I've been asked to develop an online elearning project. Way out of my depth, but it's great fun learning new stuff.

---

### Post by Petrolea on 2011-05-27
> **lordadi said:**
> Just thought I'd mention a code-editor I find lightweight, fast and flexible (I redid my school website in this - PHP, MySQL and xHTML). It's called Geany:

```
sudo apt-get install geany
```

Their website is [http://www.geany.org/](http://www.geany.org/)

+1 for Geany. It is all you need. I do all my programming in it in all kinds of languages, it has lots of features, is lightweight, simple and good looking.

For compiler: gcc as mentioned before.

---

### Post by Petrolea on 2011-05-27
> **xyjames1488 said:**
> Well, in Windows I never could get much chatter on the forums. I appreciate all the help and I think I might go with Scribe, come the time. 

So, here is a little more depth into the 'ek' of xyjames1488.
I am actually new to code editing and my current project is my first ever. It is also my heaviest, current struggle. The reason I delve into my more personal self, is because you all seem to be much more experienced than I am.

So my question is, how did you all learn your 'ropes'? I thought I knew coding and the needs for handling a serious project, but now that I am thrown into the arena and met to make words meet action. I am left without a clue where to start and how to end.

I have ideas for where I am going, but what are the crawling steps I must have missed to actually get to that destination.


Wow, what a change of topic. Well, like I said, I will no doubt have more information I seek to pry from the minds of Ubuntu Forums.

Where to start you ask? From nothing. If you're making a website, write the basic tags and do the easy features first. Then upgrade and upgrade and upgrade and upgrade. Don't go straight to something that you couldn't make even in dreams. 

If you won't understand your code you will have lots of trouble when something will go wrong (especially in your C code: if you copy-paste some code with pointers then possible seg faults will kill you).

It might be hard at first but you will develop your programming style and handling projects will be much easier. 

For example:
I had to make a website that will get some input from user and draw graph. I had no idea on how to make it. So first I made my whole website with all the basic stuff (like menus, news,...).
Then I found out how to easily draw a graph offline and save it to a specific location. 
I made a script out of it and put some code on my website that ran the script on server. Graphs were all saved in a directory and all that was left is to give it my own input and draw the images on website. My project was soon finished after that.

I guess that's one of many ways to handle making something bigger than you think you can.

Hope that gives you an idea on hove to start solving a problem like this :)

---

### Post by Mr. Picklesworth on 2011-05-27
> **xyjames1488 said:**
> So, here is a little more depth into the 'ek' of xyjames1488.
I am actually new to code editing and my current project is my first ever. It is also my heaviest, current struggle. The reason I delve into my more personal self, is because you all seem to be much more experienced than I am.

So my question is, how did you all learn your 'ropes'? I thought I knew coding and the needs for handling a serious project, but now that I am thrown into the arena and met to make words meet action. I am left without a clue where to start and how to end.

I have ideas for where I am going, but what are the crawling steps I must have missed to actually get to that destination.


Wow, what a change of topic. Well, like I said, I will no doubt have more information I seek to pry from the minds of Ubuntu Forums.

On the web, the best thing you can do is have Firebug or Chrome's web inspector available at all times.

For programming (and the web), my first bit of advice is to avoid code generators unless you know what the manual approach entails. It'll help you make informed decisions about tools for a project, and you might find your code looking very pretty as well. (Besides, code generators are evil).

I also mean that with build systems, too. I had the pleasure of doing a group programming assignment with someone who used GNU Make and started writing the makefile from scratch. It scared me at first, but after a bit of fiddling (I had sort of tinkered with Make before) I had it figured out and now I'm much more comfortable with it – and with my preference of Waf :b It really helps that Make has some solid documentation, too.
The important thing here is a lot of makefiles are generated by automake (and if you look at any open source code, you'll see lots of them), but hand-made ones are a great way to understand what it going on (and sometimes the best choice, for simpler projects).

I don't quite know where you are in general, but some other things that have served me well at different points…

Look at gcc's -v and -save-temps arguments and try invoking specific programs to build a program in parts. (For each file run the precompiler, then the compiler to turn it into assembly code, then the assembler, then the linker!). There's a lot of understanding to be gained from that small but addictive exercise. It's especially useful to know just how much the linker does and what ld-linux (the dynamic loader) is all about. Oh, and try invoking ld-linux from the command line. Much fun!

If you happen to have an interested in low level stuff now, dissy is a nice tool you can install from Software Centre. It's a really simple disassembler that gives you an elegant view of an object file in its actual form, the assembly code that made it, and (if you compiled with gcc -g) the source code that made that assembly code.

Okay, that might look daunting, but it can be enlightening when taken in little chunks. Honest! Definitely not of vast importance, though :)

Oh, now that everyone has you using text editors instead of IDEs for programming (it's sort of the Linux way; small, distinct tools seem to suit this platform really well)… My favourite debugger of late: Nemiver.

---

### Post by xyjames1488 on 2011-05-27
Well, I am taking the advice and ditching some of my 're-used code' and making just the basic site, then molding it into something more. 
I think my biggest issue is that this is a serious project, so it has become intimidating, much like finals in high school. They can be simple, but can also be intimidating due to it's importance.

Thanks for all the help folks. Any more advice is always welcome. I checked out a lot of the software and I must say, it does seem I prejudged Linux. It has good software to select from, just requires a little searching about.

---

### Post by lordadi on 2011-05-27
If you happen to have to use PHP (not sure if you mentioned this as a requirement), I would ditch Geany and use Netbeans: PHP with xDebug. 

This combination is highly powerful and lets you step through code and watch variables etc (server side!) - very useful when learning about PHP's loose type handling.

---

### Post by ApOgEEs on 2011-05-27
> **xyjames1488 said:**
> Hello Forums,

I am working on a project, and am mid-deadline. Trying to make a switch to Linux while doing this. I am having a few issues, as my main software was a plug-in bloated Notepad++. I am looking for a good multi-language editor, (Not a WYSIWYG) with quick indexing(I make tons of files.), tag support(Why not save time?), clean UI(a clean page, is a good site.) and organized for use(If I can not see it, it doesn't exist.). I have other issues, but one at a time.

I thank anyone who helps, and am looking forward to the advice and recommendations

James.

I am using:

1. Inkscape & GIMP - for graphics
2. Geany - for codes
3. Firefox + firebug - for debugging

> **xyjames1488 said:**
> 
I am also looking for a code compiler for C, I use Bloodshed, Visual Studios 2010, and Notepad++ at the moment.

I use Geany to write/edit C code. Then gcc to compile.

> **xyjames1488 said:**
> 
So, here is a little more depth into the 'ek' of xyjames1488.
I am actually new to code editing and my current project is my first ever. It is also my heaviest, current struggle. The reason I delve into my more personal self, is because you all seem to be much more experienced than I am.

So my question is, how did you all learn your 'ropes'? I thought I knew coding and the needs for handling a serious project, but now that I am thrown into the arena and met to make words meet action. I am left without a clue where to start and how to end.



I learn my 'ropes' by trying to tie my own knots from collections of known knots made by others. You can find them all over the internet. I do it until I can spin my own yarn, and make my own rope, out of any fibers. It is not recommended to start learning like me if you have serious project to do since you need more focus on that project.

---

