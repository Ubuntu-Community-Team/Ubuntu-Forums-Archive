---
title: "Alternative to MS Visual C++"
date: 2010-08-04
forum: Programming Talk
---

### Post by vishaluc on 2010-08-04
Can anyone suggest an alternative to visual c++ on Ubuntu?

---

### Post by tocado on 2010-08-04
> **vishaluc said:**
> Can anyone suggest an alternative to visual c++ on Ubuntu?

Try Gambas !

To Install:
```
sudo apt-get install gambas2
```

To read Documentation
[http://gambas.sourceforge.net/en/main.html]("http://gambas.sourceforge.net/en/main.html")

=)

BayZ !


By ToCaDo157

---

### Post by vishaluc on 2010-08-04
ThanQ :)

---

### Post by Newbie2910 on 2010-08-04
I programmed in C++ for years.  Now, I use C# and would not go back to C++ for anything.

---

### Post by Dragonbite on 2010-08-04
> **tocado said:**
> Try Gambas !

To Install:
```
sudo apt-get install gambas2
```

To read Documentation
[http://gambas.sourceforge.net/en/main.html]("http://gambas.sourceforge.net/en/main.html")

=)

BayZ !


By ToCaDo157

Gambas is VB, not C++ I thought.
Shouldn't there be something for it in Eclipse?

If you want to get into C# then can take a look at Monodevelop (which compiles to Mono, the open source .NET framework).

---

### Post by vishaluc on 2010-08-04
I need something for C++ because i have that in my course. So any good compilers for C++ ??

---

### Post by Npl on 2010-08-04
Are you searching for compilers or an IDE?
On Linux you almost always use g++ as compiler (just install build-essentials).
With Visual Studio you use MS Compiler "CL.exe". Both are just commandline tools.

An IDE is a set of tools to aid development (at least a texteditor which can use compilers directly), the only Linux IDE for C/C++ thats somewhat comfortable (IMHO) is [Code::Blocks]("http://www.codeblocks.org/")

If you`re just starting programming you probably should just use a text-editor and compiler. IDE`s are great and you dont want to miss them, but for learning you should do it the "hard way". Dont get totally dependent on IDEs, you sometimes cant use them and if you care about portability you will make your stuff compile-able from commandline

---

### Post by pbrane on 2010-08-04
Another decent IDE is anjuta. It's in the repositories. It has some features that resemble Visual Studio's as well.

---

### Post by interval1066 on 2010-08-04
Well, your compiler is going to be GNU C/C++, unless you want to shell out some bucks (or maybe they have a free version, I dunno) for Intel's dev suite. But for an IDE yeah, you could do worse than Anjuta. I like it because it seems to handle the gnu autotools correctly enough for my taste. And its really similar to DevStudio now in the way it handles release versions (debug/release code). It also has add-ons to integrate with subversion., and you can even configure it with your choice of editor panes if you compile it from source. Yeah, its pretty sweet.

---

### Post by Zorgoth on 2010-08-04
Who needs an IDE?

Emacs!  Emacs!  Emacs!

---

### Post by interval1066 on 2010-08-04
Ugg. I used emacs for years. I still think fondly of it. But I've kind of, I dunno, moved on I guess. I really didn't need emacs after I stopped reading usenet and prefer to read my email on my cell and on the web. I don't even worry about making sure I have access to a pop anymore. Its just easier to use the tools already available and ready to go than install emacs and all the modules that customize it to do what you want. Used to spend hours installing stuff like that java extension, custom mail and usenet extensions, there was an ftp extension I liked, leaning emacs lisp so I could customize extensions... I could do that for days at a time. Finally I just got tired of that and needed to do actual work. Emacs is great though.

---

### Post by vishaluc on 2010-08-07
Searching for an IDE.

---

### Post by nvteighen on 2010-08-07
Again, the de facto standard compiler used in GNU/Linux is GCC (GNU Compiler Collection), which has g++ for C++ and gcc (lowercase!) for C. Basically, use a text editor and then use the corresponding compiler in your shell.

Then, if you need an IDE to help you automate a bit the process described above and help organizing your code and such, read the stickies... Just remember the IDE is not the language, but a tool for the language.

