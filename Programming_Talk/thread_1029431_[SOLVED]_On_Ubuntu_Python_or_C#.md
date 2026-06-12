---
title: "[SOLVED] On Ubuntu: Python or C#"
date: 2009-01-03
forum: Programming Talk
---

### Post by efexD on 2009-01-03
Well, when i was on windows all i did was pretty much C# and some C++. Coming to ubuntu i noticed people were making alot of programs in python instead. Is there any specific reason why more people use python? Or could someone explain to me the goods and bads of python and why do more people seem to use it on ubuntu than windows? Thanks for your time. :popcorn:

---

### Post by jimi_hendrix on 2009-01-03
on ubuntu you cant use ANY .Net libararies... (you can still use C# though)

people use it more because they like the simplicity...many recommend it as a starting language so people become most familiar with it...and its 100% cross platform

---

### Post by jespdj on 2009-01-03
I think this is just for historical reasons. Python is not too hard, and has always been free and open source, which makes it an obvious choice for Linux desktop applications. On Windows, Microsoft's tools have ofcourse been king, so that's why C# and .NET are used often for Windows applications.

C# is ofcourse an invention by Microsoft, and there hasn't always been a free implementation of a C# compiler and CLR available which works on Linux. There's [Mono](http://mono-project.com/Main_Page), an open source implementation of Microsoft's .NET, and some of the standard GNOME programs are written in C# and run on Mono (for example Tomboy and Pidgin, if I'm not mistaken).

MonoDevelop is an IDE for C# and Mono on Linux.

---

### Post by user_none on 2009-01-03
[QUOTE="jimi_hendrix"]on ubuntu you cant use ANY .Net libararies... (you can still use C# though)[/QUOTE]
Um... Mono is an open source implementation of the .Net framework including all of the standard libraries. It also has full or partial support for almost all of the extra libraries Microsoft ships (ASP.Net, WinForms). Not to mention that it is designed to be fully compatible with Microsoft's .Net. Meaning as long as a library or application does not use pinvoke to call a native method it will work in Mono on Ubuntu.

[QUOTE="jespdj"]some of the standard GNOME programs are written in C# and run on Mono (for example Tomboy and Pidgin, if I'm not mistaken).[/QUOTE]
Pidgin is not a standard Gnome program as far as being included as part of the "official" Gnome desktop. It is added by most ditros. Also, it is not written in C#. It is written in C. Tomboy, Banshee, and F-Spot are all written in C#.

People use Python because it's easy, it was a complete solution on Linux before Mono, and it does not come from Microsoft. There are people who refuse to touch any thing even remotely related to Microsoft.

---

### Post by efexD on 2009-01-03
So with monodevelop I can pretty much use all the .net libraries correct? If so then \\:D/
I never really liked pythons syntax, it bothers me :(

---

### Post by user_none on 2009-01-03
Monodevelop isn't required. However, it does make it easier to work with Mono. Monodevelop is just an IDE designed around Mono and C#. If you install the development packages for Mono you can compile and use .Net libraries. Monodevelop also has a handy feature where you can import Visual Studio projects into it.

Take a look Monodoc (the documentation browsing app) and [http://www.go-mono.com/docs/](http://www.go-mono.com/docs/) to see what is supported. There are a number of additional API's that Mono adds to .Net. The core API of .Net is fully provide by Mono. Check if it's already supported before importing libraries. You may not have to in a number of cases.

Also, remember that Mono is designed to be binary compatible with .Net. So anything you've compiled on Windows will work with Mono. And vise versa provided you have the relevant .dlls installed. Just remember that unlike Windows you may not be able to just double click to run the .exe that is produced. If not than mono app.exe in a terminal.

You can use pretty much all .Net libraries provided that they do not use system calls that are Windows specific. Anything that uses PInvoke is out unless you want to port those calls to a C library. Such is the case to get Paint.Net working in Mono.

Mono provides most of the libraries of .Net. Not all are fully ported. WPF for instance is not yet available. Mono's 2.0 [Release Notes]("http://www.mono-project.com/Release_Notes_Mono_2.0") have a good indication of what is fully supported.

---

### Post by efexD on 2009-01-03
Well, i've looked around and people were saying that mono had poor performance on linux... Is this true or ?

---

### Post by user_none on 2009-01-03
Compared to C (or any compiled language for that matter), Mono has poor performance. By that same comparison so does .Net. If we take this a step further C has poor performance when compared to hand crafted assembly code.

Take a look at [http://shootout.alioth.debian.org/](http://shootout.alioth.debian.org/) if you want to see how it stacks up in synthetic benchmarks against other languages. By those tests Mono is much faster than Python and a tad slower than Java (though uses far less memory).

The two things you really need to think about is run time vs programmer time and how much time is actually going to be spent computing. In most cases programmer time is more expensive and in most tasks even Python is still fast enough to finish in a reasonable amount of time.

Also, remember that the way the code is written as well as optimization features of the run time (for non-compiled languages) can change how fast a language appears to be. Take a look at [http://ubuntuforums.org/showthread.php?t=1026962](http://ubuntuforums.org/showthread.php?t=1026962) . The C++ port of the code is much slower. Using one language over another won't guarantee you're app will be faster than if you coded it in another. Most of that comes down to your abilities and what the task you want to accomplish.

---

### Post by pmasiar on 2009-01-03
If you want to be competent programmer, you should try to "extend your brain", by learning more and more different languages. Python will be easy start, but then you should look into more different languages, like Lisp, Prolog, Forth, Erlang.

And every programmer should be competent in dynamically typed language for tasks where CPU effectiveness in **not** the crucial factor - because for 90% of tasks, it is not :-) After short try, you will see that programming in dynamically typed language is much faster, and more fun. 

Try Ruby if you don't like significant whitespace - but for most people, significant whitespace is what they do anyway to have properly stuctured code, and it ceases to be a problem after about 15 minutes :-)

C# is not very popular, and likely will never be, because the mirage of MSFT compatibility requires to follow every change in MSFT strategy. Many developers prefer to lead and not to follow. And even C# is slightly better designed than Java (they learned a bit), it is not **that** better - and as I said, dynamic languages are more productive and more fun. For speed, Python + C libraries seems like better bargain.

Free software will never have single dominant language like enterprisey computing has, because developers have preferences (and don't trust marketing hype like your boss might), and projects keep the language they started.

So, there are good reasons to wander outside of your shell, be curious and learn. Then, you may want to use Python on .NET - as IronPython (which integrated seamlesly with C#, I heard). :-)

---

### Post by efexD on 2009-01-03
First off, i'm no beginner, i have ALOT of experience with C++ and i have to agree with you, It doesn't really look like C# is going anywhere so i will most likely stick with C++.

---

### Post by directhex on 2009-01-03
There's always the worst of both worlds - IronPython is Python language syntax built on top of CLR (.NET) :p

---

### Post by efexD on 2009-01-03
> **directhex said:**
> There's always the worst of both worlds - IronPython is Python language syntax built on top of CLR (.NET) :p


Haha :lolflag:

---

### Post by jimi_hendrix on 2009-01-03
> **user_none said:**
> Um... Mono is an open source implementation of the .Net framework including all of the standard libraries.

iirc when i first came here asking for C# help people said i could not use any .Net libraries...never tried it because i assumed they were correct...sorry if i am wrong

---

### Post by directhex on 2009-01-03
> **jimi_hendrix said:**
> iirc when i first came here asking for C# help people said i could not use any .Net libraries...never tried it because i assumed they were correct...sorry if i am wrong

Not *ALL* assemblies are available, and not every method in every class of those assemblies which ARE available is complete (though the newer the Mono, the better the completion). However, the majority of the gaps are better-served by Linux-native replacements (e.g. you should use GTK# or Qyoto, not System.Windows.Forms, to design a nice UI on Linux)

CLI assemblies are, in theory, cross-platform - as long as they've not been programmed to be platform-specific (due to error or intention). For example,
```

tmpdir + "\DATA"

```
is platform-specific and for Windows only, due to the hard-coding of a Windows backslash. The correct code is
```

System.IO.Path.Combine( tmpdir, "DATA" );

```

Similarly, P/Invokes are a path into system-specificness, unless the library being P/Invoked is also cross-platform (e.g. GTK# P/Invokes a native GTK+, but GTK+ is cross-platform).

It's relatively safe to assume that "framework libraries", e.g. those included with Microsoft.NET or Mono or DotGNU Portable.NET, will not be portable - but apps and libraries should be. As an example, Microsoft are the ones behind IronPython - it's tested & works on Mono, as it's cross-platform Free code. F# is not Free Software right now, but again, is cross-platform

---

### Post by jespdj on 2009-01-03
> **efeXor said:**
> Well, i've looked around and people were saying that mono had poor performance on linux... Is this true or ?
Probably, and Python is also not super fast. However, for most desktop applications this is not an issue, so don't worry about it too much (unless you're going to write an application that does heavy number crunching).

---

### Post by efexD on 2009-01-03
Hmm. Thanks for all the replies! I'm going to try python. Can anyone recommend a good IDE for making programs in it?

---

### Post by pmasiar on 2009-01-03
> **directhex said:**
> There's always the worst of both worlds - IronPython is Python language syntax built on top of CLR (.NET) :p

worst - or best? I know about a startup which was able to compete and win because IronPython is so much more productive than C# - but easy to integrate with C# and .NET calls when needed.

---

### Post by |{urse on 2009-01-03
python's cool, but i'd rather have my code compiled and run in rt than be interpreted (slow).

---

### Post by Steveway on 2009-01-03
> **|{urse said:**
> python's cool, but i'd rather have my code compiled and run in rt than be interpreted (slow).

Complete BS. A proper JIT can make your code run faster than a normal AOT can.
Take a look at Pypy, those people are doing pretty revolutionary work there.
For a "IDE" I would recommend SPE; Stanis Python Editor.

---

### Post by efexD on 2009-01-03
> **|{urse said:**
> python's cool, but i'd rather have my code compiled and run in rt than be interpreted (slow).

Interpreted doesn't always mean slow.

---

### Post by Greyed on 2009-01-04
> **efeXor said:**
> Hmm. Thanks for all the replies! I'm going to try python. Can anyone recommend a good IDE for making programs in it?

vim?  :D

Well, that's where most of my Python code is written.

If I had my druthers I'd use the professional version of WingIDE.  But it's not FOSS so a non-starter for most people.  Komodo Edit (the FOSS version of Komodo) is decent but I found myself going back to vim since it was pretty comparable.

I know Eclipse + the Python plugin is popular but I have an allergic reaction to Java apps and it just feels odd using an editor written in Java, designed for Java, to hack Python.  It's like asking your wife what would be sexy to buy for your mistress.  :popcorn:

SPE gets nods but the few times I've poked at it I've shrugged my shoulders and went back to vim.

Boa-Constructor looked promising at one time but the glacial development and the author's lack of updates from his private repository have mired it in bugs and obscurity.

---

### Post by directhex on 2009-01-04
> **pmasiar said:**
> worst - or best? I know about a startup which was able to compete and win because IronPython is so much more productive than C# - but easy to integrate with C# and .NET calls when needed.

Depends on your POV, of course ;)

One of the nice things about CLR (which Java was never designed for so does poorly) is it allows you to seamlessly and trivially mix languages. You want to write one file in C#, one in Java, one in Boo, one in Python, one in Ruby, one in VB.NET, one in F#, one in Nemerle? No problem, they'll all play nice.

---

### Post by directhex on 2009-01-04
Bah, stupid double posty nonsense

---

### Post by efexD on 2009-01-04
> **Greyed said:**
> vim?  :D

Well, that's where most of my Python code is written.

If I had my druthers I'd use the professional version of WingIDE.  But it's not FOSS so a non-starter for most people.  Komodo Edit (the FOSS version of Komodo) is decent but I found myself going back to vim since it was pretty comparable.

I know Eclipse + the Python plugin is popular but I have an allergic reaction to Java apps and it just feels odd using an editor written in Java, designed for Java, to hack Python.  It's like asking your wife what would be sexy to buy for your mistress.  :popcorn:

SPE gets nods but the few times I've poked at it I've shrugged my shoulders and went back to vim.

Boa-Constructor looked promising at one time but the glacial development and the author's lack of updates from his private repository have mired it in bugs and obscurity.

@ Vim. Yes, but don't you rather prefer code completion? It is rather useful and I couldn't see programming without it when you're making huge applications.

---

### Post by Greyed on 2009-01-04
> **efeXor said:**
> @ Vim. Yes, but don't you rather prefer code completion? It is rather useful and I couldn't see programming without it when you're making huge applications.

That depends.  I haven't really missed code completion in vim but any time I go to any of the other editors I miss loads of features from vim and the code completion don't make up for it.  Besides, in a well written application your name spaces are relatively small.  We're not talking about java.style.classes.where.you.dig.eight.deep.  In Python if you need a method from deep within the class structure you:

[php]
from python.style.classes.where.you import foo

foo(spam)
[/php]

I miss bouncing on the % key.  % matches braces and while other editors which do incorporate *some* of vim's keyset insist on putting brace matching as cntl-shift-ow-my-carpal-tunnel combo.  Same for marking.  V, move.  Done.  Block (de)indention > and < once marked.  Or >> << for a single line.  Again, all of those are some chord combo that eludes me because the 1/2 vim keyset has me thinking in vim mode.

The only thing I really miss is WingIDE's source assistant.  Having a little box pull up the definition for the current function/method as well as its doc string is awesome.  Too bad WingIDE's vim mode is worse than Komodo's and the version with SA is in the $179 version.  I'm not opposed to paying for software but $179 for one feature I like is a tad steep.

---

### Post by pmasiar on 2009-01-04
> **efeXor said:**
> @ Vim. Yes, but don't you rather prefer code completion? It is rather useful and I couldn't see programming without it when you're making huge applications.

That's the main difference between IDE and good editor:

* IDE helps you to write more lines of code
* editor helps you to refactor code easier

**edit** Of course not just any editor like notepad - real programmer's editor, like emacs, vim, MultiEdit, which is extendible and programable

So with IDE you have more lines of code which wrong - it is like measuring progress of building a plane in weight (example from Bill Gates).

---

### Post by Shin_Gouki2501 on 2009-01-04
refactorings are quite language depended, eclipse or netbeans do a nice job there or me.

 Most IDE's are highly pluggable architectures. Other important aspects are: Team Access (SVN), Database Access , etc.

---

### Post by jespdj on 2009-01-04
> **pmasiar said:**
> That's the main difference between IDE and good editor:

* IDE helps you to write more lines of code
* editor helps you to refactor code easier
Are you sure you don't have these two switched around? An IDE is supposed to understand the programming language that you're working in and might have tools for refactoring. A simple text editor isn't aware that you're writing program code (well, maybe a little bit for syntax highlighting) and doesn't have sophisticated refactoring tools.

---

### Post by wmcbrine on 2009-01-04
grep is my sophisticated refactoring tool. :)

---

### Post by Sprut1 on 2009-01-04
I came from Windows and VB.net - learning python was very easy and it is in my opinion a very powerful language. If you want a good IDE install Eclipse with the Pydev plugin, it works very well!

---

### Post by efexD on 2009-01-04
> **Sprut1 said:**
> I came from Windows and VB.net - learning python was very easy and it is in my opinion a very powerful language. If you want a good IDE install Eclipse with the Pydev plugin, it works very well!

Yup, i'm using that along with MonoDevelop for C#

---

### Post by directhex on 2009-01-04
> **Sprut1 said:**
> I came from Windows and VB.net - learning python was very easy and it is in my opinion a very powerful language. If you want a good IDE install Eclipse with the Pydev plugin, it works very well!

You could continue to write VB.NET

If you wanted to, anyway

Personally wouldn't touch it with a barge pole, but I don't like Python syntax either

---

### Post by Sprut1 on 2009-01-04
> **directhex said:**
> You could continue to write VB.NET

If you wanted to, anyway

Personally wouldn't touch it with a barge pole, but I don't like Python syntax either

I think it's less of a hassle just learning something else, as I said earlier Python wasn't hard to learn, whats wrong with the syntax? I think its quite nice :)

---

### Post by directhex on 2009-01-04
> **Sprut1 said:**
> whats wrong with the syntax? I think its quite nice :)

The major point? Whitespace sensitivity.

---

### Post by Sprut1 on 2009-01-04
> **directhex said:**
> The major point? Whitespace sensitivity.

Well that forces correct indenting, I've always indented my code correctly anyways.

---

### Post by directhex on 2009-01-04
> **Sprut1 said:**
> Well that forces correct indenting, I've always indented my code correctly anyways.

One man's "correct" is another man's "stab himself in the face"

---

### Post by Sprut1 on 2009-01-04
> **directhex said:**
> One man's "correct" is another man's "stab himself in the face"

Haha, so true - good thing we all have a choice :)

---

### Post by wmcbrine on 2009-01-04
No, it's not true in this case. If you're complaining about Python's indenting, then either you've never tried it, or your else your own preferred indentation style is extremely perverse. I don't want to see such code in any language.

---

### Post by pmasiar on 2009-01-04
> **directhex said:**
> The major point? Whitespace sensitivity.

How many years of experience you have? If you ever participated in any project (commercial or free), first thing they enforce is coding standards with proper indent. Without it, reading code is total pain and mistakes are easy to hide. I would not want to participate in a project with no coding standards - certain way to failure.

Python significant whitespace is what every standard project uses, so it is 100% non-issue.

BTW debated to death in stickies.

---

### Post by Greyed on 2009-01-04
> **jespdj said:**
> Are you sure you don't have these two switched around? An IDE is supposed to understand the programming language that you're working in and might have tools for refactoring. A simple text editor isn't aware that you're writing program code (well, maybe a little bit for syntax highlighting) and doesn't have sophisticated refactoring tools.

Actually, a "simple text editor" is not what we're talking about.  A programmer's text editor understands the language.  An IDE is a programmer's editor with other pieces of software bolted in.  That is the Integrated and Environment in IDE.  Class browser, call tips, SVN (blech) integration, embedded Python interpreter & debugger.  All of those in addition to an editor create an IDE.

---

### Post by Kilon on 2009-01-05
> **efeXor said:**
> Interpreted doesn't always mean slow.

In case of Python it means extremely slow. I have taken a deep look at some benchmarks . Python ended up being 0x to 333x times slower than C++ !!!! That really blown me away I knew that python was slow but never imagined that it was so slow. I thought it would be 10x times slower max. 

[http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python&lang2=gpp](http://shootout.alioth.debian.org/u64q/benchmark.php?test=all&lang=python&lang2=gpp)

If you go for hybrid python like ironpython or jython add 2x times at least in the slowness of python !!!

Also I have read people saying that %10 of the time you will need CPU intense processing. So that makes Python useless only 10% of the times. Well it depends how you look it.  I for instance love both graphics and audio application , but using python for anything else than a scripting engine is pretty much extremely difficult. Also I largely disagree that audio and graphics application is only 10% of the market.  

Of course you have always the option to do part of your code in C++ or JAVA or .NET and the rest in python , jython, ironpython etc. That should solve the problem of slowness at least to a very large extent. 

I have to agree that python is dead easy. Compared some java and python code and in some case the code code was 5 times less .  The code was far more readable and it took me 0 time to understand what was going on. I was very much impressed.  

I also like .NET very much. Do not give a damn that is a MICROSOFT product, as I do not see myself as crusader against MICROSOFT and other big companies. Mono project is very good effort . The only reason I picked JAVA instead is that it works really well with both UBUNTU and MACOS.

So I will advice to learn python , it is really a very useful language but you have to be aware also of the weaknesses . But do not quit C++ and C# just yet ;)

Personally I follow closely and with a very large interest the progress of jython.

---

### Post by efexD on 2009-01-05
I didn't quit C++ or C# they are my main languages, i was just wondering what was with python on ubuntu because it seemed like more people used it. But it being slower then C++ was no surprise :lolflag:

---

### Post by directhex on 2009-01-05
Be very careful citing the Shootout on Alioth - it's phenomenally biased (e.g. some languages have heavily optimized benchmark codes, others are not allowed them, and their Java test beds are unrealistic)

---

### Post by Kilon on 2009-01-05
> **directhex said:**
> Be very careful citing the Shootout on Alioth - it's phenomenally biased (e.g. some languages have heavily optimized benchmark codes, others are not allowed them, and their Java test beds are unrealistic)

Have to confess here that I have seen other benchmarks as well and still python was crawling. The trick is that the slowness in not always experienced by the user especially on dual cores and quads cores, you have to do something heavy to understand the magnitude of the problem. 

Of course I am planning on doing my own benchmark on JAVA2D with JAVA against jython. No optimization will be allowed. I have finised the benchmark in JAVA and it takes 3 sec for JAVA app to open and render on 1,6 Ghz Intel Atom processor. I am now on the process of making the jython version.  I am not expecting to see 333x slowness , but at least a 5x will be realistic.

---

### Post by pmasiar on 2009-01-05
> **Kilon said:**
> In case of Python it means extremely slow....Also I have read people saying that %10 of the time you will need CPU intense processing. So that makes Python useless only 10% of the times. Well it depends how you look it....Also I largely disagree that audio and graphics application is only 10% of the market.  
You are **so** correct in that "it depends" - because your POV is mostly irrelevant to real life :-)

Audio is **less** than 10% of the market. Most of the code written in real world are applications which access data and present them to the user, often over the web. If your app spends 90% of the time waiting for database response (which is exactly the same regardless if called from Python or C++), you have control over 10% of run time, and writing that part in C++ improves speed only 10%.

All this misunderstanding about the speed is endlessly repeated by beginners with no real experience with solving real-life problems. We call them speed kiddies, but they seems to never learn, and come back and repeat again and again "Python is slow". Unless you can prove that bottleneck is Python code (which in average real-life app is not), you are much better off develop in language with higher productivity.

Speed kiddies never learn, because they are not concerned about solving the problem, but about tinkering with some small part of the problem.

---

### Post by Kilon on 2009-01-05
You don know my POV and it will take me ages to expain it to you. Your 10% argument makes no sense since it does not proves nothing nor is it an excuse for someone to prefer python. If really audio was much less than 10% of the market as you claim  SUN would not even bother to bring a highly sophisticated AUDIO/MIDI library (JAVA SOUND API) and interface easily comparable to both JAV2d and SWING library. GRAPHICS and AUDIO is a HUGE DEAL IN THE SOFTWARE Market. Not because of the amount of apps that are made but because of both the revenue that those apps generate and the complexity of those apps.  



On the other hand I agree that It makes no sense to claim that Python will be 300 times slower than C++ because if this was true then pythons apps would be useless and none would bother supporting python. So when I saw the figures I was quite bit skeptical. And I was sceptical because I have seen some highly useful apps written in python .   

I have no physical proof that python would be slow for the things I want to make. It may or may not be. And even if this is true that does not mean that I can not greatly benefit from the ease of use of jython. Afterall I have nothing to lose I can always write part of my code in JAVA. I am planning on using jython , so I will discover for myself its limits in the matters of speed and you can be certain that I wont hesitate to share it with you. I am no speed kid or whatever you call them, just someone making his first steps in python world and want to make sure he is not wasting his time. 

And I have read something very clever in a Jython paper. A developer can easily compromise speed for ease of development. A user will always prefer speed. But the user is not always right and obviously I am a developer. I would not mind cutting in half the time it takes to finish my project. I am sure speed will not be a big issue. 

Oh by the way here is a video about python . You will find the translation in the youtube comments. It made me laugh , hope it makes you laugh too.

[http://www.youtube.com/watch?v=tyZijNRhck8&NR=1](http://www.youtube.com/watch?v=tyZijNRhck8&NR=1)

---

### Post by Greyed on 2009-01-05
> **directhex said:**
> Be very careful citing the Shootout on Alioth - it's phenomenally biased (e.g. some languages have heavily optimized benchmark codes, others are not allowed them, and their Java test beds are unrealistic)

Not to mention benchmarks, all well and good, aren't real world apps.  I have an aversion to Java applications because I find them slow, huge and wasteful.  Here's some excerpts from a message I wrote to the Debian list about 2 years ago.  The metrics have not changed much since.

>   With 2 torrents going, one a 1Gb torrent and one a 300Mb torrent **Azureus** took up **300Mb of RAM**.
...

     I went back to G3Torrent which, in its day, was a feature equivalent of Azureus but written in Python.  I couldn't find the Linux version but did find a branch (also 2 years old) called **Rufus** which did run on Linux.  Rufus on the same 2 torrents took up a grand total of **30Mb**.
...
**Wine + uTorrent** on the same 2 torrents... **10Mb**.
...
**Azureus **at nice 0 would punch my box up to a **load of 2**.  1 for it and 1 for X keeping up with its updates.  I set it to **nice 5 and I get the load down to 1** and a
semi-responsive box.
...

     **Rufus in Python** (wxWidgets as its GUI set)...  load of** mayyyybe 0.1 at nice 0**.
...

     **Wine + uTorrent...  load of 0.01**.
 ...
    
I don't believe Azureus is poorly written because all the Java apps I have
tried have the same metrics.  Tons of RAM and CPU usage, vastly more than
Python which is almost as ubiquitous.
These days I use ktorrent and not Vuze (descendant of Azureus).  The metrics on Vuze, Deluge (instead of Rufus) and wine+utorret are about the same, still.

The Alioth benchmarks suggest that the Python client should be horribly slow compared to Java while Python should be maybe 2-3 times smaller than Java.  Instead Java was far slower and larger by a factor of 10.

We could say that Azureus is coded poorly and lay fault at the programmer's feet instead of the language's.  But as I said then, and have not seen differently since, most Java applications are similarly slow and bloated.  That suggests to me that Java, while possible to code efficiently and run quickly in benchmarks, is somehow making that difficult to maintain the larger the project becomes.  Whereas Python is slower in benchmarks it appears that as the project increases in size its performance is comparatively easy to maintain.

At the end of the day, quote all the benchmarks you want.  What matters to me as an end user is not that the benchmarks tell me this language is fast and that language is slow.  What I care about is what the *applications* tell me.  I work with the applications, not the benchmarks.

---

### Post by directhex on 2009-01-05
> **Greyed said:**
> Not to mention benchmarks, all well and good, aren't real world apps.  I have an aversion to Java applications because I find them slow, huge and wasteful.  Here's some excerpts from a message I wrote to the Debian list about 2 years ago.  The metrics have not changed much since.

These days I use ktorrent and not Vuze (descendant of Azureus).  The metrics on Vuze, Deluge (instead of Rufus) and wine+utorret are about the same, still.

The Alioth benchmarks suggest that the Python client should be horribly slow compared to Java while Python should be maybe 2-3 times smaller than Java.  Instead Java was far slower and larger by a factor of 10.

We could say that Azureus is coded poorly and lay fault at the programmer's feet instead of the language's.  But as I said then, and have not seen differently since, most Java applications are similarly slow and bloated.  That suggests to me that Java, while possible to code efficiently and run quickly in benchmarks, is somehow making that difficult to maintain the larger the project becomes.  Whereas Python is slower in benchmarks it appears that as the project increases in size its performance is comparatively easy to maintain.

At the end of the day, quote all the benchmarks you want.  What matters to me as an end user is not that the benchmarks tell me this language is fast and that language is slow.  What I care about is what the *applications* tell me.  I work with the applications, not the benchmarks.

I think Azureus' main issue on responsiveness comes from its nonstandard GUI toolkit. RAM consumption is no shocker (Java apps DO eat a lot of memory), but it's that horrible toolkit that harms it. Python apps tend to use PyGTK, and are all the better for it (similarly Mono apps use GTK#, not crappy things like System.Windows.Forms)

---

### Post by igouy on 2009-01-06
> **directhex said:**
> Be very careful citing the Shootout on Alioth - it's phenomenally biased (e.g. some languages have heavily optimized benchmark codes, others are not allowed them, and their Java test beds are unrealistic)

Be very careful when someone makes allegations without providing any specific examples which could help you to judge if their allegations have any basis in fact.

---

### Post by igouy on 2009-01-06
> **Kilon said:**
> In case of Python it means extremely slow. I have taken a deep look at some benchmarks . Python ended up being 0x to 333x times slower than C++ !!!! 
-snip-

Remember in those measurements the C++ programs are probably using all 4 processor cores and Python isn't.

If the programs are forced to use just one core- [**Python :: C++**]("http://shootout.alioth.debian.org/u64/benchmark.php?test=all&lang=python&lang2=gpp")

---

### Post by directhex on 2009-01-06
> **igouy said:**
> Be very careful when someone makes allegations without providing any specific examples which could help you to judge if their allegations have any basis in fact.

[http://jeffreystedfast.blogspot.com/2008/05/debian-language-benchmarks-sumfile.html](http://jeffreystedfast.blogspot.com/2008/05/debian-language-benchmarks-sumfile.html)

Howzat?

Similarly, the Java tests use unrealistic examples (although they seem to now be offering command-line flags other than -server and -Xint, thankfully)

---

### Post by |{urse on 2009-01-08
*cough*

C is faster.

---

### Post by directhex on 2009-01-08
> **|{urse said:**
> *cough*

C is faster.

Generally, yes

But is developer time useful? There's a reason people use things like Python - if they can write 10x more functional code in the same time, at a penalty of, say, 30% slower startup time (interactive apps spend 99.9% of their time waiting for user input, actual time spent using them should make language irrelevant), is that trade worthwhile? Some would say no, others would say yes.

---

