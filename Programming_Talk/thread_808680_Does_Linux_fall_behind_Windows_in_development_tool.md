---
title: "Does Linux fall behind Windows in development tools? Is Lisp ready?"
date: 2008-05-25
forum: Programming Talk
---

### Post by Lau_of_DK on 2008-05-25
> **Can+~ said:**
> Drama queen. :lolflag:



Haha, sure, I know I rant a bit :) I think its something that could really move Linux forward if we got some good development tools. Mostly when I bring this stuff up people are like "what do you need a GUI for?" .. "why do you even need a debugger?".

/Lau

Ps.: I'll leave it alone now, until the next thread.

---

### Post by Can+~ on 2008-05-25
> **Lau_of_DK said:**
> Haha, sure, I know I rant a bit :) I think its something that could really move Linux forward if we got some good development tools. Mostly when I bring this stuff up people are like "what do you need a GUI for?" .. "why do you even need a debugger?".

/Lau

Ps.: I'll leave it alone now, until the next thread.

Well, if you're talking about C++, I've used Eclipse with the cdt plugin, and the debugger works great. Other than that, you can use kdbg, or just use gdb from the shell. It took time to get used to Eclipse though, but now I like it, especially with the py-plugin.

And if everything else fails: virtual box with windows, with visual studio whatever in there. I just don't see why people can't detach from an interface, what matters is the language.

---

### Post by Lau_of_DK on 2008-05-25
> **Can+~ said:**
> Well, if you're talking about C++, I've used Eclipse with the cdt plugin, and the debugger works great. Other than that, you can use kdbg, or just use gdb from the shell. It took time to get used to Eclipse though, but now I like it, especially with the py-plugin.

Sure, I'm actually sitting with PyDev open now, trying to smack some Eulers around :)

My point was more general. Ubuntu sports some of the best programming languages around like Lisp and Python, but its not very approachable for people switching from Windows. In Windows its very simple, install VS2005, chose your langue (C++, J, J#, C#, you name it), click run, and youve got a running GUI - dont like the look? drag drop things on the form, click run, its easy. On Linux you really have to put in some work, and I've yet to see a nice looking program built in Lisp.

In a perfect Ubuntu world there would be something like "sudo apt-get install developer-tools", and you'd have a simple suite to work from, just like Vs2005, but handling all the languages that are so heavily used in Linux with the appropriate documentation, intellisense and GUI designers needed. 

/Lau

---

### Post by Can+~ on 2008-05-25
> **Lau_of_DK said:**
> In a perfect Ubuntu world there would be something like "sudo apt-get install developer-tools", and you'd have a simple suite to work from, just like Vs2005, but handling all the languages that are so heavily used in Linux with the appropriate documentation, intellisense and GUI designers needed.

...

I totally agree with you. There are times I wanted a simple py+gtk IDE, but I have moved slowly to GUIless works, considering that I started entirely with GUI-like things with flash. I've tried the wxwidgets, and all, but nothing satisfies me.

One of my projects is build an eclipse plugin with which works with the pydev plugin; but I actually never made a plugin for eclipse, and don't know how to add the gtk functionality inside. I should probably read a lot before jumping into that project, but I lack the time.

For now, I contempt myself with just making applications work, later I will learn the ins and outs of eclipse.

Anyway, this is getting outside of the original subject :)

---

### Post by pmasiar on 2008-05-25
> **Lau_of_DK said:**
> When I switched from Windows and C++/C# to Linux and all these nasty interpreted languages with poor IDEs and GUI tools, 

