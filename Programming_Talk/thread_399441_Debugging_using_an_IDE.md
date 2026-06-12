---
title: "Debugging using an IDE?"
date: 2007-04-02
forum: Programming Talk
---

### Post by alphilli on 2007-04-02
I have an application which is made up of about 50 C++ source files and a Makefile.  Is there any Linux IDE that will allow me to load these files, build the executable using my makefile, set breakpoints, run the application and interrogate data when I hit a breakpoint?

Obviously these are that things that a real IDE allows for.  But I cannot seem to find such a thing on Linux.

I believe it must exist because people could not still be building applications without such a tool.

---

### Post by lnostdal on 2007-04-02
DDD and KDGB

---

### Post by Jmccaffrey on 2007-04-02
> **alphilli said:**
> I have an application which is made up of about 50 C++ source files and a Makefile.  Is there any Linux IDE that will allow me to load these files, build the executable using my makefile, set breakpoints, run the application and interrogate data when I hit a breakpoint?

Obviously these are that things that a real IDE allows for.  But I cannot seem to find such a thing on Linux.

I believe it must exist because people could not still be building applications without such a tool.

emacs

---

### Post by alphilli on 2007-04-02
You can't be serious (emacs?).  This is 2007.

---

### Post by lnostdal on 2007-04-02
Emacs has a front-end to GDB (which is what KDGB and DDD uses as backend also).

..and Emacs is great; I use it all the time. Here:

> 
 They all used Emacs, of course. Hell, Eric Benson was one of the authors of XEmacs1. All of the greatest engineers in the world use Emacs. The world-changer types. Not the great gal in the cube next to you. Not Fred, the amazing guy down the hall. I'm talking about the greatest software developers of our profession, the ones who changed the face of the industry. The James Goslings, the Donald Knuths, the Paul Grahams2, the Jamie Zawinskis, the Eric Bensons. Real engineers use Emacs. You have to be way smart to use it well, and it makes you incredibly powerful if you can master it. Go look over Paul Nordstrom's shoulder while he works sometime, if you don't believe me. It's a real eye-opener for someone who's used Visual Blub .NET-like IDEs their whole career.

..from [http://steve.yegge.googlepages.com/tour-de-babel](http://steve.yegge.googlepages.com/tour-de-babel)

Talking about old stuff; the original LISP is from 1958, and the current (about 50 years afterwards) Common Lisp is the coolest language out there -- still after all this time.

You'll find that most Linux-programmers either use:

* Emacs
* ..or VIM

..and that they would never trade those for anything else currently out there.


edit: i think we prefer cooperation and communication between small programs/components - instead of tight integration into a big blob where no parts can be exchanged (and adding new components/parts is hard; emacs is very easy to customize)

---

### Post by mardawi on 2007-04-02
yeah, i never used emacs before... after reading this, i think i will give it a try!

---

### Post by j_g on 2007-04-03
> Is there any Linux IDE that will allow me to load these files, build the executable using my makefile, set breakpoints, run the application and interrogate data when I hit a breakpoint?

Frankly, Linux IDEs suck compared to those Microsoft dev tools you've used. Stay away from the Linux IDEs.

Here's what you do. When you compile your code (by invoking GCC from a command line, or via a makefile), make sure you specifiy the -g compiler flag so that extra debugging information is included in your executable.

Then, you obtain the GNU debugger, and a frontend for it. I recommend KDbg as the frontend. I find it to be much more usable than DDD. (KDbg is a QT app, but it will run under Gnome ok. If you use Synaptic to install KDbg, it should also install the GNU debugger for you). The GNU debugger is a command line debugger, and the KDbg frontend provides a graphical user interface that rides on top of this command line tool. It's sort of how Visual Studio is a graphical frontend to microsoft's C compiler/debugger/etc.

You run KDbg, and then from KDbg's File menu, choose the command to load your executable. (It will present a file dialog for you to locate your executable). If your executable was compiled with debugging info, then KDbg will display your C++/C source lines in a window (although the text is readonly - you can't edit it. But, you can double-click on a particular source line to toggle a breakpoint there). Then you use the Debug menu to step though the code, or run to a breakpoint, etc. KDbg will highlight your source lines (in that read-only text box) as you step through instructions. KDbg also has windows to display stack variables and memory (when the debugger is sitting idle at some breakpoint, for example), and other stuff that you'd expect a debugger to show you. (One caveat: KDbg does not appear to support multi-threaded code. If using pthreads, you may have trouble debugging).