---

### Post by FQ`9 on 2011-06-19
> **vishaluc said:**
> Searching for an IDE.

[NetBeans]("http://www.netbeans.org"), its free, and you can have a C/C++ Plugin from the repo ([http://lmgtfy.com/?q=NetBeans+IDE+JDK+Bundle](http://lmgtfy.com/?q=NetBeans+IDE+JDK+Bundle))

---

### Post by ameertawfik on 2011-06-19
You should try CDT (eclipse version for c++)
I have used codeblock, vs c++ and i find CDT better.  here is  the link to download CDT [http://www.eclipse.org/cdt/](http://www.eclipse.org/cdt/)

simple steps to setup:
1- install g++.
2- open CDT. 

CDT will use path or local variable to find g++ installation.

note: netbean has support for C++ but i have not tried it before.

---

### Post by vincegata on 2011-06-19
It's a tough question. I've been searching for a good IDE in the past several days. 

You can take a look at the link to see what's available:

[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)

Geany -- can only build your projects, the toolchain not integreated, so no built-in debugging. -- not usable as full IDE.

Code::Blocs -- limited debugging capability. --  not usable.

KDevelop -- limited debugging capability, limited support through mail list --  not usable.

NetBeans -- written in Java, a lot of features, looks terrible on Ubuntu 11.04. I've tried different "look and feel" but they do not help any. -- Not usable for my taste.

CodeLite -- usable but the interface is not consistent. It's got some weird GUI layout that's taking up screen real estate. It will be alright for dual-monitor setup. -- I am not going to use it. 

Eclipse -- a lot of features - probably all you need, written in Java so somewhat slow, crashed on me while indexing, the settings are spread out and difficult to find. The most used IDE in the world, large forum but I cannot register for its forum right now it's closed by admin, I have couple questions but cannot get answer, so I am not using it right now but I might get back to it later if I do not find anything better.

Anjuta -- I am testing it right now and looks promising but I cannot find its forum to ask questions.

Qt Creator -- using it right now for a day or two, the UI layout is different from Visual Studio but I like it so far. Try it.

---

### Post by cgroza on 2011-06-19
> **vincegata said:**
> It's a tough question. I've been searching for a good IDE in the past several days. 

You can take a look at the link to see what's available:

[http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments](http://en.wikipedia.org/wiki/Comparison_of_integrated_development_environments)

Geany -- can only build your projects, the toolchain not integreated, so no built-in debugging. -- not usable as full IDE.

Code::Blocs -- limited debugging capability. --  not usable.

KDevelop -- limited debugging capability, limited support through mail list --  not usable.

NetBeans -- written in Java, a lot of features, looks terrible on Ubuntu 11.04. I've tried different "look and feel" but they do not help any. -- Not usable for my taste.

CodeLite -- usable but the interface is not consistent. It's got some weird GUI layout that's taking up screen real estate. It will be alright for dual-monitor setup. -- I am not going to use it. 

Eclipse -- a lot of features - probably all you need, written in Java so somewhat slow, crashed on me while indexing, the settings are spread out and difficult to find. The most used IDE in the world, large forum but I cannot register for its forum right now it's closed by admin, I have couple questions but cannot get answer, so I am not using it right now but I might get back to it later if I do not find anything better.

Anjuta -- I am testing it right now and looks promising but I cannot find its forum to ask questions.

Qt Creator -- using it right now for a day or two, the UI layout is different from Visual Studio but I like it so far. Try it.
It seems emacs will fit you! :D

---

### Post by GenBattle on 2011-06-20
Eclipse would be my vote, but of course for C++ you'll need CDT (C development tools). Personally I prefer a purpose-build IDE like Code::Blocks or a text editor and compiler, Eclipse is too unwieldy for small everyday projects.

---

### Post by mourt on 2011-06-29
> **vishaluc said:**
> Can anyone suggest an alternative to visual c++ on Ubuntu?

Qt Creator. Contrary to its name also usable for "plain" C++. Probably the closest thing to the MSVC debugger you can get. For plain C++ editing, KDevelop is also pretty good.

---

### Post by trizrK on 2011-06-29
> **Newbie2910 said:**
> I programmed in C++ for years.  Now, I use C# and would not go back to C++ for anything.
Isn't C# for building Windows appliciations? 
I could be completely wrong but that's what i thought.

---

### Post by Pierrick584 on 2011-06-29
> **trizrK said:**
> Isn't C# for building Windows appliciations? 
I could be completely wrong but that's what i thought.

It is, but some people believe its cool to port microsoft's product to linux and use it, i wont argue if they're right or not, i'll just express how i find its illogical based on the simple fact that i hate microsoft and everything they make.

To stay on topic, Code::Block is definitively the best out there.

---

### Post by Dragonbite on 2011-06-29
> **trizrK said:**
> Isn't C# for building Windows appliciations? 
I could be completely wrong but that's what i thought.
To use C# in Linux, the best bet is to use Mono (framework) and Monodevelop (IDE).

Some programs you may have heard of that is written in Mono (C#) includes F-Spot, Banshee and Tomboy.

On the downside, it's future is slightly uncertain, and there are a number of people who question it's safety due to connection with Microsoft but if you look around enough you'll find the threads for and against it.  No sense bringing it all up here, except to just say that C# is primarily for Windows apps but the Mono framework brings C# to Linux.  

That and Vala (which Shotwell is written in) uses a C#-like syntax.

---

### Post by cgroza on 2011-06-29
If I need something C# like on Linux, I would go for Java.

---

### Post by nvteighen on 2011-06-30
Let's clarify: C# is a programming language that's got an internationally approved open standard (ECMA-334, ISO/IEC 23270).

It is meant to run on a VM whose specs are also part of that standard. MS calls its own implementation .NET; Mono is just another implementation. The case is very similar to Oracle's Java VM and OpenJDK's, for example.

The problem with the CLI is that the main "official" implementation is Microsoft's and that they claim "intellectual property" on some specific parts of their implementation (I think it's on the CLR, the platform-specific backend), but not on the language nor on the CLI, which is also an open standard.

In theory, they've publicly promised not to sue anyone, but who knows.

---

### Post by eric-yorba on 2011-06-30
> **Dragonbite said:**
> That and Vala (which Shotwell is written in) uses a C#-like syntax.

Yes! Anyone familiar with Java or C# could get up to speed on Vala really quickly. If you want to develop apps for the Gtk/Gnome world, it's the way to go.

---

### Post by kayosiii on 2011-07-01
I quite like KDevelop. I like the editor better than anything else I have used ([http://userbase.kde.org/KDevelop4/TipsAndTricks](http://userbase.kde.org/KDevelop4/TipsAndTricks)).
I am also really enjoying the git and subversion integration (though it is a little buggy at the moment).

Somebody mentioned support and debugging. While I agree that these are weaker areas in KDevelop, I think the picture is not as bad what was presented.

I did have problems with the first project I tried to debug in KDevelop It was a port of an existing program and was using a custom makefile. After we ported it to a nicer build system (We settled on premake4 in since the project has game console ports) the debugger worked just fine. So far debugging is better than Code::Blocks but the mechanisms are a bit non standard - KDevelop uses Tooltips with controls in them to do a lot of things. I would agree that debugging is not at as good as Visual C++ but I would call it a lot better than minimal.

As far as support goes there is also an IRC channel and forums here
[http://forum.kde.org/viewforum.php?f=25](http://forum.kde.org/viewforum.php?f=25) (the kdevelop specific forum is missing at present but the developers do seem to listen and reply on this forums.kde forum.

I would also like to note that there are other ides out there which are more similar to Visual C++ and you may be happier with one of those.

---

### Post by Dragonbite on 2011-07-01
Sounds like the people at OMG! Ubuntu had a similar question, [[COLOR="Blue"]_Ask OMG! – What are the best C++ development tools for Ubuntu? We find out!_[/COLOR]]("http://www.omgubuntu.co.uk/2011/06/what-are-the-best-c-development-tools-for-ubuntu/?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+d0od+%28Omg%21+Ubuntu%21%29&utm_content=Google+Reader")

What is interesting is the number of people that immediately jump on the lack of QtCreator in the list.

---

