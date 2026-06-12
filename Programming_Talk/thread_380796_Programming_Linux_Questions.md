---
title: "Programming Linux Questions"
date: 2007-03-10
forum: Programming Talk
---

### Post by nick.inspiron6400 on 2007-03-10
Hi,

I am going to give programming under Linux another try. I want to know what is the best IDE for C or C++ with:

1. A easy GUI plugin (i could never get Anjuta to work, maybe i was doing it wrong)
2. Easy to build and debugg.
3. If possible plug-ins for other languages. 

This is my final attempt with Linux programming, i get really confused and nobody answers my questions!!! (come on! for a expert it is so simple!!!

If all else fails i will go to Mono and learn C#.

Nick.

---

### Post by colo on 2007-03-10
You might want to take a look at Trolltech's Designer, coming along with Qt.

I prefer plain vim, though.

---

### Post by lnostdal on 2007-03-10
> **nick.inspiron6400 said:**
> Hi,

I am going to give programming under Linux another try. I want to know what is the best IDE for C or C++ with:

1. A easy GUI plugin (i could never get Anjuta to work, maybe i was doing it wrong)

Simple; use Glade:

```
sudo aptitude install glade-3
```

> 
2. Easy to build and debugg.

Use Scons for building and DDD or KDBG for debugging:

```
sudo aptitude install scons ddd kdbg
```

..these are all excellent tools.

> 
3. If possible plug-ins for other languages. 

I do all coding regardless of language using Emacs. I communicate with multiple interpreters and compilers, and I reach many languages (C/C++, Common Lisp, Scheme, Python, Ruby, PHP, Java, etc.) this way.

See my signature for a link to some writings about C/C++, Scons and GTK+/Glade (GUI-programming).

---

### Post by runningwithscissors on 2007-03-10
> **nick.inspiron6400 said:**
> Hi,

I am going to give programming under Linux another try. I want to know what is the best IDE for C or C++ with:
1. A easy GUI plugin (i could never get Anjuta to work, maybe i was doing it wrong)
2. Easy to build and debugg.
3. If possible plug-ins for other languages. 

Two options. Kdevelop, or Eclipse CDT for C/C++. For Java, Eclipse JDT or NetBeans.
You could also try Code::Blocks for C and C++, but I hear that it is still beta.

Of these, I think only KDevelop has a designer in which you can use Qt Widgets. Or else, you could try Glade that'll help you build forms with GTK+, but I am not sure if that is supplied as a part of any IDE.

I would still recommend using good old-fashioned text editors, gdb and a code profiler.


> **nick.inspiron6400 said:**
> 
This is my final attempt with Linux programming, i get really confused and nobody answers my questions!!! (come on! for a expert it is so simple!!!

If all else fails i will go to Mono and learn C#.

Nick.
Why "if all else fails"? Mono is good. And I hear good things about MonoDevelop too, though I've never used it.

---

### Post by Tomosaur on 2007-03-10
I'm currently suffering the inverse of this. I'm trying to get my head around C/C++ programming in Windows - the api is just horrible. I'm suffering all kinds of disgusting problems - and all I'm trying to write is a goddamn screensaver! If anyone has any decent guides or howtos on writing a Windows XP screensaver (preferably using C with OpenGL?) I'd be very grateful. I've seen one or two - but after following these tutorials I end up with lots of 'undefined references' and such - even with a straight copy+paste of tutorial code. I'm thinking the libraries have changed since the guides were written?

---

### Post by pmasiar on 2007-03-10
> **nick.inspiron6400 said:**
> This is my final attempt with Linux programming, i get really confused and nobody answers my questions!!! (come on! for a expert it is so simple!!!

I am not sure why you wrote this. We all here are free volunteers and nobody owes you anything. All help we provide is in our free time. So maybe to get better answers, you need to learn [how to ask questions ](http://www.catb.org/~esr/faqs/smart-questions.html) smarter way.

For instance you did not provided any background. Did you tried to learn programming by yourself? Which languages you tried, which books you used? My [ESP](http://en.wikipedia.org/wiki/Extra-sensory_perception) sensors do not show anything :-) - Come on experts, does anyone has better luck using ESP on Nick? :-)

My advice for a beginner as  first language to learn is Python. It is substantially simpler to start with  than C++/Java/C# because there are no "type nazis" checking proper types and blowing off your code, has flexible data structures, and best of all, has shell mode, where you can define variables and try them, and see results immediately. You can even import modules, instantiate objects, and try them. All in Python shell, writing and testing your code one line at a time, one method at a time.

see [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) to start learning Python

> If all else fails i will go to Mono and learn C#.

Well I am not sure how much better you will be off with C# and Mono. Do they have better, more friendly help community? Do they have more free documentation online? Simpler API to learn?

I just don't think so, but if C# and mono work better for you - all the better. It is nothing which will diminish my pleasure from free software or Ubuntu or Python or anything. Do what is best for you, be grateful for any free help you get, but do not expect miracles - learning programming is hard work to train *your own mind*, nobody can do it for you.

Good luck

---

### Post by nick.inspiron6400 on 2007-03-11
Well if i cant even get a IDE to work. When Visual C# 2005 works all the time, then maybe C# is the way to go. So far Mono has been the only IDE that has worked!!!

---

### Post by laxmanb on 2007-03-11
And you already posted a question about a netbeans book... so I guess you're learning Java... why not do some development in Java... it's GPL now, and all distros will include it within this year... 

just set the default L&F as GTK and you won't feel *much* of a difference between that and native apps...

and the Netbeans' GUI Builder rocks!!

otherwise, Python/C++ are the most 2 important languages for native linux development...

PS: so you have an Inspiron 6400? cool!! I'm getting one too!!

---

### Post by j_g on 2007-03-11
> C/C++ programming in Windows... end up with lots of 'undefined references'

Let me guess. You're trying to use "lowest common denominator" tools (like GCC or Ming) on Windows? Bad choice. Get yourself a Microsoft dev tool and you'll find those "undefined references" go away as soon as you install the tool.

When you use "lowest common denominator" software, then you're asking for major headaches.

I've written a bunch of screensavers with MSVC. No problem. It comes bundled with a full set of includes and libraries for the Win32 API, and it's IDE knows how to find the location of such without requiring the enduser to set environment variables (which is NOT the way to do things on Windows).

---

### Post by Tomosaur on 2007-03-11
> **j_g said:**
> Let me guess. You're trying to use "lowest common denominator" tools (like GCC or Ming) on Windows? Bad choice. Get yourself a Microsoft dev tool and you'll find those "undefined references" go away as soon as you install the tool.

When you use "lowest common denominator" software, then you're asking for major headaches.

I've written a bunch of screensavers with MSVC. No problem. It comes bundled with a full set of includes and libraries for the Win32 API, and it's IDE knows how to find the location of such without requiring the enduser to set environment variables (which is NOT the way to do things on Windows).

Thanks for the tip, I'll give it a go.

---

### Post by j_g on 2007-03-11
Just a followup. Microsoft takes developer support very, very seriously. They'll do just about anything to make it easy for developers to write Windows software. In order to promote NET, they have been giving away the express versions of VB, C++, C#, and J# NET developer environments for free. That's right. You can download and use those tools for free. (I've personally used the C# and VB freebie versions).

[http://msdn.microsoft.com/vstudio/express/downloads/](http://msdn.microsoft.com/vstudio/express/downloads/)

Also, you should download the lastest "Software Development Kit" (SDK) for all the latest includes and libs compatible with these development environments.

Why develop Windows software using Linux ports that are primitive, incomplete environments, not well-integrated with the Windows API, unintuitive, and you can't get good support/help/docs for them, when you can get free stuff from MS that gives you what the other tools lack?

---

### Post by tht00 on 2007-03-11
Meh.  VS was nice in some aspects.  I learned how to program in VB6, and it was excellent to be able to throw a GUI together and just run it.  Next, I toyed with VC++6 to learn C++, never any GUI there.  That was all back before my Linux days.

Anymore, I've just been using gedit and the command line for building apps -- Java, C++, and I've been toying with Python (though, it might be worth mentioning that I don't use Windows anymore).  I've found it about the fastest method I've used yet.  I do miss the breakpoint/walkthrough system that VS offered though.  I'll have to dig into some of the debugging utilities available in Linux.

Back to the OP, I haven't found a 'good' IDE for Linux, though, I haven't toyed with many.  I guess I've also become a bit of a purist -- I like to write all my own code rather than having it auto-generated.

Really, you can do _very_ well without an IDE.  It can take a little getting used to, but I think it's worth it. ;)

---

### Post by lnostdal on 2007-03-11
Tomosaur: 
You'll get undefined references using any compiler (well, linker really) regardless of OS if you're not linking with the correct libraries/binaries.

Getting OpenGL up and running under Windows using GCC is not a problem.

(note that I have zero interest in discussing MS vs. GNU/Linux with you, j_g .. this post is from me to Tomosaur or anyone wanting help with Linux and/or GNU-related questions exclusively)

edit:
tht00: For debugging of C stuff KDBG and DDD (both are frontends to GDB) are great. Remember to have the compiler generate extra debug-info; debuggers give you way more useful info that way.

---

### Post by pmasiar on 2007-03-11
> **j_g said:**
> Just a followup. Microsoft takes developer support very, very seriously. They'll do just about anything to make it easy for developers to write Windows software. 

or more exactly, they take care about Windows market share very seriously, creating "standard de facto" products without regard of any relevant standards. 

> In order to promote NET, they have been giving away the express versions of VB, C++, C#, and J# NET developer environments for free. That's right. You can download and use those tools for free. (I've personally used the C# and VB freebie versions).

more exactly: when facing rising popularity of F/OSS tools, free Java SDK and Eclipse, they were forced to counter it by free (as beer) .NET tools. It was no "love towards developers" involved - just marketing trick to keep developer's mindshare.

> Why develop Windows software using Linux ports that are primitive, incomplete environments, not well-integrated with the Windows API, unintuitive, and you can't get good support/help/docs for them, when you can get free stuff from MS that gives you what the other tools lack?

j_g, why you waste time preaching Microsoft gospel to users of "primitive" free software? For us, freedom to tinker, freedom to look how it is done, freedom to change it if we feel so is as important as integration to API. I am ready to work around  deficiences in free software (often I report it as a bug, and promise is made to fix it in next release) which maybe is not *yet* in some aspects 100% comparable with proprietary software - but if we all share our efforts and keep improving free software, it will be better than any proprietary offerings. 

Free is not about the price - it is about freedom.

I was trying to learn monstrosity as VS - and it was not easy. In some cases, I can clearly see disregard of VS developers about me, the user. They clearly thought: "it sucks, we know it, but it is good enough for you - we don't have time to make it better now, you will have to wait 2 years and then we will fix it - and you have good reason to upgrade". Over-complicated cluttered menus, non-intuitive functions, and you can waste hours trying to find parameters to customize it. 

j_g: IMHO it is exactly for what you,criticized about SPE [here](http://ubuntuforums.org/showpost.php?p=2281375&postcount=4) and [here](http://ubuntuforums.org/showpost.php?p=2262563&postcount=3). Do you like more functionality if it is in proprietary software like VS, which you learned long time ago, and you like your free software plain and primitive? And you do not see contradictions?

And obviously free software is not well-integrated with Windows API and will never be: (1) main focus is to make it well integrated with free software, GNU/Linux (2) even Microsoft itself was not able to release Windows API, even when required by EU commission. How can free software developers, without access to sources, even dream of doing it? And again, if they can, why they would want to?

I am not saying that free software is perfect in every aspect - but I am saying that free software is good enough to use in most cases, is getting better every day, and if something is done right, it will stay that way, and is not changed in next release on a whim from marketing.

It seems to me that I am interested to increase mindshare of free software developers, and I would prefer that the brightest and most talented developers will work in enhancing free software. Are you, j_g, concerned about keeping mindshare (and market share) of developers using proprietary tools? Or am I mistaken?

---

### Post by runningwithscissors on 2007-03-11
> **j_g said:**
> Why develop Windows software using Linux ports that are primitive, incomplete environments, not well-integrated with the Windows API, unintuitive, and you can't get good support/help/docs for them, when you can get free stuff from MS that gives you what the other tools lack?
Because MS dev tools aren't free for commercial development purposes. 
And you must be joking if you think that the Windows API is comprehensible. Maybe at the higer levels of C# class libraries. But one look at unwrapped COM or Win32 will make you sick.

---

### Post by Ergo on 2007-03-11
If development and projects in Windows are familiar to you, then try KDevelop.

[http://ubuntuforums.org/showthread.php?t=273088&highlight=kdevelop](http://ubuntuforums.org/showthread.php?t=273088&highlight=kdevelop)

This link explains better than I can.  I used this back when I was learning C++ in college.  The school was using .NET framework 1.1.  I wanted to use open source.  They didn't care, so I used KDevelop.  I found it a complete surprise when they looked and more or less acted alike!

---

### Post by j_g on 2007-03-11
This is not a forum to argue about Microsoft's policies (but I do disagree with your depiction of them). All I care about is the quality of the tools. You can scream and stamp your feet all you want about the politics of open source versus commercial software, but the bottom line is the usability and efficiency of the software, and for as much as some Linux advocates want everyone to believe otherwise, MS tools are among the most widely chosen, used, and highly regarded dev tools among developers. This is due entirely to the usability, efficiency, completeness, and general quality of those tools, as demonstrated to people who really use those tools (rather than people who merely claim to use those tools, but obviously have not developed any Windows software that any Windows users would want to use -- like Inostdal. Hey, maybe he knows about Linux development, and is helpful here. I'm not suggesting otherwise. But when to comes to Windows, his "advice" is just not helpful to a developer, especially a newbie Windows developer. I've written lots of programming tutorials for Windows developers, and even won some awards for them. And frankly, I don't consider his advice about Windows development to be based upon any notable, practical experience, and therefore, not good).

Granted, this is also not a good forum for a guy to post about problems with Windows development, but for example, when a guy is having the most rudimentary trouble compiling a Windows screensaver, you do _not_ tell him to go out there and get some Linux dev tool port that is already what he's tearing his hair out over. This is a disservice. The ostensible intent is to promote open source software, and undoubtably Linux development, but it actually backfires because all it does is convince people that Linux stuff is hard to use and "sucks". You should be recommending open source alternatives only when they are actually better for the recipient. And if they aren't, well then, it's the responsibility of the maintainer to either improve his offering to compete, or stop targetting his offering to people like newbies or Windows developers (who would be much better off with something else designed for them).

I, of all people, am certainly in favor of improvement to Linux dev tools (because frankly, I think that a lot of them, and in particular a lot of the ubiquitous ones like autotools, are drastically in need of improvement, redesign, and/or replacement with better alternatives). But I'm not going to lie to some newbie Windows programmer and tell him that it's best for him to use this stuff. It isn't. Even if I were to lie to him, he's going to eventually find out that I deliberately misrepresented the usability of those tools over the competition. And that's going to backfire. Learn from history. Overzealous Amiga advocates oversold the Amiga, and as soon as people realized that, it died. Then OS/2 advocates did the same with OS/2. The same policy ain't going to work with Linux either. History has already shown that it backfires.

By all means improve the tools. But don't live in a vacuum. Take a realistic, practical look at the competition. Don't just load Visual C++ into Wine, poke around, and then pretend to know how usable it is. Actually develop Windows software that Windows endusers will use. Then, take your own alternative and compare its usability to that. How does it stack up? Does a newbie programmer find it as easy to setup and use? Is it as intuitive? Does the enduser find that he can use it without needing to seek a lot of assistance from others (especially about the most rudimentary aspects of using the offering)? Does it do specific tasks as well as the competition? If not, don't oversell it, or target it to a clientele for which it is not as good as the alternatives. That will only backfire.

Hell, I've actually recommended others software over my own in cases where someone asks me about some aspect of my tools, and I deduce that for what he's trying to do, my tool isn't geared for him and something else is better suited to him. Some of you Linux folks need to actually get out into the real world and learn why MS dev tools are so widely used and highly regarded. You go out there and tell Windows developers that it's all because MS is an "evil entity" and has nothing whatsoever to do with the usability and quality of the stuff, and those developers are going to just roll their eyes and think "oh god, not another Linux kook I have to listen to", and that just makes things bad for everyone who is using Linux. Don't do it.

---

### Post by j_g on 2007-03-11
> look at unwrapped COM or Win32 will make you sick.

Hasn't made me sick at all. Not at all.

[http://www.codeproject.com/script/articles/list_articles.asp?userid=88625](http://www.codeproject.com/script/articles/list_articles.asp?userid=88625)

I actually find it easier than Corba and Bonomo.

---

### Post by runningwithscissors on 2007-03-12
> **j_g said:**
> Hasn't made me sick at all. Not at all.

[http://www.codeproject.com/script/articles/list_articles.asp?userid=88625](http://www.codeproject.com/script/articles/list_articles.asp?userid=88625)

I actually find it easier than Corba and Bonomo.
I know that CORBA is insanely complex, but as far as usage on desktop apps goes, we have a better system for IPC now (dbus). KParts blows any other component embedding system out of the water, but I'll sadly concede that it can't be used in commercial apps. However, OLE is not any easier to use than Bonobo (which is indeed, rather nasty).

---

### Post by Wybiral on 2007-03-12
> MS tools are among the most widely chosen, used, and highly regarded dev tools among developers. This is due entirely to the usability, efficiency, completeness, and general quality of those tools

"entirely"

???

I think they're more widely used due to the fact that developers like to hit wider targets, not because the tools are better.

Even when I did program on windows I used GCC based tools like code::blocks and dev-c++ more than MS tools (partly because they are free, but even when offered MS-VC++, I still opted for GCC)

Tools are tools... If you know how to tune a guitar by ear you wont have to rely on a tuner every time you need to play. Dev tools are the same. Maybe not for other languages, but for C/C++, if you fully understand the processes of compiling, assembling, and linking then you are usually set. Then all you need to know are the individual libraries and API's you're using.

I've yet to run across any "tools" that are just so amazing that they can do anything that I can't do by hand. And before you say "why do it by hand if you don't have to" I will say "because it doesn't take that much time, I can type out a Makefile in the time MS-VC++ takes to load and open a project"

I'm not saying that those tools suck or that microsoft is an "evil entity", I'm just saying that you don't really need those tools if you know what you're doing.

And to any newbies... Learn the process of compiling first. Don't just learn some specific IDE or development tool... Learn what is really going on so that you can program independently of that specific IDE.

That makes more sense to me than allowing yourself to become dependent on one tool.

Portability is also an issue for me...
GCC is available for most platforms...
VC++ is **_[COLOR="Red"]NOT[/COLOR]_**...
I'll choose GCC.

---

### Post by j_g on 2007-03-12
> we have a better system for IPC now (dbus).

Wait a minute. You complained about how hard "unwrapped COM" was. So I show you a series of articles I wrote about using COM in plain C that demonstrate how you can do anything with it from a language that doesn't even have objects. Now you cite dbus which can't even be used "unwrapped" unless you use the "low level API", and here are the first two sentences of the documentation at [http://dbus.freedesktop.org/doc/dbus/api/html/index.html:](http://dbus.freedesktop.org/doc/dbus/api/html/index.html:)

> This manual documents the low-level D-Bus C API. If you use this low-level API directly, you're signing up for some pain.

The second sentence is even emphasized in bold.

The dbus documentation mentions "wrappers" for the API and says "These wrapper libraries are the API most people should use".

If you don't want to use wrappers, why on earth would you use dbus??? (Not that I necessarily think that wrappers are a bad thing. I'm going on your supposition that they are. On the other hand, I've yet to see a series of articles equivalent to the ones I've written on COM. Does anyone actually use dbus in C _without_ the GLib wrapper?).

Come on now. I'm all for seriously discussing the merits/disadvantages of various options, but I definitely do not think that wrappers is a legitimate criticism of COM, especially given that Linux is inundated with wrappers for various things, and in particular dbus recommends it.

In any event, I think that COM's transparent remote access via proxy stubs is easier than dbus' insistence upon making an app come up with a specific path to the remote instance (ie, this Address -> [Bus Name] -> Path -> Interface -> Method thing ain't what I'd call transparent).

> KParts blows any other component embedding system out of the water

It looks like a C++ only version of one small aspect of COM, IOleTarget. It's hardly an alternative to COM because it doesn't do all that COM does. (ie, It looks like QT's version of OLE, but restricted to a specific language unlike COM).

> OLE is not any easier to use than Bonobo

OLE is obsolete. It was replaced by COM, and OLE became just a few COM objects (such as IOleTarget). Most of what COM is used for has nothing to do with embedding controls, but rather automation and scripting.

P.S. I don't find Bonobo particularly difficult. I just don't find it to be as easy and flexible as COM.

---

### Post by j_g on 2007-03-12
> they're more widely used due to the fact that developers like to hit wider targets, not because the tools are better.

That's illogical. Many other dev tools are available on Windows, and you yourself cite specific examples of ported Linux tools. And yet, the overwhelming majority of Windows developers choose MS tools. They are choosing them because of the usability and overall quality of the tools compared to the competition. MS simply has some of the best developer support out there. They have to. They know they need it to be #1. They don't tell developers, "just learn to use some really, really convoluted tools like autoconf from a command line", because then they wouldn't be #1. So they instead say "Try this integrated package that takes you from writing your source to creating an installation file of the finished product, all without needing to ever do anything as primitive and cryptic as typing:

AC_CONFIG_FILES(
  [tests/aclocal-${APIVERSION}:tests/aclocal.in],
  [chmod +x tests/aclocal-${APIVERSION}],
  [APIVERSION=$APIVERSION]) 

(NOTE: Just one quick, typical, actual example from the automake docs).

If you want to be #1, that's what you have to do. If you want to be #2, don't do it.

---

### Post by runningwithscissors on 2007-03-12
> **j_g said:**
> Wait a minute. You complained about how hard "unwrapped COM" was. So I show you a series of articles I wrote about using COM in plain C that demonstrate how you can do anything with it from a language that doesn't even have objects. Now you cite dbus which can't even be used "unwrapped" unless you use the "low level API", and here are the first two sentences of the documentation at [http://dbus.freedesktop.org/doc/dbus/api/html/index.html:](http://dbus.freedesktop.org/doc/dbus/api/html/index.html:)



The second sentence is even emphasized in bold.

The dbus documentation mentions "wrappers" for the API and says "These wrapper libraries are the API most people should use".
Despite that doom and gloom warning, have a look at a simple tutorial for executing and supplying callable methods using only libdbus.

[http://dbus.freedesktop.org/doc/dbus/libdbus-tutorial.html](http://dbus.freedesktop.org/doc/dbus/libdbus-tutorial.html)

And form your examples, the one to do the same with COM:
[http://www.codeproject.com/com/com_in_c1.asp](http://www.codeproject.com/com/com_in_c1.asp)

Granted that neither approach is very attractive or ready for immediate use with an application unless you're writing a set of saner bindings, I think the dbus example is nicer.

> **j_g said:**
> It looks like a C++ only version of one small aspect of COM, IOleTarget. It's hardly an alternative to COM because it doesn't do all that COM does. (ie, It looks like QT's version of OLE, but restricted to a specific language unlike COM).
It only does the component embedding part of COM. And compared to Bonobo or OLE, it is definitely far better.

> **j_g said:**
> OLE is obsolete. It was replaced by COM, and OLE became just a few COM objects (such as IOleTarget). Most of what COM is used for has nothing to do with embedding controls, but rather automation and scripting.
Didn't know that OLE has been put out to pasture. When I last tried to understand C  programming on Win, it was still about. 

So was the C API for Win32 (which has since been buried under nicer interfaces), where creating a window is an exercise in frustration. And I say that after having used Xlib for the same purpose.

> **j_g said:**
> P.S. I don't find Bonobo particularly difficult. I just don't find it to be as easy and flexible as COM.
Perhaps. Maybe I am biased because I never really understood programming on Windows, or I was just young and not as experienced when I last tried it.

I do write C# code on Windows at work, however. And it's not a bad language.

---

### Post by lnostdal on 2007-03-12
It would be useful if anyone had any actual questions here. Your ranting and FUD about how "it is not feasible to use GCC etc. on Windows" isn't getting anyone anywhere, j_g. I am definitively not paying attention.

*shrrug* Doing OpenGL in a screensaver-context on Windows using GCC and "Linux"-tools is _trivial_ ...

---

### Post by j_g on 2007-03-12
Well actually, the two examples don't quite do the same thing. There's a matter of the app being able to actually discover the location of the object without needing to know its location ahead of time (ie, not having a "location" hard-coded into the program), handling potential object name collisions, standardized version checking, dealing with multiple clients, reporting errors between clients, etc. None of this is specified in that dbus example. But aside from that, I have a big problem with this code:

```
// loop, testing for new messages
while (true)
{
...
   if (NULL == msg)
   { 
      sleep(1); 
      continue; 
   }
...
}
```

This is known as a "busy-wait loop". Unless you're doing realtime critical stuff, this should _never_ be done on a pre-emptive multi-tasking system. And it surely should not be done in a situation where you may be processing communication between networked machines (which typically is a time-consuming process). This is a performance killer.

dbus lacks the ability to allow a process to stop running and wait for a given "signal" that another process wants an operation performed???

The other problem I have is with the exit() instructions. They bypass needed cleanup (for example, who is freeing that conn handle and msg?), and of course, terminate a process without any hope of error recovery.

I should hope that this is not meant to be a functional example of dbus, because it is seriously flawed in terms of performance constraints, memory leaks, and error handling.

> creating a window is an exercise in frustration.

The "right" way to do it is to use MS dev tools. You use the GUI builder to create a "dialog" with all the controls in it. You save it to your RC file, and it gets linked into your EXE. Then you just call CreateDialog (instead of DialogBox) to present the window (and its controls), and specify your message handler for it. You don't build up a window a control at a time by calling CreateWindow (although technically, you can do it that way). That would be like X windows.

Under the hood, this is what languages like VB net and C# do when creating their "forms".

---

### Post by j_g on 2007-03-12
> Your ranting and FUD about how "it is not feasible to use GCC etc. on Windows" isn't getting anyone anywhere

Doctoring others' quotes again, I see. Feisibility isn't the issue. Lots of things are possible if you expend enough energy and time. But that doesn't mean it's worth expending that energy and time when an easier, more efficient, and better integrated option is available.

But just for the record, your undemonstrated claims about what's best for new Windows programmers aren't helping anyone here either. In fact, as an experienced Windows programmer, I think your simplistic, nebulous advice to Windows programmers is bad.

---

### Post by Tomosaur on 2007-03-12
Please guys, chill out.

j_g, I have used MSVC in the past - the reason I stopped using it, (granted, I DID stop using Windows in favour of Linux, but that wasn't 'THE' reason) was because I generally don't get on well with IDEs at all. I prefer the text editor / compiler approach in all honesty, it just suits me better. I'm not averse to using it again, I just would rather make minimal use of an IDE. In any case, the problem certainly seems to be the libraries I was using. I am downloading the Windows SDK as I type, so hopefully that'll sort this mess out.

To those arguing about Windows vs Linux development - you'd do well to remember that they're two completely different platforms, thus have different requirements. I personally dislike the Windows API, it just seems ugly to me. If I spent more time with it, I may get over this, but I haven't yet, and I have no immediate requirement to do so, apart from this little project. In any case, it makes perfect sense to use Microsoft's tools over third-party tools. MS know their platform better than anyone, so it seems perfectly reasonable to me that they would be able to get the most out of it with the minimum of fuss. For apps tailored specifically to Windows, I see no problem not to use MS tools. If you have an anti-Microsoft stance, then fine, don't use MS tools, nobody's forcing you. If, on the other hand, you can understand that, given the nature of Windows - MS is the company most likely to release tools to facilitate the development of stuff FOR Windows, then by all means, you may aswell just use MS tools. Linux has no central organisation, you're free to poke around and do pretty much whatever you feel like. That suits a lot of us, others find it annoying. There's no point in arguing over it, since it's not going to change. Windows is a propietary, closed product, thus it's in Microsoft's interests to make development as easy as possible. Linux is an open, community driven, fluid project. No organisation has that much of an interest in attracting developers. That may be good, or bad. There certainly seem to be no shortage of developers on Linux - the only 'deciding factor' in these arguments is, when it comes down to it, commercial success. It's no secret that if your only interest in development is making money - you're better suited to Windows. I don't think anybody here is going to argue with that.

---

### Post by lnostdal on 2007-03-12
j_g: 
Here is an example:

[IMG]http://nostdal.org/~lars/programming/c/mingw/screensavers/Screenshot-WinXP_SP2-1.png[/IMG]
[IMG]http://nostdal.org/~lars/programming/c/mingw/screensavers/Screenshot-WinXP_SP2-2.png[/IMG]

(this is WinXP SP2 under vmware-player)

Here is the code:
[http://nostdal.org/~lars/programming/c/mingw/screensavers/](http://nostdal.org/~lars/programming/c/mingw/screensavers/)

Now please go away, or at _least_ stay away from me and/or my posts/claims. You're stealing my time and your MS FUD is annoying and tedious.

edit: if preferred i could also have cross-compiled this ..   (mingw on linux can produce Windows "exe"-files)

---

### Post by runningwithscissors on 2007-03-12
> **j_g said:**
> ```
// loop, testing for new messages
while (true)
{
...
   if (NULL == msg)
   { 
      sleep(1); 
      continue; 
   }
...
}
```

This is known as a "busy-wait loop". Unless you're doing realtime critical stuff, this should _never_ be done on a pre-emptive multi-tasking system. And it surely should not be done in a situation where you may be processing communication between networked machines (which typically is a time-consuming process). This is a performance killer.

dbus lacks the ability to allow a process to stop running and wait for a given "signal" that another process wants an operation performed???

That is because there is no standard event loop for use on Unix apps. So it has to make do with whatever event loop is being used. Since dbus is mostly designed for use with desktop apps, it uses the event loops provided by them. And most graphical apps do provide those. Glib being one.

> **j_g said:**
> The other problem I have is with the exit() instructions. They bypass needed cleanup (for example, who is freeing that conn handle and msg?), and of course, terminate a process without any hope of error recovery.
That is a small example and also, resources are reclaimed on the termination of a process by any sane OS. Yes, it is cleaner to handle exit signals and move back up to main freeing all resources in the process, but for a small example like this, it's all right to terminate on exit.

> **j_g said:**
> I should hope that this is not meant to be a functional example of dbus, because it is seriously flawed in terms of performance constraints, memory leaks, and error handling.
It's not.

> **j_g said:**
> The "right" way to do it is to use MS dev tools. You use the GUI builder to create a "dialog" with all the controls in it. You save it to your RC file, and it gets linked into your EXE. Then you just call CreateDialog (instead of DialogBox) to present the window (and its controls), and specify your message handler for it. You don't build up a window a control at a time by calling CreateWindow (although technically, you can do it that way). That would be like X windows.
Not in the case of a bare-bones window that will only hold an opengl context. Which is the reason for using Xlib in the first place. For a regular GUI application, you'd use a proper widget toolkit.

> **j_g said:**
> Under the hood, this is what languages like VB net and C# do when creating their "forms".
Obviously.

---

### Post by pmasiar on 2007-03-12
> **j_g said:**
> This is not a forum to argue about Microsoft's policies (...). All I care about is the quality of the tools. You can scream and stamp your feet all you want about the politics of open source versus commercial software, but the bottom line is the usability and efficiency of the software,

You are absolutely right. This is forum dedicated to help Ubuntu programmers resolve issues related to programming in Ubuntu, to promote Ubuntu and help fixing [Bug #1](https://launchpad.net/ubuntu/+bug/1). All we care here is free software, and how to make it better than proprietary software. You can scream and stamp your feet all you want about how much more beginner-friendly is GUI of some proprietary program - but the bottom line is [four freedoms of the user](http://www.gnu.org/philosophy/free-sw.html). :-)

j_g, you are missing one important part: we, advocates of free software, are willing to work with programs which might be today little less user friendly or temporarily lack some advanced features of proprietary programs - because we care about freedom. And we know that with time, all those bugs will be fixed, given enough developers. And to have more and smarter developers than Microsoft has is one of the goals of this forum.

:-)

Look at Eclipse: it is about as advanced as Visual Studio. And it is entirely free, and thousands developers are adding plugins to it, and it is inevitable that after some time it will be better than VS, and free, and MS will switch to it (or something similar). Borland did it. Can you imagine that in the future, MS will be selling not whole VS, but just plugins for Eclipse? Because it would not make sense to spend money to develop and maintain features which Eclipse provides for free.

Commoditization of basic software is inevitable (MS did it to personal computer industry), and free software is perfect commodity. 

And you again bring red herring - "commercial software". Free software can be commercial - Red hat does it, Canonical does it. Dichotomy is not between "open source" and "commercial" - non-free is software which does not provide basic freedoms (one of which is access to source).

j_g, you are experienced expert. Please visit FSF website, learn what GPL really means, do not repeat propganda regurgitated by some misinformed journalists about "open source" being agains commercial software. You are smarter than that, you can learn how really it is, if you want to learn it.

> and for as much as some Linux advocates want everyone to believe otherwise, MS tools are among the most widely chosen, used

No, I agree with you - that is exactly the bug #1 which we want to fix :-)

> and highly regarded dev tools among developers. This is due entirely to the usability, efficiency, completeness, and general quality of those tools

Don't get me started. I can write pages how I struggled with using VB.NET and .ASP. VS is as hard to learn, unintuitive, with obscure menus etc as any other complicated piece of software - maybe even more, because it is inflicted on other people. For free software tools, because they are *used* by authors, authors fix most glaring usability bugs. For VS, it does not happen that easy. But enough about VS.

> like Inostdal. Hey, maybe he knows about Linux development, and is helpful here. I'm not suggesting otherwise. But when to comes to Windows, his "advice" is just not helpful to a developer, especially a newbie Windows developer.

It is not relevant. Developer who came here for advice is someone who uses, or plans to use, Ubuntu. So even on windows, it makes more sense to learn tools and skills which she can later reuse on Ubuntu, advancing free software. So windows-specific help using proprietary tools is last resort only. Our goal is promote free software and gain users to our cause. If Microsoft wants to gain developer's mindshare, Ubuntu forum is very bad place to do that, and I do not see why anyone from us should be helpfull in it. After all, Microsoft is main obstacle to world domination of Linux, no? :-)

> all it does is convince people that Linux stuff is hard to use and "sucks". You should be recommending open source alternatives only when they are actually better for the recipient. 

Even if the free software is not superior to proprietary now, I still believe it makes more sense in most cases to learn using free tool. (1) you can easier transfer your skills to other workplaces - because you do not have to ask for money to buy it at new job (2) you learn how to use it, how you could improve it, and either fix bugs yourself, or suggest improvements to developers, and pay favor in return by improving docs, or helping new users or something. (3) saved money can be contributed to something more important (to user) than MS profits :-) I believe that is better in most cases for the recipient to learn use free tools.

> Take a realistic, practical look at the competition. Don't just load Visual C++ into Wine, poke around, and then pretend to know how usable it is. Actually develop Windows software that Windows endusers will use. 

Why would I recommend anyone to do that? I recommend learning to use free tools, and developing better software what anyone can use, not only people who can afford to pay for Windows. I do not want wasting my time learning something with will become inferior in my lifetime - my mind capacity is limited, I go for becoming expert user of free tools.

> and those developers are going to just roll their eyes and think "oh god, not another Linux kook I have to listen to"

OK deal: if you will not call me 'linux kook", I will not call you "[astroturfing](http://en.wikipedia.org/wiki/Astroturfing)  MS-owned and paid shill" :-) Sounds reasonable?

BTW thank you with helping on some other threads - j_g, you are obviously expert programmer and when talking about technical issues, you know your stuff. But please understand one thing:

We are Ubuntu users here. We want to learn to use free tools which Ubuntu makes available, to make Ubuntu the best Linux distro around, and fix Bug #1. Part of it is gaining mindshare between developers, experienced and new. Promoting Microsoft is not helpfull. We know that some tools are not *YET* :-) as good as microsoft sells, but we are willing to learn ways around it, and we promise (someone will) fix it. We often value the freedom more than convenience - because we have fun improving our tools. With enough eyebulbs, all bugs are shallow. If you want to join, you can help us to make free software superior to proprietary. if not, you are still welcomed to hang around and answer technical question, but if you will continue promoting non-free software, you will get flames again. We all have bias -- for free software -- and we like it that way.

---

### Post by laxmanb on 2007-03-12
please... stop this frivolous discussion - it has no use... 

a. Visual C++ is not a good solution to build complex GUI programs for Windows anyway... so I don't even know where that came into the picture anyway... 

b. The question was about linux programming...

PS: Microsoft dumping VS in favour of Eclipse... a bit too much wishful thinking?

---

### Post by pmasiar on 2007-03-12
> **laxmanb said:**
> a. Visual C++ is not a good solution to build complex GUI programs for Windows anyway... so I don't even know where that came into the picture anyway...

j_g said that VS is better than anything Linux has, and everyone who disagrees is a clueless Linux kook. It turned on my preaching mode... :-)

> PS: Microsoft dumping VS in favour of Eclipse... a bit too much wishful thinking?

Obviously not in next 5 years. But 20 years from now, when   adding all the Eclipse features which thousands of capable developers will keep adding to plugins will became too expensive, MS will have no other option. I remember when Borland was selling the best IDE for C. Now IIRC Borlands sells plugins for Eclipse. If not now, soon will. It is very hard to compete with free (as beer) tool, if free is good enough. I am patient, and Linux, Eclipse and other free software is not going to disappear any time soo, i hope. It is just matter of time - plan to take over the world progresses as expected :-)

---

### Post by j_g on 2007-03-12
> Why would I recommend <that authors of developer tools spend some time using MS tools>?

Because MS tools are the most widely used and respected dev tools for PCs. It behooves any software developer of dev tools to get to know how they work so you can see why so many people choose those tools, and incorporate its selling points into your own offerings.

A case in point, I developed a complete REXX development environment for Windows. There were already several REXX interpreters for windows, including Linux ports, but I found those to be very lacking in usability, and extremely lacking compared to other Windows dev tools, especially MS stuff. I didn't set my standard as those lowest common denominator ports, but rather, tried to "compete" with successful MS products like Visual Basic. The "net result" is that I got a significant number of people using my tools because they felt it offered them a much more usable programming environment than those other REXX alternatives. Some even chose it over some MS tools.

> I recommend learning to use free tools

I've probably written more free software than many of the people posting to forums like these. Obviously, I have nothing against free software. What I dislike is people advocating stuff that is really not well-suited to a given target audience, advocating open source over well-respected tools just because it's open source, giving advice about platforms of which they are largely ignorant (and misrepresenting their own experience on such), etc.

> to make Ubuntu the best Linux distro around

I don't see the point of that. Ubuntu doesn't need to compete against other Linux distros, because I don't see why any current Linux user wouldn't already have tried it out and either be using it or have rejected it. The only way to grow the enduser, and developer, base is to start to appeal to non-Linux users/programmers. And you're not going to do that if you're competing in a vacuum. For example, Mac and Windows developers sure as hell aren't going to be enticed by GNU autotools. If anything, they're going to be repulsed by them. Mac and Windows endusers aren't going to be enticed by needing to deal with Configure (and the multitude of headaches it brings) when they want to install some software. I mean, some of the people posting here about how they know what novice programmers/endusers need, don't even make RPM or DEB packages for their software. What the hell qualifies them to talk about the needs of such people if they aren't even packaging their stuff in a way that would be the most _minimal_ standard that any Mac or Windows user would even tolerate? And they're giving advice to novice Windows programmers??? They don't know the first thing about what Mac and Windows endusers and programmers want and need. These are not the people who are going to make any difference to Ubuntu's advancement. It will need to be done by people who are willing to, and have some experience, transcending the "GNU mindset" of those folks. It will need to be done by people who do not see an advantage to supporting an endless number of Linux distro forks, all with essentially the same stuff, but rather focussing upon supporting only the major distros. It will need to be done not by people who believe that folks use Windows only because they've been brainwashed or strong-armed by MS, but because Windows stuff actually can be more usable to the majority of endusers and programmers than this lowest common denominator, "use a command line or you're out of luck", "you don't need good docs because you have the source code" stuff. And it will take people who are willing to look at Windows stuff to see why endusers choose it, and are willing to say "um, this here is actually pretty usable. Let me just borrow this approach for my own offering". I swear if Linux dev tool developers had made Open Office, it would look Emacs, and they'd be futilely telling Windows endusers "You don't _need_ MS Office. I don't see why you just don't switch over to Emacs running on Ubuntu". Clueless, really.

---

### Post by j_g on 2007-03-12
> Here is the code:
[http://nostdal.org/~lars/programming/c/mingw/screensavers/](http://nostdal.org/~lars/programming/c/mingw/screensavers/)

stay away from me and/or my posts/claims.

Omg! You've stolen someone else's code, run its makefile through a compiler, and are passing it off as the fruits of your own labor to ostensibly demonstrate that you have experience writing Windows software!

Is there no depth to which you'll sink?

I've actually written two Windows screensavers that are copyright under my own name. I don't need to use someone else's work in an attempt to establish my own credentials.

P.S. Although you've copied the code from someone else's FTP site and put it under your own page labeled Ming screensavers, these are _not_ Windows screensavers. They are merely normal apps that happen to display graphics using openGL. Admit it, you don't even know what Windows APIs are needed to make a screensaver.

---

### Post by Wybiral on 2007-03-12
> **j_g said:**
> Because MS tools are the most widely used and respected dev tools for PCs. It behooves any software developer of dev tools to get to know how they work so you can see why so many people choose those tools, and incorporate its selling points into your own offerings.

A case in point, I developed a complete REXX development environment for Windows. There were already several REXX interpreters for windows, including Linux ports, but I found those to be very lacking in usability, and extremely lacking compared to other Windows dev tools, especially MS stuff. I didn't set my standard as those lowest common denominator ports, but rather, tried to "compete" with successful MS products like Visual Basic. The "net result" is that I got a significant number of people using my tools because they felt it offered them a much more usable programming environment than those other REXX alternatives. Some even chose it over some MS tools.



I've probably written more free software than many of the people posting to forums like these. Obviously, I have nothing against free software. What I dislike is people advocating stuff that is really not well-suited to a given target audience, advocating open source over well-respected tools just because it's open source, giving advice about platforms of which they are largely ignorant (and misrepresenting their own experience on such), etc.



I don't see the point of that. Ubuntu doesn't need to compete against other Linux distros, because I don't see why any current Linux user wouldn't already have tried it out and either be using it or have rejected it. The only way to grow the enduser, and developer, base is to start to appeal to non-Linux users/programmers. And you're not going to do that if you're competing in a vacuum. For example, Mac and Windows developers sure as hell aren't going to be enticed by GNU autotools. If anything, they're going to be repulsed by them. Mac and Windows endusers aren't going to be enticed by needing to deal with Configure (and the multitude of headaches it brings) when they want to install some software. I mean, some of the people posting here about how they know what novice programmers/endusers need, don't even make RPM or DEB packages for their software. What the hell qualifies them to talk about the needs of such people if they aren't even packaging their stuff in a way that would be the most _minimal_ standard that any Mac or Windows user would even tolerate? And they're giving advice to novice Windows programmers??? They don't know the first thing about what Mac and Windows endusers and programmers want and need. These are not the people who are going to make any difference to Ubuntu's advancement. It will need to be done by people who are willing to, and have some experience, transcending the "GNU mindset" of those folks. It will need to be done by people who do not see an advantage to supporting an endless number of Linux distro forks, all with essentially the same stuff, but rather focussing upon supporting only the major distros. It will need to be done not by people who believe that folks use Windows only because they've been brainwashed or strong-armed by MS, but because Windows stuff actually can be more usable to the majority of endusers and programmers than this lowest common denominator, "use a command line or you're out of luck", "you don't need good docs because you have the source code" stuff. And it will take people who are willing to look at Windows stuff to see why endusers choose it, and are willing to say "um, this here is actually pretty usable. Let me just borrow this approach for my own offering". I swear if Linux dev tool developers had made Open Office, it would look Emacs, and they'd be futilely telling Windows endusers "You don't _need_ MS Office. I don't see why you just don't switch over to Emacs running on Ubuntu". Clueless, really.

Then why don't you go troll around in a Windows development forum instead of here?

EDIT:

Or better yet, develop some of that software that you claim Linux lacks instead of crying about it.

---

### Post by Tomosaur on 2007-03-12
> **lnostdal said:**
> j_g: 
Here is an example:

(this is WinXP SP2 under vmware-player)

Here is the code:
[http://nostdal.org/~lars/programming/c/mingw/screensavers/](http://nostdal.org/~lars/programming/c/mingw/screensavers/)

Now please go away, or at _least_ stay away from me and/or my posts/claims. You're stealing my time and your MS FUD is annoying and tedious.

edit: if preferred i could also have cross-compiled this ..   (mingw on linux can produce Windows "exe"-files)

Hey hey hey!

I hope you're not trying to claim this is your own work. I've seen these examples before:

[http://nehe.gamedev.net/counter.asp?file=data/downloads/0-9/1for3.zip](http://nehe.gamedev.net/counter.asp?file=data/downloads/0-9/1for3.zip)

Christophe Devine is the original programmer for these. I'm hesitating to accuse you of plagiarism here, since you left the copyright in the source, but you should probably have credited him in your post. The "I could have cross-compiled this" makes it sound like it's your work :/

---

### Post by lnostdal on 2007-03-12
> **Tomosaur said:**
> I hope you're not trying to claim this is your own work.

right .. the copyright message is as you mention intact

the point is to show (you?) how _easy_ it is to compile and do this stuff under windows using GCC .. i also mentioned that you can cross-compile (linux --> windows) and get the same result if you so wish

if i intended to claim the code as my own i would have done a _much_ better job .. there is no need to play this game of steal and hide though; i only use free software anyway .. it is not mine or yours; it is ours

..now cut the crap and games and let's get on with the hacking ;)

---

### Post by j_g on 2007-03-12
> the point is to show (you?) how _easy_ it is

If it's so easy such that you recommend your particular Windows dev system to even newbie Windows developers, how come a person who claims to have experience with Windows couldn't do this "easy", "trivial" thing on his own, and had to borrow someone else's code right down to the makefile in order to establish the supposed merits of his advice? (Not that you even got it right -- I already noted that you've erroneously identified these examples as screensavers when they do not even utilize the Windows API for screensavers and therefore are not even automatically launched by the OS when the screensaver is supposed to kick in).

How come you didn't just give the URL to the sources (which I found in 1 minute) instead of copying them to your own website?

Weak.

---

### Post by j_g on 2007-03-12
> develop some of that software that you claim Linux lacks instead of crying about it.

What makes you think that, in the _very short time_ that I've been using Linux, I haven't already managed to develop software for which there's no equivalent alternative? In fact, I've already released a freebie for a particular hardware peripheral that lacked the depth of linux support that I covered. Granted, I chose what I considered a "small project" as my very first foray into Linux programming, deliberately so. It manages shared access to this hardware device from numerous applications and "plugins". To do this, it features a daemon that creates a shared memory buffer and signals to coordinate access to the shared memory from various processes, use of signals/X messages to allow applications to ask each other for access to the device and to grant access to each other (ie, allow applications to serialize their access to the device under their own terms), a shared library to facilitate this, device I/O to the low level driver for this hardware, use of multi-threading (posix threads) to launch/run "plugins" (written in C or Python), GTK+ and bonobo to create a Gnome applet frontend to set some parameters for the device management, etc.

And when I finished the software I made a Deb package for Ubuntu so that common endusers would not have to struggle with Configure and source code in order to setup a package that has a daemon, shared lib, and gnome frontend at least.

But it's not just for endusers. It's part of a larger "Linux software development kit" I wrote for this hardware so other Linux developers could use it to write software for this device. It therefore comes with tutorials/docs that also meet my minimum standards for such.

Frankly, although I do consider it a small project, and of course, my very first Linux software, it _may_ actually be more sophisticated in its design and packaging than stuff you've written, so I'd be careful before you make too many assumptions about what I have, can, and intend to do with Linux programming. I think it should be obvious that I have a good amount of experience in Windows programming, and I'm levering some of that knowledge in my first foray into Linux dev. Don't assume that I can't and won't write Linux software that seeks to meet my own minimum standards of usability, because it's a _very good bet_ you'll end up being wrong (and just give me an opportunity to say "I told you so").

And I wrote this package myself. I didn't just take someone else's code and makefile, run it through a compiler and say "Look how easy it was for me to 'create' this software". I actually had to design how this stuff worked together, and code it all out.

_Everything_ I've talked about in this forum matters to me because, if I'm not already using it now, or have tried it and found it lacking, I will be using/evaluating soon. I'd advise you not to depict me as a Windows troll because it's a good bet I'll make you eat those words sooner or later.

---

### Post by pmasiar on 2007-03-12
OK. I can see what your position is, some parts do have merit - but you add too much spin to it. I personally may advice different approach, but it might be also matter of opinion.

> **j_g said:**
> Because MS tools are the most widely used and respected dev tools for PCs. 

Widely used - yes, it comes with almost-monopoly. Respected? Not by everyone, by far. If you don't want to get flamed, scale down your enthusiasm for MS products. Really. Unless you want constant flamewars. 

> It behooves any software developer of dev tools to get to know how they work so you can see why so many people choose those tools, and incorporate its selling points into your own offerings.

To learn what competition does makes sense *after* you know tools of your own side inside out, but not before. 

> I've probably written more free software than many of the people posting to forums like these. 

It is really hard to believe all your claims - you know the joke that on internet, nobody cares that you are a dog. From some of your comments I noticed you might be knowledgeable, but I still have your word only to  believe you are *that* good. Prove it somehow, or stop making claims. Put up, or shut up. 

> Obviously, I have nothing against free software. What I dislike is people advocating stuff that is really not well-suited to a given target audience, 

Target audience are Ubuntu users. You are the only one trying to convert people to Windows :-) When someone needs help about Windows, there are better places to ask help than forum dedicated to Ubuntu, no?

> Ubuntu doesn't need to compete against other Linux distros, (...) The only way to grow the enduser, and developer, base is to start to appeal to non-Linux users/programmers. 

Fair enough. Make it "best desktop" - but it is farther ahead :-)

>  people who do not see an advantage to supporting an endless number of Linux distro forks, all with essentially the same stuff, but rather focussing upon supporting only the major distros. 

You are going to decide which distros to support and which abandon?  Or do we ask real expert so loved by press - Enderle? Steve Balmer? Or maybe Gartner Group will decide? Your arguments to consolidate distros do not make sense - how to do that, and why?

Free software is like guerrilla. Do not aim for 80% acceptance rate: doubling it from 5% to 10% is all is needed for now, and  tactics is for that. Wait couple years, when free software will aim for 80% of users, your advice will be more timely. :-)

I am not interested discussing how superior MS software is to anything ever made by free software and how hopeless and clueless free software users are. 

You keep repeating yourself. It gets boring. We know we should abandon most distros, even Gentoo and Suse, and switch to superior MS Visual Studio, so we will be able to appreciate excellent free software you wrote in it. You can put it in your sig. Come on. Better go to Gentoo forums and persuade than to switch to Ubuntu. :-)

---

### Post by Wybiral on 2007-03-12
> **j_g said:**
> I'd advise you not to depict me as a Windows troll because it's a good bet I'll make you eat those words sooner or later.

OK... Then stop wasting your time telling people to "use Windows tools because Linux tools aren't as good" and start making Linux tools better.

I don't care if you say "I told you so"... Do it, prove me wrong. If you do it's just good for Linux. But I haven't seen you post anything productive, all I've seen is anti-portability and Linux tools, and pro-microsoft. And on a Linux forum... So yeah, I see it as being a "Windows troll" if you will.

That project you described sound good, what was it for? Any chance in tossing a link?

---

### Post by j_g on 2007-03-13
> but you add too much spin to it.

This coming from the person who denigrates MS offerings just because those offerings are from MS? Frankly, I think most businesses would see _you_ as employing heedless spin, rather than me.

```
Respected? Not by everyone
```

You're arguing with your own straw man.

> To learn what competition does makes sense *after* you know tools of your own side inside out, but not before.

That's ridiculous. You don't investigate what the marketplace is buying _after_ you finish designing your own offering. That's a prescription for failure.

> but I still have your word only to  believe you are *that* good. Prove it somehow, or stop making claims. Put up, or shut up.

I'm not a Microsoft employee, nor have I contributed any lines of code to MS dev tools. But I at least have the sense to recognize the merits of their offerings, know how many people favor these tools in the real world, and don't come off like some teenage niche brand fanboy who declares that people should not use them simply because they're from MS, or not free. Do you actually expect professional Windows developers to _not_ roll their eyes in disdain when you say such things???

> You are the only one trying to convert people to Windows

Typical fanboy black and white fanaticism. I'm not trying to convert anyone to Windows. The Linux software I'm writing doesn't even run on Windows. What I'm trying to do is counter misguided "advice" and counter-productive advocacy, people actually posting incorrect "information" all for the sake of attempting to endorse their brand of advocacy (like posting source for an alleged screensaver that isn't even a windows screensaver).

> When someone needs help about Windows, there are better places to ask help than forum dedicated to Ubuntu, no?

Absolutely. And there are much better people to ask then someone who dismisses MS offerings with some of the most lame fanboy advocacy one can imagine, as well as someone who takes someone else's source code, attempts to use it to establish his own credentials and "accuracy" of his own advice, not even realizing that the source code he chose doesn't even function as what he alleges it to be.

> You are going to decide which distros to support and which abandon?

Absolutely. I will evaluate a distro to my own minimum standards of usability, and support only those that pass the test. And even then, I may chose a smaller subset, because I simply think there are too many distros out there.

> Your arguments to consolidate distros do not make sense - how to do that, and why?

For the same reason that consolidation takes place in so many other venues. It can eliminate redundancies in effort, streamline development/production/testing/support, improve standardization, etc. There are many reasons.

Why did the European Economic Union form? How come all those countries got rid of their own currency and adopted the euro? Etc.

Of course, there are reasons why sometimes it is better to decentralize and spin off entities. But Linux has gone way, way, waaaaaaaaay beyond this point with the distros. It's already at the point of ridiculous, pointless, and counterproductive, and showing no signs of doing anything but getting worse. By the way, I'm hardly the first Linux person who feels this way. [http://www.linux-mag.com/id/2940](http://www.linux-mag.com/id/2940)

> Better go to Gentoo forums and persuade than to switch to Ubuntu.

I strongly suspect that most every Gentoo user who would _ever_ use Ubuntu already has a copy of it (and some other distros) tucked away on some partition. It's not like they have to pay for it. The geeks who love to play with configuration files have already been "sold" all of the Linux distros they can handle. You aren't going to increase Ubuntu's uptake even a small percentage by going after these people.

There _are_ some people who aren't using Linux who could perhaps be persuaded. But to get these people, you have to do much more than what has already been done, and particularly in the areas of usability and consolidation. You just don't realize that because you seem to not know any of these endusers very well. They use Windows and Macs. Oh yeah, and the Windows developers use MS tools. Lots of them.

I really think your concept of marketing needs a major, major overhaul and reality check.

---

### Post by lnostdal on 2007-03-13
> **j_g said:**
> If it's so easy such that you recommend your particular Windows dev system to even newbie Windows developers, how come a person who claims to have experience with Windows couldn't do this "easy", "trivial" thing on his own, and had to borrow someone else's code right down to the makefile 


I do not reinvent the wheel unless I have to. Creating a window (or fullscreen context) with an OpenGL context in it is all over the net (this is the first hit I found via Google). The Makefile of this particular example, however - was originally for Linux exclusively. It now shows how to compile OpenGL-stuff under Windows using GCC.

For OpenGL in most cases I'd probably use a(n) (already existing; yes - I'm still a "thief" .. :rolleyes: .. thanks for the support guys) portable library for getting the OpenGL-context up. SDL or GLUT or whatever. But this one shows how to do it directly via the Win32 API.

[quote=j_g]
How come you didn't just give the URL to the sources (which I found in 1 minute) instead of copying them to your own website?
[/QUOTE]

Because that would not show Tomosaur or anyone else how to compile it under Windows using GCC. I've already explained this to some other guy back in this thread.

You add nothing to this discussion or even this forum, j_g. You do not belong here because while using MS tools, asking questions about them or even recommending them (when nothing else is possible or feasible) is OK. It is _wrong_ to promote them while saying real alternatives _do not exist_ in the consistent way you are doing here and in many other threads when the Linux/GNU-options will do _absolutely fine_ and are _very good_ and thus "exist" in a practical context or manner also.

You are in all ways in a _direct_ opposition of the Ubuntu, Linux and Open Source/Free Software movement .. and also me and just about 100% of all the other members on this forum by doing this. You are _directly_ *provoking, insulting and hurting* this community with your FUD. I *strongly* suggest you find another place to play your war-, FUD- and trolling-games. 

..if this is not ultimately enforced upon you, then this is _not_ the kind of inconsistent forum/community I want to be a part of - and .. yeah, either _you_ change, or leave .. or _I_ leave. It's up to you; I can pretty much already predict what the community will prefer.

edit: Oh, and connecting this stuff with the screensaver-API of Win32? That is also trivial/easy; GCC is not the obstacle here.

---

### Post by Tomosaur on 2007-03-13
In case any one cares, I solved the problem, it was a missing library that I needed to link. MSVC didn't even report errors, it just refused to compile, so I'm back with Dev-Cpp for the time being. Perhaps I didn't have the equivalent of 'pedantic' switched on or something, but whatever..

To the OP - I really am very sorry this thread has derailed so much, I've reported it to mods to be split out from yours. I think the current discussion is interesting, so I don't really want it to get trashed, but it certainly doesn't belong here. I just thought your thread would be a better place to ask since the premise was somewhat similar to yours.

To the person (I think it's pmasiar?) saying 'this is not the place':
This IS the place. This is 'Programming Talk', not 'Ubuntu Programming Talk'. There's even a header near the top of the page saying:

> 
Programming Talk:
This forum is for all programming questions.
The questions do not have to be directly related to Ubuntu and any language is allowed. 

and since I know there are people who regularly post here that have, or do, program for Windows too, it's only reasonable to assume I would get some guidance. I did, and have benefited from it. That's pretty much the point of this forum, eh? :p

To j_g:
Inostdal is right -  I am still using gcc to program the screensaver, using the Win32 API. The problem was a linking error, because a library wasn't being found (although I'm not sure why - the library was physically on my machine, and the paths were all set up right, but when I'd tried to link it, it failed, must have missed the error message). It's all fixed now, I think it was something to do with a trailing slash causing an error. A lot of the forum members here are very passionate about free software, it's obviously not the best thing to tar it all with the same brush. I can understand your appreciation of the MS tools - it's perfectly logical that MS tools would be best for Windows development, but you have to understand that people here aren't big fans of MS, and most have used MS tools and come away unimpressed. I know I'm one of them, at least. I stopped using Windows while I was still on trivial command line apps, hence the win API was pretty damn alien to me when I needed to develop something a little more complex. I already kind of disliked MSVC, but it IS a poweful tool, and I can understand why Windows developers like it. I'm happy with less complicated stuff, but that's my opinion.

To everyone else:
Arguing about development environments is ridiculous, ok? You like chalk, MS devs like cheese. It's nothing to do with monopoly if MSVCE is given away **free**. It is a very powerful tool, and MS knows their platform better than anyone else. They KNOW how to make development easy for Windows, there's obviously something more than brainwashing going on there. If you don't like MSVC, then just don't use it. Nobody is forcing you too. If you want to, or need to, develop on Windows, then it's entirely up to you what you *choose*. Surely that follows on from the Ubuntu philosophy, right? Yes, j_g could tone down the 'MS Rawks' tone, but I doubt he's here to irritate anyone. He's been heplful to me, and other people. Other respondants in this thread have done nothing but argue, I think you need to take a step back and rethink this.

---

### Post by Vorian on 2007-03-13
everyone needs to cool down here.  I'm going to close this thread for 24 hours.

---