When you find your bug, then you close down KDbg, and go fix your code in some text editor. (KDbg won't let you edit your code in place. It's a debugger only. Not an IDE). Then recompile your code. Rerun KDbg and reload your new executable (with the new source code). Debug again.

It's not efficient as a real IDE, but it appears that lots of Linux developers don't much care about efficiency. Anyway, it works.

---

### Post by lnostdal on 2007-04-03
hm, no need to restart/close down kdbg after making changes etc. .. kdbg will reload the source file automatically next time you do a run (f5) - keeping in sync

instead of double-clicking, use f9 to toggle breakpoints ... in general take note of all short-cut keys mentioned in the menus

---

### Post by pmasiar on 2007-04-03
ahhh, j_g welcome back, again repeating how Linux stinks? Some things never change... :-0

> **j_g said:**
> Frankly, Linux IDEs suck compared to those Microsoft dev tools you've used. Stay away from the Linux IDEs. (...)
It's not efficient as a real IDE, but it appears that lots of Linux developers don't much care about efficiency. Anyway, it works.

You are right as always in your technical advice, but you are missing *why* it is so. And it is not as you expect, and you seems to be frustrated. But you are frustrated because you are trying to swim against the flow. 

Many/most linux developers use Emacs/vim for past 10-20 years, they can use it with any new language around, and are not subject of tools version upgrade treadmill. Not that they do not care about efficiency - they *do* care, and what they use, works for them beter than IDE - all the free software available is the proof!

Now, what it means for rest of us? We can either try IDE - with full understanding that brightest experts are not interested in IDEs, and will not add their "expert support" to them like to the other free tools; or we can try learn tools what experts use. Which are *not* IDEs. 

Or, you can start a company, seling IDEs for Linux.... on second thought, maybe not :-)

---

### Post by sysctl on 2007-04-03
Eclipse + CDT supports visual debugging similar to Visual Studio.

---

### Post by j_g on 2007-04-03
> you are trying to swim against the flow. 

brightest experts are not interested in IDEs, and will not add their "expert support" to them. 

As usual, an excellent sales pitch:

"Whatever it is that you want, we're not giving it to you. And everything that you've already found to be lacking is exactly what we're offering you, so just shutup and use it."

You ought to work in PR. Really. What company wouldn't love to have you selling its products?

---

### Post by pmasiar on 2007-04-03
> **j_g said:**
> What company wouldn't love to have you selling its products?

j_g, you are still missing one important point - free software is not made by any company. People who are interested in doing something, just do it, in their free time. If people capable of creating slick IDE are not interested, how you *make* them become interested? It is not easy to force volunteers to do something if they don't want to do it. Any of people complaining about IDE, including you, can join efforts and prove me wrong, and create super-VS. Don't whine that someone else is responsible - not so. You have free tools, compiler, libraries - don't whine.

Or start a company selling IDE for Linux... You can use all my posts as advertisements. :-)

Free software is made by volunteers for fun, and this had obviously consequences which you are not ready to accept.