I am in just the opposite trouble. After struggling with VB wizard hell (where it's hard to understand consequences of any change, so for every tweak you needed to run wizard again) I switched couple years ago to Perl, then Python. Freedom! Use good editor, and understand exactly what is going on! But not for long: I am again in IDE hell, this time with Java. I honestly tried to understand how Struts works, but gave up, paid $50 for MyEclipse plugin, and  I am training to become Java monkey until something better will come around.

For a good programmer with good language, IDE is just additional layer obscuring what you want to do, necessary only to navigate overly complex language and libraries. Yes, it does help generate more code, but, as Bill Gates famously said, measuring programmer's productivity in lines of code is like measuring airplane design in tons.

If you don't know what to program, join GameBaker (see my sig) and program some games :-) and if engine cannot do what you need, you can improve it :-D

---

### Post by LaRoza on 2008-05-25
> **Lau_of_DK said:**
> 
My point was more general. Ubuntu sports some of the best programming languages around like Lisp and Python, but its not very approachable for people switching from Windows. In Windows its very simple, install VS2005, chose your langue (C++, J, J#, C#, you name it), click run, and youve got a running GUI - dont like the look? drag drop things on the form, click run, its easy. On Linux you really have to put in some work, and I've yet to see a nice looking program built in Lisp.

In a perfect Ubuntu world there would be something like "sudo apt-get install developer-tools", and you'd have a simple suite to work from, just like Vs2005, but handling all the languages that are so heavily used in Linux with the appropriate documentation, intellisense and GUI designers needed. 


VS is from the same company that made the OS, so are those languages (as they are used). In the free world, there are no such restrictions. This leads to choices to make. It can be a little confusing, as there is no man behind the curtain. However, there are GUI creation tools for Linux. 

The sticky link, [http://ubuntuforums.org/showthread.php?t=772507](http://ubuntuforums.org/showthread.php?t=772507), as a list for you of some of the tools for creating GUI's. Note, wxGlade supports Lisp.

In a perfectly Ubuntu world, there would be a large collection of tools easily downloaded. However, these tools wouldn't be mandatory. Wait...it is like that now ;)

---

### Post by Alasdair on 2008-05-25
Java isn't really an object-orientated language, it's an IDE-orientated language. ;-) I've certainly seen the horrors of what people can do with VB and MS Access when they don't understand what's going on, but get away with it due to the hand-holding wizards. Imagine someone that clearly did not fully understand the concepts of loops and arrays. Now give them a complex form with 300 or so nearly identical widgets arranged on it. Instead of using a loop to iterate over a control array containing the widgets, they had a individual subroutine copied and pasted 300 or so times for every single button. VBA + Access is like crack to such people... Luckily this wasn't an actual system, but is was a piece of A-Level coursework (it got a good mark too!). My VB6 monstrosity was positively wonderful by comparison... good times. :)

> I've yet to see a nice looking program built in Lisp.
There are plenty of (supposedly good) GTK bindings for Common Lisp out there, so it should theoretically be possible to build applications that look just like anything else on your desktop. McCLIM also has a GTK backend and there are a few nice apps written for that. Personally I get along fine with the LTK bindings to the tk toolkit, and although tk may have fallen out of the toolkit ugly tree and hit every branch on the way down it's simple and it works well.

Oh and games are always fun to code, plus you can get SDL bindings for nearly every language under the sun.

---

### Post by Majorix on 2008-05-25
> **Lau_of_DK said:**
> Sure, I'm actually sitting with PyDev open now, trying to smack some Eulers around :)

My point was more general. Ubuntu sports some of the best programming languages around like Lisp and Python, but its not very approachable for people switching from Windows. In Windows its very simple, install VS2005, chose your langue (C++, J, J#, C#, you name it), click run, and youve got a running GUI - dont like the look? drag drop things on the form, click run, its easy. On Linux you really have to put in some work, and I've yet to see a nice looking program built in Lisp.

In a perfect Ubuntu world there would be something like "sudo apt-get install developer-tools", and you'd have a simple suite to work from, just like Vs2005, but handling all the languages that are so heavily used in Linux with the appropriate documentation, intellisense and GUI designers needed. 

/Lau

You are forgetting about Netbeans, which is a perfect tool for the drag&drop approach you seem to want to have.

You have to pay for VS2008, while you don't for NB.

With VS2008 you have direct access to VB and C#. With NB, you get a lot of languages to choose from, including Java, Jython and JRuby. I have tried running IronPython on top of VS, but I was unsuccessful. Either it was a bug or I did something wrong; but who cares, it is not as easy as you say it is.

---

### Post by slavik on 2008-05-25
> **pmasiar said:**
> I am in just the opposite trouble. After struggling with VB wizard hell (where it's hard to understand consequences of any change, so for every tweak you needed to run wizard again) I switched couple years ago to Perl, then Python. Freedom! Use good editor, and understand exactly what is going on! But not for long: I am again in IDE hell, this time with Java. I honestly tried to understand how Struts works, but gave up, paid $50 for MyEclipse plugin, and  I am training to become Java monkey until something better will come around.

For a good programmer with good language, IDE is just additional layer obscuring what you want to do, necessary only to navigate overly complex language and libraries. Yes, it does help generate more code, but, as Bill Gates famously said, measuring programmer's productivity in lines of code is like measuring airplane design in tons.

If you don't know what to program, join GameBaker (see my sig) and program some games :-) and if engine cannot do what you need, you can improve it :-D
on a note of agreement (is this the first time we agreed on anything?), when I took the advanced C programming class in college, one of the first tasks was to create a separately compiled program (multiple header/source files), I opened up VC++6, then closed it and found Dev-C++. :)

---

### Post by Lau_of_DK on 2008-05-25
> **Alasdair said:**
>  McCLIM also has a GTK backend and there are a few nice apps written for that. Personally I get along fine with the LTK bindings to the tk toolkit, and although tk may have fallen out of the toolkit ugly tree and hit every branch on the way down it's simple and it works well.


First of all, McCLIM is so ugly I hoped nobody would mentioned it, because it really drags the whole forum down. Secondly, the "i know it sucks but its so simple and it works" argument, is another way of saying "in a Linux world where everything is unstable and nearly unuseable, I'll stick to this incredibly bad tool, because at least its simple, and it works." You need help my friend.

> **LaRoza said:**
> VS is from the same company that made the OS, so are those languages (as they are used). In the free world, there are no such restrictions. This leads to choices to make. It can be a little confusing, as there is no man behind the curtain. However, there are GUI creation tools for Linux. 


Yes, and they suck, thats the whole point. 

> **LaRoza said:**
> 
In a perfectly Ubuntu world, there would be a large collection of tools easily downloaded. However, these tools wouldn't be mandatory. Wait...it is like that now ;)

With one addition: "Easily downloaded and excellent in quality". I mean honestly, this is one area where Linux is seriously lagging behind Microsoft and its a shame. 

[QUOTE=pmasiar]
For a good programmer with good language, IDE is just additional layer obscuring what you want to do, necessary only to navigate overly complex language and libraries.
[/QUOTE]

This is exactly the type of argument thats keeping quality back. Basically "Because I'm such a 1337 h$x0rz I'll only use emacs, with black text and a black background, and everybody who wants a real IDE is trying to cover up bloated code" - Its simply not true. Vs2005 speeds programming up, it makes libraries easily discoverable and its a generic platform that everybody easily understands. I'm sorry you've had bad experiences with VB in the past, but honestly, I think thats what VB is there for :)

/Lau

---

### Post by Alasdair on 2008-05-25
> **Lau_of_DK said:**
> First of all, McCLIM is so ugly I hoped nobody would mentioned it, because it really drags the whole forum down.
McCLIM is ugly by default, yes, but that is why I mentioned that it also has a *GTK backend*. If you use that it will look like just like any other app that comes with Ubuntu.

> **Lau_of_DK said:**
> Secondly, the "i know it sucks but its so simple and it works" argument, is another way of saying "in a Linux world where everything is unstable and nearly unuseable, I'll stick to this incredibly bad tool, because at least its simple, and it works." You need help my friend.
Why do you jump from 'simple and it works' to 'unstable and unusable'? I use LTK precisely because it is the most stable and usable widget toolkit for cl. Have you heard of the [KISS principle]("http://en.wikipedia.org/wiki/KISS_principle")? The fact that it is ugly is irrelevant to me. There are plenty of other gui libraries for lisp out there that may suit you, see [here]("http://www.cliki.net/GTK%20binding") and [here]("http://www.cliki.net/Graphics%20Toolkit").

---

### Post by Lau_of_DK on 2008-05-25
> **Alasdair said:**
> 
Why do you jump from 'simple and it works' to 'unstable and unusable'? I use LTK precisely because it is the most stable and usable widget toolkit for cl. Have you heard of the [KISS principle]("http://en.wikipedia.org/wiki/KISS_principle")? The fact that it is ugly is irrelevant to me. There are plenty of other gui libraries for lisp out there that may suit you, see [here]("http://www.cliki.net/GTK%20binding") and [here]("http://www.cliki.net/Graphics%20Toolkit").

I made the jump based on your own logic. By saying "its irellevant" says to me youre missing the point, or at least, MY point. It was that Linux lacks GUI Development tools integrated in nice IDE's that can compete with Visual Studio.

On different note: You actually showed me quite a few GUI libs that I wasn't aware of for Lisp, so I'll look into it abit more, but a word of caution: If its all ugly, I'll start ranting again :)

/Lau

---

### Post by LaRoza on 2008-05-25
> **Lau_of_DK said:**
> 
Yes, and they suck, thats the whole point. 

With one addition: "Easily downloaded and excellent in quality". I mean honestly, this is one area where Linux is seriously lagging behind Microsoft and its a shame. 

This is exactly the type of argument thats keeping quality back. Basically "Because I'm such a 1337 h$x0rz I'll only use emacs, with black text and a black background, and everybody who wants a real IDE is trying to cover up bloated code" - Its simply not true. Vs2005 speeds programming up, it makes libraries easily discoverable and its a generic platform that everybody easily understands. I'm sorry you've had bad experiences with VB in the past, but honestly, I think thats what VB is there for :)