Why you expect someone (let's call him "Johny") spend time away from his friends and family doing something not fun, for free, and usefull for you, but useless for "Johny"? Would you do that? Did you already started? Can we see links?

Let me tell you my personal *opinion* - why I personally dislike IDEs. When using IDE, it is easy to write more code, but it is not easy to refactor it. When using good editor, writing and refactoring are same, so I refactor where it makes sense. As a result, with IDE I have more code to maintain, which is IMHO  *bad*.

---

### Post by j_g on 2007-04-03
> If people capable of creating slick IDE are not interested, how you *make* them become interested? It is not easy to force volunteers to do something if they don't want to do it.

I'm not, and have never, suggested that "volunteers should be forced to do something they don't want to do". You're missing _my_ point which is, it does _absolutely no good_ to respond to someone asking about an IDE by telling him *"I don't use an IDE, and neither do some other linux programmers, so therefore you shouldn't want nor use one either"*. (For the record, I also don't think it helps much to say "Make it yourself", even though that may be the only alternative one can offer. But that's life). What do you really think that accomplishes? Granted, I can't point him to good IDE for Linux either, and gave him advice that doesn't utilize an IDE. But that's only because I tried the Linux IDEs and I don't think there's a good one that will satisfy people who really like IDEs and obviously have tried some Linux tools and found them lacking (like the OP alludes) -- particularly people who like MS dev tools. And that's why I gave him advice about an alternative method. It's not because I was completely oblivious to his needs/wants, and was simply telling him to do something based strictly upon my own needs/wants. It's because I understand and agree with his preference of dev tools, and I have found that the solution I came up with is simply the best available alternative, albeit not really what I, and I believe he, would prefer. (And I do mention any caveats or shortcomings I see with the alternative. I'm just being honest with him, as best as I discern his needs/wants to be, based upon similiarities in our perspective/needs/wants).

As far as your other observation goes, granted, a freeware programmer is under no obligation whatsoever to cater to the needs of particular folks, but by the same token, he has no right to tell other folks that they shouldn't want what they want, nor find lacking that which they happen to find lacking. Those other folks are just as free to decide, and state, that for themselves.

I would hope that a new breed of Linux developer (very likely Windows or Mac developers crossing over into Linux, who have experience using IDEs for other systems) would have interest in improving Linux IDEs. If not, well, that's the way things go. Linux will simply have to be lacking in something that other alternatives do better. And if you don't care about IDEs at all, what difference does it make to you if developers who do care, choose another platform such as Windows? If you care because of advocacy issues, then maybe you _should_ start to care a lot more about IDEs, because as I point out above, the tact of simply telling people that they shouldn't want what they want, and shouldn't find lacking that which they do find lacking, isn't a viable answer to the problem. If these now-routine posts from people asking "Where can I get a Linux IDE that is comparable to <some MS IDE>?" (I mean, we're getting them like every week here -- doesn't that tell you that there is likely a need out there that _isn't_ being met?) seem to spark a need in you to tell these folks that "you don't need what you want", just because you want to pretend Linux is all things to all people, then maybe you _should_ be more serious about their needs and be personally doing more to address (rather than dismiss) them?

> Any people complaining about IDE, including you, can join efforts and prove me wrong, and create super-VS.

I have other projects that I'm already committed to, and do not have the time (right now) to attend to an easy, intuitive, Linux C/C++ IDE. (Although the idea does appeal to me, and I wouldn't rule out the possibility of doing that at some point when time is available). But that's irrelevant. The problem isn't that I'm not making such an IDE. The problem is that other people aren't doing that good job of it either, and yet, people are asking for better than what's available. And so when someone asks about the existence of such, and people express their opinions about such, it does no good to simply tell those people they shouldn't want what they want, and shouldn't find lacking that which they do find lacking.

> I personally dislike IDEs.

So what. I don't like hotdogs either. But that doesn't mean if someone posts a message saying "Where can I get a ballpark frank that tastes like what I used to get at a particular vendor", I'm not going to say "I don't like hotdogs. Therefore, you shouldn't like them either. You should eat hamburgers. We make everyone who comes here, and likes hotdogs, eat hamburgers instead. That's our way. Great, ain't it?".

If I happened to like hotdogs, but found the local ones lacking, I may say "I like hotdogs too. Unfortunately, I don't feel that the hotdogs you get around here are as good as the hotdogs you got there, and I'll tell you why...". That's the way it goes. If that really bugs you, then maybe you should care a lot more about Linux IDEs, and _you_ should improve them? Otherwise, why pretend to care about something you say you don't even like to use?

---

### Post by pmasiar on 2007-04-03
I have mostly no problem with everything you say, except this sentence:

> **j_g said:**
> )but it appears that lots of Linux developers don't much care about efficiency. 

because it is blatant lie. **Linux developers care very much about efficiency** - you just pretend not to see that *your definition* of efficiency is different than theirs, and *you* ask them to accommodate *your* approach to efficiency.

> **j_g said:**
> it does _absolutely no good_ to respond to someone asking about an IDE by telling him *"I don't use an IDE, and neither do some other linux programmers, so therefore you shouldn't want nor use one either"*.

You try hard to portrait Linux gurus as evil overlords forcing their choice over hapless beginners. Gurus do not ignore IDE because they are evil - in gurus best opinion, excellent universal editor as emacs or vim is in most cases preferable to IDE. 

If beginners want to become efficient Linux hackers, they should learn proper most efficient tools. Do we agree on that? 

> freeware programmer 

You know very well that free software is not freeware. You just placed it to add some oil to flames?

> is under no obligation whatsoever to cater to the needs of particular folks, but by the same token, he has no right to tell other folks that they shouldn't want what they want, nor find lacking that which they happen to find lacking. Those other folks are just as free to decide, and state, that for themselves.

Of course everybody is free to use anything she wants, pick any tool she like, and if it is not good enough, improve it. That's the whole point of free software. I am not telling what they should want or not want: I am telling why their choice of tool -- IDE -- is considered by gurus less effective, and what are (in opinion of gurus) better choices. Do I have right to say this advice, and explain why? Or you can decide that I have no right to voice my opinions if I happen do disagree with you?

I have no problem with your opinions, but if you mix a lie between useful technical explanation, I reserve right to call you on that lie.

> I would hope that a new breed of Linux developer (very likely Windows or Mac developers crossing over into Linux, who have experience using IDEs for other systems) would have interest in improving Linux IDEs.

I have no problem with that. For record, I recommend beginners to use SPE Python editor, which is very feature-rich, and has nice functionality which is not present in simple generic code editors.

It makes sense for someone playing with Python to play with Python IDE. But next step might be learning proper universal editor, like emacs or vim. I heard that vim can be scripted in Python... :-)

>  If not, well, that's the way things go. Linux will simply have to be lacking in something that other alternatives do better. 

Whose definition of *better* we are talking about? Yours? Can you prove it that your opinion about what is *better tool to edit source code* (== IDE) is more valid than join opinion of famous Linux hackers, who mostly prefer emacs or vim? 

> just because you want to pretend Linux is all things to all people, then maybe you _should_ be more serious about their needs and be personally doing more to address (rather than dismiss) them?

Linux is definitely *not* all things for all people. Linux is for people who want to learn tools what they use and become experts. Linux is for people who want to control their own destiny, and *not* for whiners who are happy with whatever marketoids from some corporation decide is good enough for them.

And seems to me you found excellent innovation to flamewars: instead of [vim vs emacs](http://en.wikipedia.org/wiki/Editor_war) you have "IDE vs. editors". It has no answer, everybody can use whatever tool they want. Big proprietary companies like lock-in which comes with IDE, in Linux lock-in does not make sense.

---

### Post by j_g on 2007-04-04
> lots of linux developers <don't seem to> care very much about efficiency

That comment was made in the context of a discussion about Linux developers seeming to think there's nothing wrong with the current state of Linux IDEs. (You yourself propose that  most Linux developers have no qualms about the way Linux IDEs are right now). The ubiquitous "GNU auto tools", which seem to be the "muscle" behind every Linux C/C++ IDE works as follows:

You've got autoscan, which generates a text-based configure.scan file. Then, you've got automake, which takes a text-based makefile.am file and generates one or more text-based makefile.in files. Then, you've got autoconf, which takes a text-based makefile.in, and text-based configure.am file, and generates a very convoluted, text-based configure file. Then, the configure file generates a whole boatload of other text-based files.

There's absolutely _nothing_ efficient about this. Far from it. Clearly, the goal was to try to support every possible fork of Linux/Unix in existance, which is something entirely different than efficiency. Obviously, efficiency was not the goal of this design.

I stand by my assessment of Linux C/C++ IDEs (and the above comment in its context).

> You try hard to portray Linux gurus as evil overlords forcing their choice over hapless beginners.

You've been reading too much Tolkein. I simply point out what I see to be, or not be, the merits of particular designs/paradigms/what-have-you, and what I deem to have been the intents behind choosing those designs/paradigms. And believe me, I'm far less "demagogery" about Linux developers than you are about MS developers. So don't even go there.

I simply don't think Linux IDEs are very good (and a _good part_ of that has to do with GNU auto tools. I also do think that integration among components done by separate entities can be a bit... well... unpredictable. That's not terribly surprising though. For example, Anjuta's use of gdbg is probably the most unstable interaction between an IDE and its debugger that I've ever used).

> excellent universal editor as emacs or vim is in most cases preferable to IDE.

That's fine if you believe that, and it's fine if the 5% of PC users who currently use Linux think that. But as you're seeing from the (what appears to be weekly) messages from new, former Windows folks (ie, 90% of the PC users) trying Linux development, they're telling you that they want "an IDE like <some MS dev tool -- typically .NET>". If all you've got for them is emacs, you're in big trouble. Check out the reaction from the OP of this thread to that very suggestion:

*"You can't be serious (emacs?). This is 2007."*

Why are you simply refusing to even acknowledge what other people are telling you pointblank? Is there some point to that?

> If beginners want to become efficient Linux hackers, they should learn proper most efficient tools. Do we agree on that?

Here's a better question. If you want the other 90% of PC Users to use Linux, then you should give them what they want and are asking for, rather than what _you_ think they should want/use. Do we agree upon that?