Do they? They seem high quality to me. Remember: Linux has some of the most visually impressive applications. They were built on Linux. 

I don't really know. I don't use VS and the one time I tried it, I couldn't figure out how to do anything.

Not all code uses a GUI. In fact, most doesn't. Even in Windows, the most impressive applications don't have a GUI (or a simple one). VS may make the creation of certain types of programs faster, but there is more to it than that. Programming isn't about making GUI's, it is about solving problems. It may be that certain types of programs benefit from VS, but most do not.

(It isn't a generic platform...It is a Windows specific IDE.)

---

### Post by LaRoza on 2008-05-25
> **Lau_of_DK said:**
> 
On different note: You actually showed me quite a few GUI libs that I wasn't aware of for Lisp, so I'll look into it abit more, but a word of caution: If its all ugly, I'll start ranting again :)


Don't rant on this thread. Remember, beauty is in the eye of the beholder. I find Ratpoison to be beautiful and elegant. I like wmii and think it is the greatest WM. Not everyone does.

For a programming idea (the purpose of this thread...), how about making things "pretty" whatever that means.

---

### Post by Lau_of_DK on 2008-05-25
> **LaRoza said:**
> Do they? They seem high quality to me. Remember: Linux has some of the most visually impressive applications. They were built on Linux.


Eeeh? Everything made for Windows these days is extremely eye-candied up, take the new Office suite for instance. (not that Im a fan, but I've never seen anything look that good on Linux)

> **LaRoza said:**
> 
I don't really know. I don't use VS and the one time I tried it, I couldn't figure out how to do anything.


Now... Does this say alot about VS, or about you? :lolflag:

> **LaRoza said:**
> (It isn't a generic platform...It is a Windows specific IDE.)

Let me rephrase: Its intuitively easy to pick up.

Anyway, I feel kinda bad for the OP, since we drifted from the topic, so lets drop the "Microsoft pwns Linux" sub-thread :)

/Lau

---

### Post by LaRoza on 2008-05-25
> **Lau_of_DK said:**
> Eeeh? Everything made for Windows these days is extremely eye-candied up, take the new Office suite for instance. (not that Im a fan, but I've never seen anything look that good on Linux)

Now... Does this say alot about VS, or about you? 

Let me rephrase: Its intuitively easy to pick up.

Anyway, I feel kinda bad for the OP, since we drifted from the topic, so lets drop the "Microsoft pwns Linux" sub-thread :)


Yippee, MS Office is pretty. Look at Linux now. Look at Compiz (look at all the plugins and settings!), look a OzOS (Enlightenment). How a window is styled depends on the window manager. In wmii, it is plain, in Compiz, it can be anything you want. 

Perhaps it says a lot about me. It probably indicated I prefer to focus on programming rather than the tool. I have seen people using VBA in MS Access without knowing how (or even the concept) to normalize a database. I prefer to know SQL and database design, rather than how to easily use a non free tool on a specific platform.

If VS is what you use in your job, and it works, it must be a good tool. I am not saying it isn't, but it is just a tool. At the end of the discussion, it is yet another editor with some features. If God intended us to use VS, it would be available for Linux.

---

### Post by Joeb454 on 2008-05-25
I quite like VS, but I also like VIM ;)

I'm easy when it comes to development app's. Though I've noticed the thread steering away from the title ;)

---

### Post by pmasiar on 2008-05-25
> **Lau_of_DK said:**
> "i know it sucks but its so simple and it works" argument, is another way of saying "in a Linux world where everything is unstable and nearly unuseable, I'll stick to this incredibly bad tool, because at least its simple, and it works." You need help my friend.

maybe it is you who need help :-) Read [Biculturalism](http://www.joelonsoftware.com/articles/Biculturalism.html) essay by Joel Spolsky (who worked for MSFT and knows exactly what he is talking about).

Main difference between Unix/Linux and Windows is, that Unix is "set of small sharp tools which do one thing, and do it right", focused on needs of developer, while Windows is big warm fuzzy experience for user, developer be damned.

> Yes, and they suck, thats the whole point. 

You somehow failed to prove that, or your proof sucks :-) Can you see difference between your opinion and a fact?

> With one addition: "Easily downloaded and excellent in quality". I mean honestly, this is one area where Linux is seriously lagging behind Microsoft and its a shame. 

LOL. Easy to download and install is **exactly** the area where Linux pwnz Windows big time! Seems like lack of relevant skills  on your side :-)

> "Because I'm such a 1337 h$x0rz I'll only use emacs, with black text and a black background, and everybody who wants a real IDE is trying to cover up bloated code" - Its simply not true. Vs2005 speeds programming up, it makes libraries easily discoverable and its a generic platform that everybody easily understands. 

LOL, I don't use emacs, switched to white background long time ago - I even created custom Midnight Commander color style for that! :-)

VS is easily discoverable for anyone who uses it for many years, but for experienced programmer who knows what to do using another editor, VS can be frustratingly inconvenient and limiting. IDEs, and especially VS, are for people who don't care about customizing the environment, and are happy with whatever features IDE developers deemed good enough for plebes, I mean users. I don't want to spent another 10 years mastering another IDE, and if I made some customizations, I want them to be easily extracted and transferred to another  of many systems I need to use daily. 

Yes, VS allows you to generate more code. But generating code is less important than refactoring it, and that's exactly where VS sucks. IntelliJ is the non-sucking IDE, but not VS.

> I'm sorry you've had bad experiences with VB in the past, but honestly, I think thats what VB is there for :)

For bad experiences? You might be right :-) I had those multiple times, so it might be a pattern :-)

> so lets drop the "Microsoft pwns Linux" sub-thread 

... especially if everyone above n00b level knows that  "Linux pwnz Microsoft" :-)

---

### Post by CptPicard on 2008-05-25
Lau, you really need to give Clojure+Swing+Netbeans a go. A completely dynamic, Lisp way to write Swing GUIs... and when you don't want to edit a running app as Clojure code, you can always draw up your GUI stuff in Netbeans first, and then just hook up actions and stuff in Clojure... it's beautiful :)

---