On the other hand, if all you want is to just keep the current 5%, then things are good to go.

> I am telling why their choice of tool -- IDE -- is considered by gurus less effective

I totally dispute your claim. It may be that the 5% of the current PC users who have chosen Linux think so (and even then, I haven't seen any verifiable figures to prove that), but I sure don't find it to hold true among developers in general -- certainly _not_ Windows developers. Most of them do use MS IDEs.

> Do I have right to say this advice, and explain why? Or you can decide that I have no right to voice my opinions if I happen do disagree with you?

Go ahead. It shouldn't be very long now before another guy comes along and asks "Is there a Linux IDE that's comparable to Visual C# NET?". You can go ahead and tell him "Use emacs".

Not sure what you think that's going to accomplish, nor am I sure how that's going to negate dissenting opinions from someone who obviously is much more in tune with the poster's choice of dev tools and methodology of working. But it's your prerogative.

> you mix a lie between useful technical explanation

Ironically, that's a lie. I don't do that.

> Can you prove it that your opinion about what is *better tool to edit source code* (== IDE) is more valid than opinion of famous Linux hackers

I can "prove" that my opinion about IDEs is better to someone who asks "where can I get a C/C++ IDE that's like <some MS dev tool>?". Why? Because I've made the same choices in dev tools as they have, not deliberately opposite choices, so I clearly am more empathetic and with their needs/wants, and experienced with the item in question, than someone who would not even endorse their choices. To assume otherwise is to assume that it's a good idea to pose the question "What's the best tasting soda in this store?" to a store employee who responds "I don't like soda.". You've pretty much lost the guy right there.

---

### Post by sysctl on 2007-04-04
I use vim myself, but being accustomed to Windows IDEs I agree that Linux is severely lacking in RAD tools department (for native applications that is). Besides, it is quite an elitist attitude to point out that such and such is more "efficient", "hardcore" and has "guru's" stamp of approval. It may be efficient for **your** workflow and habits, but stating a priori that "emacs > all IDEs" is not exactly the objective point of view.

---

### Post by pmasiar on 2007-04-04
> **j_g said:**
> You've been reading too much Tolkein. .

Thats lie, I never had a patience for Tolkien. I ignore rest of your posts.

---

### Post by Wybiral on 2007-04-04
> **j_g said:**
> ... Here's a better question. If you want the other 90% of PC Users to use Linux, then you should give them what they want and are asking for, rather than what _you_ think they should want/use. Do we agree upon that? ...

You mean what YOU think they want?

I came into Linux from Windows and I'm happier with my Linux dev tools/files.

And I don't think I'm the only one... So clearly the current tools work for a lot of Linux developers.

Also in regards to another comment you made... In the eyes of someone trying to reach a wider market target, portability and platform support **IS** efficiency. It's not just some excessive extra as you make it sound. There's a reason those tools support various platforms...

EDIT:

**Please moderate when people are trolling so the rest of us can post without conflict**

---

### Post by PriceChild on 2007-04-04
Please leave moderation to the moderators. It is extremely impolite to accuse others publically of trolling and could be considered trolling in itself. If you have a problem with a post then please use the report button.

I'm watching this thread :)

---

### Post by alphilli on 2007-04-04
Where can I get CDT?

---

### Post by j_g on 2007-04-04
> You mean what YOU think they want?

I _do_ think that I have a pretty good idea of what someone wants when he says something like "I used to use this MS IDE on Windows. I like it, and that's the sort of thing I want to use on Linux. I can't seem to find that on Linux. Does such a thing exist for Linux?"

Furthermore, I think that I understand that person's wants/needs better than someone who flatout dislikes the tools that person has chosen, and clearly does not work the same way that other person works. To assume otherwise is illogical.

And of course, I do not think that it serves any purpose to tell someone who wants an IDE, "you shouldn't want that".

> I came into Linux from Windows and I'm happier with my Linux dev tools/files.
And I don't think I'm the only one... So clearly the current tools work for a lot of Linux developers.

I came into Linux from Windows and I'm not happier with the Linux dev tools (well, the IDEs and stuff like autotools at least). I know I'm not the only one, otherwise we wouldn't have weekly messages from people saying things like "I used to use this MS IDE on Windows. I like it, and that's the sort of thing I want to use on Linux. I can't seem to find that on Linux. Does such a thing exist for Linux?".

So clearly the current tools don't "work" for other Linux developers. Makes sense, right?

Note: I say "work" because in the context of this discussion, it truly is a relative term. I _have_ used GNU autotools to make some Linux software already, and I have used IDEs like Anjuta to compile some Linux software. They "work". But that doesn't mean I prefer using them to MS dev tools. I really, really don't. I use the former only because that's all I have for Linux. Also note that when answering questions such as the above, _that_ is what I tell the person. I don't tell him "you shouldn't want that".

> portability and platform support **IS** efficiency.

Well, that's probably why people are asking for equivalent tools to the stuff they use on Windows, you think? I mean, they like, and prefer, using an IDE on Windows (and are telling you as much), so they want something just like it on Linux. So what good does it do to tell them to start doing something entirely different? Does that sound efficient to you?

Hi, moderator. :)