### Post by LaRoza on 2008-05-25
> **CptPicard said:**
> Lau, you really need to give Clojure+Swing+Netbeans a go. A completely dynamic, Lisp way to write Swing GUIs... and when you don't want to edit a running app as Clojure code, you can always draw up your GUI stuff in Netbeans first, and then just hook up actions and stuff in Clojure... it's beautiful :)

Nah, I recommend: Clojure# and MS Visual Netbeans.

---

### Post by Joeb454 on 2008-05-25
I recommend Chocolate-Covered Ubuntu Beans ;)

---

### Post by ZylGadis on 2008-05-26
Interesting thread bordering on flaming. Very interesting :)

Lau is undoubtedly a very misled young man/woman who prefers form over substance (which is contrary to the preferences of all good programmers (and, do not forget, all generalizations are bad)). At the same time, I have noticed many trends among other young men/women here (not that I am very old) that I disagree with, namely preference for python as a solution to everything, preference for lisp as a solution to everything, preference for anything Paul Graham says, etc. So, perhaps, the best abstraction that can be done is that people differ in their value systems and preferences, and it is meaningless to argue. To each his own, and everyone must reach his own enlightenment.

To all of you: show me the code. Nothing else matters in this context. The silliest idiot who did 300 copies of a piece of code in Microsoft Access did more useful work than you did in this thread (myself included).

The good part is that none of us are afraid to judge ourselves or others. And sometimes we even are right :) 

Back to topic: I have never in my 19 years of programming lacked for ideas. It is time to do everything I want that I miss.

---

### Post by slavik on 2008-05-26
> **ZylGadis said:**
> Interesting thread bordering on flaming. Very interesting :)

Lau is undoubtedly a very misled young man/woman who prefers form over substance (which is contrary to the preferences of all good programmers (and, do not forget, all generalizations are bad)). At the same time, I have noticed many trends among other young men/women here (not that I am very old) that I disagree with, namely preference for python as a solution to everything, preference for lisp as a solution to everything, preference for anything Paul Graham says, etc. So, perhaps, the best abstraction that can be done is that people differ in their value systems and preferences, and it is meaningless to argue. To each his own, and everyone must reach his own enlightenment.

To all of you: show me the code. Nothing else matters in this context. The silliest idiot who did 300 copies of a piece of code in Microsoft Access did more useful work than you did in this thread (myself included).

The good part is that none of us are afraid to judge ourselves or others. And sometimes we even are right :) 

Back to topic: I have never in my 19 years of programming lacked for ideas. It is time to do everything I want that I miss.

I can agree to your point that the dominant thought in this forum is that Python is the solution to everything, I cannot agree, however, with your point that "lisp is a solution for everything" as another dominant though in this forum.

As for the "show me the code," you might be right. The thing to think about is that writing code != knowledge simply due to the fact that I know many professors who wrote their last C code before I was born, but posses more knowledge than all of the "regulars" of the programming forum. Then again, I have not seen any code posted by you ...

---

### Post by Lau_of_DK on 2008-05-26
> **CptPicard said:**
> Lau, you really need to give Clojure+Swing+Netbeans a go. A completely dynamic, Lisp way to write Swing GUIs... and when you don't want to edit a running app as Clojure code, you can always draw up your GUI stuff in Netbeans first, and then just hook up actions and stuff in Clojure... it's beautiful :)

Interestingly I got a PM from Wybiral saying the exact same thing a couple of days ago. Im suspecting you guys have been caught up in some pseudo-religious-sect, and no youre trying to reenlist me? :) The effort is appreciated, and Clojure is at the top of my todo list.

[QUOTE=pmasiar] <- Aimed at -> [/QUOTE]
>**maybe it is you who need help. Read [Biculturalism](http://www.joelonsoftware.com/articles/Biculturalism.html) essay by Joel Spolsky (who worked for MSFT and knows exactly what he is talking about).**

You read too much, but alright, I'll give it a read

[B]>Main difference between Unix/Linux and Windows is, that Unix is "set of small sharp tools which do one thing, and do it right", focused on needs of developer, while Windows is big warm fuzzy experience for user, developer be damned.
[/B]

This is a typical comment from someone who is not accustomed to VS, if you read my previous posts in this thread, you'll note that my concern is based primarily on VS being a superior tool for the developer.


[B]>LOL. Easy to download and install is **exactly** the area where Linux pwnz Windows big time! Seems like lack of relevant skills  on your side :-)
[/B]

Dont be so quick to judge. LaRoza said she wanted something that was easy to download, and not mandatory. I said that the goal was ease of download + (as in PLUS, ALSO, NOT EXCLUDING) excellent in quality. So _my_ theme for the day, was higher was higher quality.


[B]LOL, I don't use emacs, switched to white background long time ago - I even created custom Midnight Commander color style for that! :-)
[/B]

HAHA! :lolflag:

[B]>Yes, VS allows you to generate more code. But generating code is less important than refactoring it, and that's exactly where VS sucks. IntelliJ is the non-sucking IDE, but not VS.
[/B]

When I say "speed up coding" I dont mean for the sake of having your source file contain the maximum amount of characters, I mean you can write a TCP/IP multiclient server from the bottom up in less than 1 hour. And on top of that - The client will look extremely nice :)


**>... especially if everyone above n00b level knows that  "Linux pwnz Microsoft" :-)**

You're right of course, and it was for a good reason that I abandoned Microsoft products ENTIRELY for the sake of commiting to Linux. Im just trying to raise some awareness that there is one area where Linux is falling behind and since Linux is based off a community of developers, future releases could increase in quality exponentially if the tools were improved on.

Anyway, if you dont get it by now, I actually recommend that you switch to VB :)

/Lau

---

### Post by Lau_of_DK on 2008-05-26
> **ZylGadis said:**
> Interesting thread bordering on flaming. Very interesting :)

Lau is undoubtedly a very misled young man/woman who prefers form over substance (which is contrary to the preferences of all good programmers (and, do not forget, all generalizations are bad)). 

First of all, the name Lau is danish male-name. Which means that I'm a Man, with a capital M as in... Microsoft :)

Secondly - Where do you guys get your intel "Lau prefers form over substanse". Its the most simplistic understanding of this debate possible. Its not a matter of form over substance, its a matter of producing quality software that is not lacking in either department and more specifically: Having tools that **assist** you in producing this software.