---

### Post by Wybiral on 2007-04-04
> **j_g said:**
> I mean, they like, and prefer, using an IDE on Windows (and are telling you as much), so they want something just like it on Linux. So what good does it do to tell them to start doing something entirely different? Does that sound efficient to you?

Hi, moderator. :)

I never said they should start doing something entirely different, did I?

I'm just saying... Not everyone has a problem with the tools the way they are.

I'm not saying people shouldn't write better tools, thats fine. But you make it sound like you need super fancy high-tech tools to program, when all you need is a compiler and the right dev files (and maybe a GUI editor if thats what you're into).

---

### Post by pmasiar on 2007-04-04
> **j_g said:**
> And of course, I do not think that it serves any purpose to tell someone who wants an IDE, "you shouldn't want that".

You are very picky to other people quoting you - where did you found this quote? 

As you are aware, Linux is *not* Windows. People coming from Windows to Linux have many options:

1) learn the best tools used by linux gurus
2) learn any existing IDE, and if it does not fit their needs, improve it
3) learn any of many other programmer's editors, and maybe improve it
4) if none of tools is good enough, start new one - you have all the compilers
5) decide that Linux is too much learning for them, and return to Windows
6) decide that al this is too much learning, but they want to use Linux anyway because it is "cool", and they assume that if they whine loud enough, someone will write programs for them.
7) whine to Microsoft, asking *them* to release whatever they want, for Linux. 

I prefer learners, not whiners, but it is my personal preference. :-)

j_g, you still pretend you do not understand that using free software (not freeware!) is... free :-) decision for anyone. It is not about convenience. No free software developer owes you anything. Software is as-is. Every developer of course wants users who are willing to learn new ways - but nobody wants whiners. It makes business sense to steer whiners towards competition - let them whine there :-)

Linux is not for everyone. Particulary not for someone who does not want to learn, and is happy with Windows.

How funny it would be if I came to some Microsoft forum and whined about why MSFT cannot release VS for Linux? BTW how long you think my post would survive before deleting?

---

### Post by pmasiar on 2007-04-04
> **j_g said:**
> Ironically, that's a lie. I don't do that.

here is your lie. OK, "lack of understanding"

> **j_g said:**
> lots of Linux developers don't much care about efficiency.