Just an example: If Visual Studio had Lisp as a project type and could run/compile Lisp programs with the usual ease of GUI design I would probably purchase an XP + Visual Studio, and have that as a boot option for development. But Lisp, wonderful as it is, is crippled when it comes to producing quality, easily deployable, good looking programs. I've seen several "why is Lisp so under-appreciated?" and people philosofize for hours, but the reason is just this: Its unapproachable, incomplete and at a stage of infancy compared to Quality Languages+IDEs like C#. Of course it would be nice if the truth was that Lisp coders are just super-1337-spectacular compared to everyone else and thats why no-one appreciates their language, but its just not the case-

And just to relieve my guilty conscience: For a good programming idea, there are many types of backup solutions that are interesting to work with.

/Lau

---

### Post by Lster on 2008-05-26
This argument seems to have an awful lot of opinion but not much reason.

[QUOTE=pmasiar]LOL. Easy to download and install is **exactly** the area where Linux pwnz Windows big time!
[/QUOTE]

Why?

[QUOTE=pmasiar]VS is easily discoverable for anyone who uses it for many years, but for experienced programmer who knows what to do using another editor, VS can be frustratingly inconvenient and limiting.[/QUOTE]

I'm now at a point when I am well experienced and I still like VS - it's my primary choice when working on Windows (which isn't often). I know many very experienced programmers who use it... and I've genuinely found it useful myself especially when learning new parts of the language. In fact, it's kind of like Python's console which I also find a great aid.

If you hate the additional features it has, you can always use it as a glorified text editor! :)

---

### Post by Vox754 on 2008-05-26
> **Lau_of_DK said:**
> **"why is Lisp so under-appreciated?"** and people philosofize for hours, but the reason is just this: Its **unapproachable**, **incomplete** and at a **stage of infancy** compared to Quality Languages+IDEs like C#. Of course it would be nice if the truth was that Lisp coders are just super-1337-spectacular compared to everyone else and thats why no-one appreciates their language, but its just not the case-


Can someone please unban lnostdal?!

I demand a public confrontation between these two guys!

---

### Post by Lau_of_DK on 2008-05-26
> **Vox754 said:**
> Can someone please unban lnostdal?!

I demand a public confrontation between these two guys!

Actually lnostdal has been a great help for me, when I was learning Lisp initially, he showed me many libs and many interesting parts of the language. After a few weeks of studying and applying what I was taught, I realised the things you quoted me on and confronted lnostdal with it. His initial reply was "I dont care", his second reply: He banned me from the IRC channel :)


/Lau

---

### Post by maximinus_uk on 2008-05-26
It is true, Lisp does study from a lack of resources in some areas (GUI programming, for one).

But I speak as someone who used to use VS (though some time ago, I must admit). When I first came to Linux I too was looking for a Linux VS replacement and was disappointed to not find it.

But as time has passed I now see *all* of Linux as the development system; so essentially I use Emacs and a bash terminal (with screen - very cool) for my coding IDE (and it usually rocks, as well).

If I want a program to look pretty, or just want to whip up something pretty fast, I use Python. If I'm fiddling with lots of text files, I might use Perl. And if I'm doing something hard, well I use Lisp since, IMHO it's the best language for expressing an algorithm with.

I've been coding for some 27 years now, I've been through all the styles and systems (I think), used to be an MS fanboy and loved my Visual C++ but honestly I'm far more productive and much happier with Emacs and a terminal.

Anyhow, that's a bit off-topic. No, I never struggle for ideas - just the time to fufill them!

---

### Post by Vox754 on 2008-05-26
> **Alasdair said:**
> 
There are plenty of (supposedly good) GTK bindings for Common Lisp out there, so it should theoretically be possible to build applications that look just like anything else on your desktop. McCLIM also has a GTK backend and there are a few nice apps written for that. Personally I get along fine with the **LTK bindings to the tk toolkit**, and although **tk may have fallen out of the toolkit ugly tree** and hit every branch on the way down **it's simple and it works well.**


About Tk:

I think Tk developers are currently working hard to bring it up to par with other toolkits, or at least to make it "pretty".

Since Tcl/Tk 8.0 (few years ago), Tk has had native look and feel, at least in Windows.
If you browse the web you'll find plenty of programs written with Tk that use the native Windows and Mac OSX widgets.

Strangely, Tk maintained the primitive (ugly) Motif appearance on Linux until 8.4, which is mostly known by perl/python/ruby/-tk. So it's understandable if most Linux developers think of Tk as the ugliest toolkit around.

Since the stable release of 8.5, around December 2007, Tk now loads by default the "Tile" package which provides "themes", thus a really improved appearance on Linux.
Therefore, linking against the new libtcl8.5 and libtk8.5 should improve the appearance of Tk with all languages that have bindings like perl, python, ruby, java, lisp.

I think the developers are working to make it like wxwidgets, that is, to actually use GTK+ (or Qt) if present on the system.

I feel the Tk toolkit has yet a lot to give, because it is very simple for small applications.
A big push would be given to Tk if python started including tk8.5 instead of tk8.4, before python-3.0.

I'm pretty sure I read they are releasing Tcl/Tk8.6, and then they'll make the leap to Tcl/Tk9.0 to bring a load of improvements. Let's wait and see.

---

### Post by LaRoza on 2008-05-26
> **Lau_of_DK said:**
> 

Anyway, if you dont get it by now, I actually recommend that you switch to VB :)

/Lau

It has support for Linux? That is what pmasiar uses (at home, at least). It has support for Java? That is what pmasiar does at work. It has support for Python? That is what pmasiar uses for many things (although I suspect he actually just uses Perl but is ashamed).

VS may be a great tool for Windows development using Windows languages and Windows libraries, but not everyone uses Windows.

Not every type of programming would benefit from the VS RAD environment. In fact, only type of programming does (RAD...).

> **Vox754 said:**
> Can someone please unban lnostdal?!

I demand a public confrontation between these two guys!

I demand the transcript of the public confrontation that I missed on IRC...

---

### Post by Lau_of_DK on 2008-05-26
> **Joeb454 said:**
> :lolflag: Interesting, I don't know how I could parse the idea's though ;)

The Python standard library has got you covered:

[php]
import * from standard

for idea in google:
    if idea.good():
        print idea
[/php]

Or maybe on a more serious note, you could make a forum-crawler, which googles to find forums, then crawls them, indexing threads based on some word statistics and number of replies. If nothing else, it might make for some interesting reading parsing the results :)


/Lau

---

### Post by Lau_of_DK on 2008-05-26
> **LaRoza said:**
> 
I demand the transcript of the public confrontation that I missed on IRC...

Besides the fact that I've lost the log, I dont think anything was said, that was worth repeating :) If lnostdal wants to make the debate public, he's free to do so.

/Lau

---

### Post by slavik on 2008-05-26
It's interesting how someone does not like Lisp because it doesn't have a "pretty" GUI library. The question seems to be missed: "What is the made for?"

Lisp was created to do AI, not GUI. VB was created to do GUI and it is good at that.

Next, we'll start hearing that doing I/O in Haskel is difficult.

No matter what you do to a hammer, it will never become as good of a screwdriver as a screwdriver that was intended to drive screws from the get go.

As for writing a complete client-server program, I can do it in Perl in 30 minutes (gasp: it will be readable and even object oriented ... oooh!!!!), what is your point?

---

### Post by Lau_of_DK on 2008-05-26
> **slavik said:**
> 
As for writing a complete client-server program, I can do it in Perl in 30 minutes (gasp: it will be readable and even object oriented ... oooh!!!!), what is your point?

Alright, you've got 30 minutes starting now.
Looking forward to your next post.


/Lau

---

### Post by slavik on 2008-05-26
> **Lau_of_DK said:**
> Alright, you've got 30 minutes starting now.
Looking forward to your next post.


/Lau
Didn't know I had to refresh forums all the time ...
[http://www.codetoad.com/perl_socket_programming.asp](http://www.codetoad.com/perl_socket_programming.asp)

---

### Post by Lau_of_DK on 2008-05-26
> **slavik said:**
> Didn't know I had to refresh forums all the time ...
[http://www.codetoad.com/perl_socket_programming.asp](http://www.codetoad.com/perl_socket_programming.asp)

Haha :) Well done.

Im stepping down from this discussing, we've drif5ed way too far off topic. 

/Lau

---

### Post by LaRoza on 2008-05-26
> **Lau_of_DK said:**
> Alright, you've got 30 minutes starting now.
Looking forward to your next post.


/Lau
Here is an entire CGI web server in Python:

```

import CGIHTTPServer
import BaseHTTPServer
class Handler(CGIHTTPServer.CGIHTTPRequestHandler): 
    cgi_directories = ["/cgi"]
PORT = 8000
httpd = BaseHTTPServer.HTTPServer(("", PORT), Handler)
print "serving at port", PORT
httpd.serve_forever()

```

---

### Post by LaRoza on 2008-05-26
> **Lau_of_DK said:**
> Besides the fact that I've lost the log, I dont think anything was said, that was worth repeating :) If lnostdal wants to make the debate public, he's free to do so.

/Lau

Round 2 *ding*

I was joking, I really am not interested.

---

### Post by CptPicard on 2008-05-26
> **ZylGadis said:**
> namely preference for python as a solution to everything, 

This is very untrue really... sure there is a strong preference for Python by many people, but it simply shows that Python is a good language for many tasks. I don't think anyone in their right mind would claim that it is the solution to everything.

The Python argument comes in response to two misconceptions, generally:

1) That n00bs are well served starting with C++
2) That people must at some point "graduate" to a "real language" like C++.

Both are speed kiddy fantasies and need to be shot down. A lot of us are actually comfortable enough in our self esteem that we can actually say it out loud that not everything needs to be done the hard way, and additionally, that a lot of the really interesting stuff is actually doable only in high-level languages, or alternatively, implementing the HLL yourself in your low-level language code.

> preference for lisp as a solution to everything,

Well, it IS a very strong language, and the closest to "solution to everything" than anything else I've seen -- YMMV

> preference for anything Paul Graham says

Argue against what Paul Graham actually says, not the fact that people cite him.

> So, perhaps, the best abstraction that can be done is that people differ in their value systems and preferences, and it is meaningless to argue. To each his own, and everyone must reach his own enlightenment.

This kind of an attempt to just water down the arguments by claiming that the issue itself does not exist always smacked of a cop-out by someone who has run out of things to say.

I do believe there is an objective world out there that we can talk about, even in the issue of programming languages. There is subjectivity involved, of course, but if you could just say that everyone has to learn by himself and form their own opinions, we  could just as well close shop here and go home. Algorithms are objective and programming languages are ways to describe and express them... there *has* to be "real" objective information about programming languages that you can communicate to people who still don't know better.

> 
To all of you: show me the code. Nothing else matters in this context. The silliest idiot who did 300 copies of a piece of code in Microsoft Access did more useful work than you did in this thread (myself included).

So you're measuring software development in KLOC, like those infamous airplane builders who measure their design in tons? :)

I prefer to think before I type anything. The more I can actually do work in thought, the less I have to do real manual labour...


> The good part is that none of us are afraid to judge ourselves or others.

Oh, and the judging part is the fun part too.. ;)


> **Lau_of_DK said:**
> Interestingly I got a PM from Wybiral saying the exact same thing a couple of days ago. Im suspecting you guys have been caught up in some pseudo-religious-sect, and no youre trying to reenlist me? :)

Yes, Lars is our evil high-priest...

Although I must admit that Clojure is a sort of sect-ish aberration from his "Common Lisp Catholicism"... we do not quite share all the tenets of his faith, such as having separate namespaces for functions. We're mono-namespaceists.

And yeah, you must try using Swing through Clojure. You can easily choose the point where you leave the Netbeans GUI designer and just start editing your running app from inside code like you usually do in Lisp.

Netbeans is after all closest to what you want regarding VS GUI builder. And if you want to look into Lisp IDEs you should check out LispWorks.

> Im just trying to raise some awareness that there is one area where Linux is falling behind and since Linux is based off a community of developers, future releases could increase in quality exponentially if the tools were improved on.

It's interesting that Linux still is where it is without all these wonderful tools, and Microsoft, with its supposedly great tools, is not like light-years ahead.

Anyway, I do recommend you do get involved in some tools project. If all people had done with Linux was to just point out flaws and expect others to fix them, nothing would ever have happened. I am all for good tools, and would love for you to write them for us ;)


> **Lau_of_DK said:**
> its a matter of producing quality software that is not lacking in either department and more specifically: Having tools that **assist** you in producing this software.

Automated programming is still an open problem. I have a strong suspicion that statically typed languages are a crutch for the compiler and machine, not really for the human being, and the more you move out of that and give the human being more power, the more difficult it becomes for the machine to really help... and it's possible that it really, in sum total, can't.

Frankly, GUI programming is the mind-numbingly boring, dumb part of any software development. All the interesting, "difficult" stuff is somewhere else, and in a properly engineered piece of software, GUI is separated from the engine room anyway. Writing stuff "through" a GUI builder may actually produce GUIs that contain way too much of the application logic, whereas a lightweight GUI builder just gives you the view, nothing else...

I do sort of agree with you in the "IntelliSense" department, but one has to remember that proper genericity in the language and library vastly reduces the API size and makes it more natural to remember, reducing the "discoverability" requirement.