When talking about efficient tools for Linux development, I take [Linus opinion](http://en.wikipedia.org/wiki/Emacs#Other_implementations) over  any Windows whiner, every time.

---

### Post by j_g on 2007-04-05
> When talking about efficient tools for Linux development, I take Linus opinion

When answering someone's question about Linux IDEs, I take into account what that person says he wants and needs, not what someone else, who may or may not even use an IDE, thinks. Sorry, but the guy already passed on emacs. I'm not sure why you're still trying to sell him on it.

---

### Post by sysctl on 2007-04-05
> **alphilli said:**
> Where can I get CDT?

In Eclipse, **Help > Software Updates > Find and Install**. Select **Search new features to install**, and then check **Callistro Discovery Site**. It will return a list of plugins and CDT will be among them.

---

### Post by alphilli on 2007-04-05
Thanks for this.  It was a start.

However, when I get that list of plugins there are a bunch of them but none that resembles the name "CDT".  Does it also go by some other name?

Thanks.

---

### Post by GeneralZod on 2007-04-05
No mention of kdevelop yet?

I've not tried importing an existing project before, but check out:

[http://www.kdevelop.org/mediawiki/index.php/FAQ#How_to_create_a_simple_project_with_just_a_Makefile_.28also_known_as_Custom_Project.29_.3F](http://www.kdevelop.org/mediawiki/index.php/FAQ#How_to_create_a_simple_project_with_just_a_Makefile_.28also_known_as_Custom_Project.29_.3F)

For setting it all up for a build-debug cycle, try:

[http://ubuntuforums.org/showthread.php?t=399090](http://ubuntuforums.org/showthread.php?t=399090)

---

### Post by sysctl on 2007-04-05
> **alphilli said:**
> Thanks for this.  It was a start.

However, when I get that list of plugins there are a bunch of them but none that resembles the name "CDT".  Does it also go by some other name?

Thanks.

C/C++ Development Tools

---

### Post by pmasiar on 2007-04-05
great, finaly we can both agree on something (you did not disputed it): whan you said "lots of Linux developers don't much care about efficiency." that *was* a lie, and you know it.

> **j_g said:**
> When answering someone's question about Linux IDEs, I take into account what that person says he wants and needs, not what someone else, who may or may not even use an IDE, thinks. Sorry, but the guy already passed on emacs. I'm not sure why you're still trying to sell him on it.

this discussion was already widely off-topic from what OP asked. I was talking about IDE in general. As you know very well, I am not selling anything to anyone. use best tool which suits you. heck, use Windows if you like it so much and it suits you more, why should I care?

---

### Post by PriceChild on 2007-04-05
I will be closing this thread.

Involved parties may make one (1) closing statement each.

If the OP requires more advice then I will of course allow this thread to remain open.

---

### Post by alphilli on 2007-04-05
Well after all this I still have not found out how to get CDT installed within Eclipse.  

I'm ready to give up but I still find it hard to believe that people are developing applications under Linux without a decent debugging tool.  There must be something out there that one can find, install and actually have work within one week!

Emacs is not the solution!

---

### Post by Wybiral on 2007-04-05
> **alphilli said:**
> Well after all this I still have not found out how to get CDT installed within Eclipse.  

I'm ready to give up but I still find it hard to believe that people are developing applications under Linux without a decent debugging tool.  There must be something out there that one can find, install and actually have work within one week!

Emacs is not the solution!

What exactly are you looking for in a development tool? What all features are required?

---

### Post by j_g on 2007-04-06
> hard to believe that people are developing applications under Linux without a decent debugging tool.

You're using C++/C, right? I recommend kdgb.

1) Select the "System -> Administration -> Synaptic Package Manager" desktop menu item. This brings up Synaptic's window.
2) In Synaptic's window, select the "Edit -> Search" menu item. This brings up the search dialog.
3) Enter "kdbg" (minus the quotes), and press Enter. This should locate the kdbg package and display it in Synaptic's listbox.
4) Mark that kdbg package for installation.
5) Click the "Apply" button in Synaptic's tool bar. This will install kdbg.

Now, kdbg is a QT package (ie, more suited for the KDE desktop). If you're running the Gnome desktop, then after installation is complete, no kdbg menu item will appear under your "Applications -> Programming" menu. (Linux seriously needs an installation API to deal with these sorts of issues). So, you'll need to manually add a menu item as so:

1) Select the "System -> Preferences -> Menu layout" desktop menu item. This brings up the menu layout dialog.
2) In the "Menus" listbox, scroll down and highlight (click upon) the "Programming" item.
3) The listbox on the right will now show you all the items under your "Applications -> Programming" desktop menu. Click the "New Item" button. This brings up the "New Item Properties" dialog.
4) For the "name", enter "Debugger" (minus the quotes).
5) Click the "Browse" button. This brings up a file dialog. You need to use this to find the kdbg executable. It should be in /usr/bin (and this is where the dialog initially looks). So just try to find "kdbg" in the list, and double-click it.
6). Now just click the "OK" button to dismiss the "New Item Properties" dialog. This should now place a "Debugger" item under your "Applications -> Programming" desktop menu. Just select this to run kdgb. NOTE: I've found that sometimes you need to reboot your system before the new menu item shows up. (Linux really, really needs an installation API to address these issues).

See my first message in this thread (on page 1) for a little more discussion about kdbg itself. It's a fairly straightforward graphical debugger. It displays your source code, and allows you to double-click upon lines to set/clear breakpoints. Then, you can run/debug the code, and use kdb's variables window, and other windows, to show you the contents of variables/memory/registers, etc.

Is this scheme as good as an integrated IDE? No. Is it as good as Microsoft's IDEs? Absolutely not. Does it work? Yes. Is it serviceable? Yes. It's not a bad debugger at all. You should find that it does what you need. Does this mean that Linux doesn't need improved dev tools? No. Linux does not live in a vacuum and must compete with, and be judged against, the other alternatives out there.

P.S. Yes, emacs is not the solution. But you'll still need a separate text editor to edit your source code. I just use Gedit. There's a plugin you can download that will automatically run a makefile from Gedit, and display the gcc compiler's output messages to Gedit's "console window". Again, it's not really an IDE in the way that Windows users have come to know IDEs, but it's better than nothing.

P.P.S Ensure that your makefile supplies the -g option to gcc/g++, or else debugging info will not appear in your executable. In that case, Kdgb will still debug your exe, but it won't display your source code because it doesn't have needed debug info.

---

### Post by GeneralZod on 2007-04-06
> **alphilli said:**
> Well after all this I still have not found out how to get CDT installed within Eclipse.  

I'm ready to give up but I still find it hard to believe that people are developing applications under Linux without a decent debugging tool.  There must be something out there that one can find, install and actually have work within one week!

Emacs is not the solution!

Did you try my suggestion on the last page?

---

### Post by alphilli on 2007-04-06
Yes. I had tried that before I started this thread and I couldn't even get it to install.

---

### Post by GeneralZod on 2007-04-06
> **alphilli said:**
> Yes. I had tried that before I started this thread and I couldn't even get it to install.

Did you try:

```

sudo apt-get install kdevelop

```

?

Do you have the Universe repository enabled?

---

### Post by sysctl on 2007-04-06
> **alphilli said:**
> Well after all this I still have not found out how to get CDT installed within Eclipse.  

What actually is going wrong? At least do you get to the point that I have on the screenshot in my previous post?

---

### Post by alphilli on 2007-04-06
Thanks a lot.  Yes. I am using C++ alright.

The infomation you provided was great and it got me far enough to actually attempt to run my app. 

However, my app uses some shared libraries so I need to be able to set LD_LIBRARY_PATH and I can't figure out how I can set an environment variable within KDbg.  Is there a way?

Thanks.

---

### Post by alphilli on 2007-04-06
Yes. That exactly how I tried to install it.

 It downloaded some file(s) and then started to install and encountered some obscure error (something about a missing item) and then aborted the install.

I suspect it needs other modules installed first.

---

### Post by alphilli on 2007-04-06
I get to the screenshot that you show but the list of items I see in there is not the same as yours.  There is no CDT listed at all.

---

### Post by j_g on 2007-04-06
> my app uses some shared libraries so I need to be able to set LD_LIBRARY_PATH and I can't figure out how I can set an environment variable within KDbg.



On Linux, you don't need to set an environment variable for each individual app you run. You can set an environment variable in Linux and it is automatically applied to each app you run. I forgot offhand how to set the LD_LIBRARY_PATH in Linux, but you should be able to find some info if you do a search. Undoubtably, it involves
 finding and editing some configuration (ie, text) file.


But I think that an easier thing to do is just copy those shared libraries (.so files) to your /usr/lib directory (which is undoubtably already in the LD_LIBRARY_PATH).

1) Select the "Applications -> Accessories -> Terminal" desktop menu item. This opens a command prompt window. Its current directory will be your desktop.

2) Set your current directory to where your .so files reside. For example, if you have them in a folder named "libs" on your desktop, type the following command, and press Enter:

cd libs

2) Copy each .so file to /usr/lib. For example, if you have a lib named "libstuff.so", then type the following command, and press Enter:

sudo cp libstuff.so /usr/lib/

You'll be prompted to enter your administrator password (since you're copying to a directory that only an administrator can copy to). Do that and press enter.

Copy the other .so files as above.

---

### Post by Game_Ender on 2007-04-06
Since nobody is actually posting an IDE for linux, I would like to mention Code::Blocks.  Install a nightly build (they have debs built for Ubuntu).  It runs on Windows, Linux, and Mac.  It has a decent debugger, that is scriptable so you can enhance to provide better debug info for you custom classes.  Go [here]("http://forums.codeblocks.org/index.php?board=20.0") to get a nightly (much stabler than the typical night and much better than the last official release).

---

### Post by alphilli on 2007-04-07
Thanks for everyone's suggestions.  

I now have Eclipse running with CDT and it seems to do the job.  Of course, it's no VS but it does allow me to set breakpoints and display the value of data items.

Two problems I find with it are that it doesn't seem to have a way to display Unicode strings nicely and often pointers show up as NULL in the "Variables" window when they really aren't NULL.

I can live with these limitations though.

---