> Just an example: If Visual Studio had Lisp as a project type and could run/compile Lisp programs with the usual ease of GUI design I would probably purchase an XP + Visual Studio, and have that as a boot option for development.

LispWorks. But I don't understand what is wrong with SLIME. If GUI really is the only issue, Lars is right -- you're whining on a marginal thing. You are, of course, welcome to work in something like the CL wxWidgets bindings.. they would be sort of cool really.


And around here you launch into your typical troll-mode that got you the ban from Lars:

> 
 But Lisp, wonderful as it is, is crippled when it comes to producing quality, easily deployable, good looking programs.

Lisp the language (and its various variants) is one of the most remarkable, visionary languages of all time. Software "quality" as measured by something like bug count and engineering elegance can be very, very high indeed. Deployment is not a problem, you can easily roll a .deb. If your only complaint is the GUI, you're making a (perfectly solvable) side-issue into a major flaw of a language itself.

Personally I couldn't care less if the SBCL+Emacs+SLIME combo lacks a good GUI solution -- the completely dynamic programming environment that lets you first build the little parts and then the bigger parts, redefining parts as you need to, is far more powerful than anything I've ever used.

> I've seen several "why is Lisp so under-appreciated?" and people philosofize for hours, but the reason is just this: Its unapproachable, incomplete and at a stage of infancy compared to Quality Languages+IDEs like C#.

:lolflag:

It's under-appreciated because it takes a mindset change, and most people coding today began their education in programming using imperative, static-typed languages, and stopped before they met Lisp.

There is nothing in *Lisp* that makes it "immature" in some GUI sense. Actually, Lisp is wonderful for dynamically building your GUI (see the Clojure+Swing case). You just need the bindings.

You're still mixing together the language and the toolkit in your thinking...

> Of course it would be nice if the truth was that Lisp coders are just super-1337-spectacular compared to everyone else and thats why no-one appreciates their language, but its just not the case-

It is my experience that competent Lispers are also pretty competent at anything related to programming. Maybe it's also because they don't get such a mental block when they get their VS-pacifier taken away from them. This approaches the classic speed kiddy argument that HLL users use HLLs because they are unable to use LLLs, btw.

Do I need to refer you back to my continuations thread? :)

> **Lau_of_DK said:**
> I realised the things you quoted me on and confronted lnostdal with it. His initial reply was "I dont care", his second reply: He banned me from the IRC channel

That, and the above "Lisp is immature" waving-the-muleta-at-bull stuff, and then lecturing him that he should be nicer to people to get some sort of peace of mind so he wouldn't be so grumpy, and that he should find God too while he's at it... ;)

You got what you were after IMO...

---

### Post by LaRoza on 2008-05-26
I will be separating all the off topic posts from this thread when I get home.

So feel free to stay off topic in the meantime, it will all be moved anyway.

---

### Post by pmasiar on 2008-05-26
> **Lau_of_DK said:**
> I actually recommend that you switch to VB :)

I found this remark offensive and demand apology!

---

### Post by Lau_of_DK on 2008-05-26
> **pmasiar said:**
> I found this remark offensive and demand apology!

Alright, receive my sincerest appology! It really wasn't meant as an offense.

And on a broader note, I think a few things I've said in this thread didn't really accurately portray my love for both Linux, Python and Lisp - I absolutely enjoy working with all these things.

I was PMing with Cpt.Picard and although I hate to admit it, he makes a good point that certain things aren't meant to be aimed a "noobs", like for instance there is no "Kernel Design for n00bs IDE", making such a tool would steal time away from more relevant tasks - So point taken.

On the other hand I maintain that certain languages - Like Lisp, which I love- is a bit hard to approach and I do hope that this will be worked on in the future - I might actually put in some work on this myself.

Hope nobody else took offense - I meant no harm.  :whiteflag:

/Lau

---

### Post by LaRoza on 2008-05-26
> **Lau_of_DK said:**
> 
On the other hand I maintain that certain languages - Like Lisp, which I love- is a bit hard to approach and I do hope that this will be worked on in the future - I might actually put in some work on this myself.

Hope nobody else took offense - I meant no harm.  :whiteflag:


Lisp isn't meant to be showy. It is best used to define and write algorithms. VB and VS are used to make simple GUI programs (simple in that the focus is on the interface rather than the nuts and bolts)

Lisp was originally a language entirely built on lambda calculus (Scheme reflects this better than Common Lisp). Lisp's beauty is not in dragging and dropping, but in making a human thought become a computer's. 

We see through that ;)

---

### Post by CptPicard on 2008-05-26
> **LaRoza said:**
> Lisp's beauty is not in dragging and dropping, but in making a human thought become a computer's. 

QFT.

**Emo Picard bursts into tears as he is overcome by emotion**... "Make it so" is Picard's greatest line. It's like Lisp.

---

### Post by LaRoza on 2008-05-26
> **CptPicard said:**
> QFT.

**Emo Picard bursts into tears as he is overcome by emotion**... "Make it so" is Picard's greatest line. It's like Lisp.

Amazing that Picard has been overcome with a statement from the Borg. (Most of the Borg runtime is in a form of Lisp. Of course, this Lisp doesn't have any of the negative parts of Earth lisp as we have assimilated it from more than one planetary culture)

---

### Post by CptPicard on 2008-05-26
> **LaRoza said:**
> Amazing that Picard has been overcome with a statement from the Borg.

It has to be Jean-Luc Picard's secret [Gödel sentence]("http://en.wikipedia.org/wiki/G%C3%B6del%27s_incompleteness_theorems") the Borg learned while assimilating him. You know, like the sleep instruction Data injected in Best of Both Worlds. (It was a fairly pathetic deus ex machina in an otherwise perfect two-part episode...)

It's a bit weird though, I never thought the real fictional Picard was much of a programmer. Maybe Data would have benefited more from studying the interface between humanity and machinery as expressed through Lisp. Personally, I have -- in real life I am much more of a "humanities" kind of person than one would assume from me being a CS geek. That's why I like Lispy things :)

>  (Most of the Borg runtime is in a form of Lisp. Of course, this Lisp doesn't have any of the negative parts of Earth lisp as we have assimilated it from more than one planetary culture)

It's got to be like Clojure then, because of its concurrency support. The Borg Queen could just run countless numbers of Agents and gather their values... mutable state would be Bad for a Borg Collective style entity.

EDIT: Wait... wait... do you mean that *all* planetary cultures eventually create a form of Lisp? That's like that one law of programming that states that any sufficiently complex program eventually incorporates Lisp :)

---

### Post by LaRoza on 2008-05-26
> **CptPicard said:**
> 
EDIT: Wait... wait... do you mean that *all* planetary cultures eventually create a form of Lisp? That's like that one law of programming that states that any sufficiently complex program eventually incorporates Lisp :)

Yes.

It is math and logic, every race has this to some degree.

---

### Post by slavik on 2008-05-26
To answer the first question, autoconf is friggin' awesome. No reading on a page of the app "you need such and such library here" only to find that the link is dead or the library is outdated or somesuch, configure checks for the libraries during compilation and tells you exactly what lib is missing and what version it wants.

---

### Post by Can+~ on 2008-05-26
> **Lau_of_DK said:**
> Hope nobody else took offense - I meant no harm.  :whiteflag:

/Lau

Aw, but I just brought out the popcorn, damnit.

Btw, even if the subject was split, the title "Re: Do You Struggle For Programming Ideas?" is still there.

---

### Post by Rich43 on 2008-05-27
Whats wrong with Mono and MonoDevelop then?

---

### Post by slavik on 2008-05-27
Mono is implementing libraries for which there are or might be patents.

---

### Post by Rich43 on 2008-05-27
Innocent until proven guilty, otherwise its just FUD.

---

### Post by Lau_of_DK on 2008-05-27
> **Rich43 said:**
> Whats wrong with Mono and MonoDevelop then?

Mono might be the next BIG thing to hit Linux, who knows? Its got some strong backing.

Before I deserted Windows entirely, I was very capable in C# and switching to the same language, but where every 2.nd class that I used to use, is now gone, can be frustrating. But time will solve that issue. Secondly, I'm actually very eager to dive into both Python and Lisp. Python is alot of fun and Lisp is downright fascinating! :)

/Lau

---

### Post by pmasiar on 2008-05-27
> **slavik said:**
> on a note of agreement (is this the first time we agreed on anything?)

No, I think we agree all the time: we both prefer simple minimalistic "get out of my way" solutions to our programming problems instead of bloated "in your face" solutions. 

You still like Perl, I am past that stage, preferring Python now. When you will face maintaining your own Perl code which you did not touch for 3 years, I think you will have zen moment and understand me :-)

---

### Post by eFFeeMMe on 2008-05-27
I program small games, I'm never out of ideas :)

---

### Post by slavik on 2008-05-27
> **pmasiar said:**
> No, I think we agree all the time: we both prefer simple minimalistic "get out of my way" solutions to our programming problems instead of bloated "in your face" solutions. 

You still like Perl, I am past that stage, preferring Python now. When you will face maintaining your own Perl code which you did not touch for 3 years, I think you will have zen moment and understand me :-)
[php]
#!/usr/bin/perl -w

#       info_get.pl
#       
#       Copyright 2008 Vyacheslav Goltser <slavikg@gmail.com>
#       
#       This program is free software: you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation, either version 3 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program.  If not, see <http://www.gnu.org/licenses/>.

# This script will return a sorted list of all computers
# within the domain specified in the $domain variable

# use section
use strict;
use Getopt::Std;

## Subroutine section
#print all processed names
sub prnt {
	my @arr = @_;
	for(sort @arr) {
		print "$_\n";
	}
}

# getopt
my %opts = ();
getopts("d:cmwMWv",\%opts);

#usage
# -d group		get list of clients from the 'group' workgroup/domain
# -c			print counts of clients/workgroups
# -m			process members of specified domain (or all members if -d not given)
# -w			process workgroups/domains
# -M			print list of members
# -W			print list of workgroups/domains
# -v			print version and exit

if (defined $opts{v}) {
	print "WINSList v0.1.0.0\n";
	exit 0;
}

#variables
my @wins_list;
my @clients;
my @groups;
my $counter = 0;

@wins_list = `smbtree -NS`; # get a list of domains/clients

if ($#wins_list == 0) {
	print $wins_list[0];
	print "\nCouldn't get any system information\n";
}

if (defined $opts{w}) {
	#process workgroup/domain information
	for (@wins_list) {
		if ($_ =~ m/^([A-Za-z0-9].*)$/i) { push @groups, $1; }
	}
	
	#print information
	print $#groups+1 . " workgroups/domains found.\n" if defined $opts{c};
	prnt(@groups) if defined $opts{W};
}

if (defined $opts{m}) {
	#process member information
	if (defined $opts{d}) {
		until ($wins_list[$counter] =~ m/^$opts{d}$/i) { $counter++ };
		$counter++;
		while ($wins_list[$counter] =~ m/\\\\(.*?)\s/) {
			push @clients, $1;
			$counter++;
		}
	}
	else {
		for (@wins_list) {
			if ($_ =~ m/\\\\(.*?)\s/) { push @clients, $1; }
		}
	}
	
	#print information
	if (defined $opts{c}) {
		print $#clients+1 . " members";
		if (defined $opts{d}) {
			print " of domain " . $opts{d};
		}
		print " found.\n";
	}
	prnt(@clients) if defined $opts{M};
}
[/php]

and (the following script which takes a list of computer names):

[php]
#!/usr/bin/perl -w

#       wins_reverse.pl
#       
#       Copyright 2008 Vyacheslav Goltser <slavikg@gmail.com>
#       
#       This program is free software: you can redistribute it and/or modify
#       it under the terms of the GNU General Public License as published by
#       the Free Software Foundation, either version 3 of the License, or
#       (at your option) any later version.
#       
#       This program is distributed in the hope that it will be useful,
#       but WITHOUT ANY WARRANTY; without even the implied warranty of
#       MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#       GNU General Public License for more details.
#       
#       You should have received a copy of the GNU General Public License
#       along with this program.  If not, see <http://www.gnu.org/licenses/>.

use strict;

my $tmp;
my $ip;
my $mac;
my $count = 0;
my $members = 0;
my %systems = ();

while (<>) {
	chomp;
	$tmp = join '', `nmblookup -A $_`;
	$systems{$_}{ip} = $1 if ($tmp =~ /(\d{1,3}\.\d{1,3}\.\d{1,3}\.\d{1,3})/);
	if ($tmp =~ /([[:xdigit:]]{2}-[[:xdigit:]]{2}-[[:xdigit:]]{2}-[[:xdigit:]]{2}-[[:xdigit:]]{2}-[[:xdigit:]]{2})/) {
		$systems{$_}{mac} = $1;
	}
	else {
		$systems{$_}{mac} = "00-00-00-00-00-00";
	}
}

for(sort keys %systems) {
	printf "%s %s %s\n", $_, $systems{$_}{ip}, $systems{$_}{mac};
}
[/php]

and I dare you to claim that my code is unreadable. :)

---

