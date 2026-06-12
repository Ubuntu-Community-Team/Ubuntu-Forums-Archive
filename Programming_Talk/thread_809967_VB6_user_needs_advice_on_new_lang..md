---
title: "VB6 user needs advice on new lang."
date: 2008-05-27
forum: Programming Talk
---

### Post by lestrade on 2008-05-27
I am having good success moving from WIndows to Ubuntu.  One of the hangups is programming. I am pretty good at throwing together a program in either VB6 or QuickBasic in WIndows/Dos.  I think Python might be an easy switch.  Is there the same kind of environment (IDE) that allows easy debugging. or in the case of VB6, easy form development (control buttons, radio buttons, windows, listboxes, etc) -- or is there some other language that I should consider?
thanks
JP

---

### Post by mssever on 2008-05-27
> **lestrade said:**
> I am having good success moving from WIndows to Ubuntu.  One of the hangups is programming. I am pretty good at throwing together a program in either VB6 or QuickBasic in WIndows/Dos.  I think Python might be an easy switch.  Is there the same kind of environment (IDE) that allows easy debugging. or in the case of VB6, easy form development (control buttons, radio buttons, windows, listboxes, etc) -- or is there some other language that I should consider?
thanks
JP

Try Glade for building GUIs and the Python shell and pdb for debugging. I've never used Windows dev tools, so I don't know how my suggestions compare...

---

### Post by kknd on 2008-05-27
Hi, welcome.

In the GNU / Linux world, programmers usually don't like IDEs, and prefer to choose each part of his toolbox.

It also involves the libraries to use. With some exceptions, like Java, you won't find a language with a default library that have all what you need (network, GUI), but this isn't a problem, since there's plenty of libraries to choose.

If you're looking for scripting languages and GUI, Python (here I prefer Lua, but Python is more popular) and GTK+ (a GUI library). If you want to graphically design the UI, you can use the above with Glade.

For editing code, you can use any editor, but I recommend using Geany or Gedit.

Hope it helps.

---

### Post by pmasiar on 2008-05-27
Yup, Python is excellent choice for Linux-side language.

But it is not about 'not preferring IDE'. It is more about learning really good universal editor and use it with all languages. 

Also, because of free nature, there aren't many companies to sponsor and pay for loads of boring work which goes to commercial IDE.

Pretty decent free Python editor is SPE, but any editor will do, just look for python mode (if nothing else, convert tabs to 4 spaces). Some people like Eclipse, PyDev is Py plugin, and eclipse has plugins for just everything else. Decent commercial IDEs ade WingIDE and Komodo, they might have free 'teaserware' versions to try out.

But of course "real" unix hacker decides to go for vim or emacs, and then wages holy wars against the other side :-) Those editors are not as easy to learn (they are user-friendly, just picky about the friends :-) ), but highly customizable, flexible - and forever! :-)

---

### Post by mssever on 2008-05-27
> **pmasiar said:**
> Pretty decent free Python editor is SPE, but any editor will do, just look for python mode (if nothing else, convert tabs to 4 spaces). Some people like Eclipse, PyDev is Py plugin, and eclipse has plugins for just everything else. Decent commercial IDEs ade WingIDE and Komodo, they might have free 'teaserware' versions to try out.

But of course "real" unix hacker decides to go for vim or emacs, and then wages holy wars against the other side :-) Those editors are not as easy to learn (they are user-friendly, just picky about the friends :-) ), but highly customizable, flexible - and forever! :-)

Even gedit--Gnome's default text editor--is a good editor, especially if you install plugins for it. Don't compare gedit to Windows Notepad. I personally use a combination of gedit and vim. But, as mentioned above, there are many good choices.

(Also, Scribes takes an unusual approach to text editing that you'll either love or hate.)

---

### Post by lestrade on 2008-05-27
Great!! Thanks very much.
JP

---

### Post by slavik on 2008-05-28
pmasiar said Python, hence I will say Perl. You just can't beat true multithreading. :)

---

### Post by LaRoza on 2008-05-28
> **slavik said:**
> pmasiar said Python, hence I will say Perl. You just can't beat true multithreading. :)

When you need true multithreading, no, CPython doesn't deliver, however, I doubt this is a consideration for the average programmer.

---

### Post by dhirajpatra on 2008-05-28
**Hi friend. Welcome to Open Source world.**
Comeout from monopoly and static atmosphere. Try something best in FREE.
Have you ever tried PHP. You can start [PHP]("http://php.net") development if you already have some ASP knowledge. You will also get some help to start a bright career in PHP [LAMP]. Visit my blog. Regards.

---

### Post by DavidBell on 2008-05-28
You might also look at Gambas and RealBasic, I haven't used either of them but my understanding is roughly Gambas is 'VB for Linux' targeted mainly at QT GUIs though GTK too I think (it's free); and RealBasic is 'VB for cross-platform' (costs $600, there is a demo, at one time the linux version was free and may still be).

I am yet to find an IDE in linux where the 'I' stands for 'Integrated' in a way that is comparable to VB.

DB

---

### Post by Lau_of_DK on 2008-05-28
> **lestrade said:**
> I am having good success moving from WIndows to Ubuntu.  One of the hangups is programming. 

Hey Lestrade,

Finally! Someone who understands me! :)

First of all, moving from Windows to Linux in terms of programming can be both an eye-opening experience, and very frustrating depending on how you approach it - I'll try to steer you out of repeating my experience.

First off, finding a fully integrated IDE that incorperates a nice editor, some type of intellisense, a GUI designer, automatic building/compiling is a very rare thing in Linux. If you like C++ then I highly recommend the Qt4 Eclipse Integration, it has all these things. There's a catch though: Youre missing out on some of the fantastic things that are available on Linux.

1) Python
Python is very easy to pick up, but still powerfull. Natively it supports things as decorators, generator expressions and lambdas, which are all things you need to Google, but they will change the way you code all the way down to how you think about functions. At least it did for me. Note: Its also very possible to do GUIs in Python (even Qt ones) but this I still consider this functionality as unapproachable and incomplete.

2) Lisp
I think its natural to be facinated when you see something extraordinary, like an earthquake or some such phenomena, but Lisp will hit you in the same way coming from Windows. Although I dare and double dare you to produce a nice GUI with this language, its a pleasure to work with because of its flexibility, its a programmable language where youre constantly making additions to the very language, to shape it around your style of coding and needs. In Lisp you'll also want to get familiar with Lists, Lambdas and the all powerfull Macros. These are not Macros like any other you've seen though. One thing you could try to get an impression of some Lisp code, is go back a little in the Forum and find the thread "Programming Challenge #12: Computational Geometry" and find Alasairs Lisp solution, its brilliant.

So real quick, links to get you started.

**Eclipse/C++:**
"sudo apt-get install eclipse eclipse-cdt"
Link: [Download integration plugin]("http://trolltech.com/developer/download/qt-eclipse-integration-linux.x86-gcc3.3-1.4.0.tar.gz")
Link: [Install manual]("http://trolltech.com/developer/downloads/qt/qteclipse-installmanual")

**Python:**
Python thankfully comes included in Ubuntu. For an IDE I recommend the Pydev plugin in Eclipse. Im sure 100% sure (but I'll check later) but I think its installed via
"sudo apt-get install eclipse-pydev" [**confirmed**]

**Lisp:**
First, I really recommend that you read this, especially Chapters 1 - 3: [Practical Common Lisp]("http://gigamonkeys.com/book/") 
Second, if you're intrigued and want to get going, follow this guide exactly: [Getting started]("http://common-lisp.net/~lnostdal/writings/sbcl.html")


Hope you enjoy the switch to Linux,
/Lau

---

### Post by irrdev on 2008-05-28
If you are going to use Python, I recommend for an IDE that you use Eclipse in conjunction with the Pydev Eclipse plugin. It has tons of great features. ;)

---

### Post by kalaharix on 2008-05-28
If you come from VB6 (as I do) you will be fine with Gambas. I have found it very reliable and let down for the new convert only by the documentation (no criticism: it is a community effort and I guess I am part of that community!). I am not a fancy programmer and my needs hinge around data access and manipulation.

REALBasic is free for single user data on Linux and is very easy to install. I just don’t like the IDE. Whilst I am sharing my likes and dislikes: I think Glade sucks.

---

### Post by pmasiar on 2008-05-28
> **Lau_of_DK said:**
> 
1) Python ...I still consider this functionality as unapproachable and incomplete.


Compared to what?

---

### Post by aquavitae on 2008-05-28
> **pmasiar said:**
> Compared to what?I'll add my voice to that! Compared to fortran maybe? ;)

Since nobodys mentioned it - I like using Eric IDE. Good project management, integrated vcs, debugger, compiler... I never use interface designers though - I like the control of coding it myself, and anyway I think its quicker!

---

### Post by beatmaster on 2008-05-28
i came from a VB6 and classic ASP platform too and when I jumped to PHP and mysql I thought it was pretty easy... the XAMPP packaged eveything you will need from PHP, mysql and filezilla (and more!)

if you need to make windows like applicatios with the GUI and stuff you can try TCLtk.  but if you came from V that will be hard and unnatural... I use Netbeans to make GUIs, it supports perl, java and even ruby!

---

### Post by beatmaster on 2008-05-28
i am not sure if the programming tools from "Active" like ActivePerl will work.  if you are a VB programmer like me then you might be after the IDE and not really the sophisticated PL capabilities like threading.

---

### Post by pmasiar on 2008-05-28
> **beatmaster said:**
> i am not sure if the programming tools from "Active" like ActivePerl will work.  if you are a VB programmer like me then you might be after the IDE and not really the sophisticated PL capabilities like threading.

How are language capabilities like threading (which is irrelevant to beginner IMNSHO) related to IDE? 

Do you know ActiveState Komodo? it is pretty decent IDE, as IDE's go, but how is IDE related to Perl? 

And BTW, OP is decidedly mowing away from VB, unlike you OP does not (I hope) want to be a Blub programmer. :-)

---

### Post by Mickeysofine1972 on 2008-05-28
I personally like to use Python for GUIs as I dont often have to do anything time critical and it has a pretty good set of libraries to get you going and can be extended if needs be, (not really that likely though as it has such good libs).

I would go for IDLE as an IDE though as it just doesn't seem to fit my sense of workflow, I use Scite as it has a terminal built in that lets you run what you just wrote. I also use wxGlade to build my GUI then get it to generate the code.

The only editors that seem to have anything like proper code complete is Code::Blocks and gPHPEdit but neither are good for Python.

Thats my 2p anyway :D

Mike

---

### Post by days_of_ruin on 2008-05-28
> **pmasiar said:**
> Compared to what?
+1.I haven't gui programmed in any language but python but I don't
see any other language being easier.

---

### Post by Mickeysofine1972 on 2008-05-28
> **days_of_ruin said:**
> +1.I haven't gui programmed in any language but python but I don't
see any other language being easier.

I really hate to say this but VB is easier to programing as you have the ability to click on a form element and go straight to the method and start programming then you can run it as soon as you wrote it by clicking a button.

That might not seem much but I saves time and energy and programming is all about holding loads of context in your head, which is made harder by extra steps in the development process.

If someone would build that in to Glade then I could scratch that last statement.

Mike

---

### Post by slavik on 2008-05-28
> **Mickeysofine1972 said:**
> I really hate to say this but VB is easier to programing as you have the ability to click on a form element and go straight to the method and start programming then you can run it as soon as you wrote it by clicking a button.

That might not seem much but I saves time and energy and programming is all about holding loads of context in your head, which is made harder by extra steps in the development process.

If someone would build that in to Glade then I could scratch that last statement.

Mike
QFT!!! (Even though I don't like VB either).

---

### Post by nvteighen on 2008-05-28
I coded some time ago in VB4 and VB6... I really liked the GUI, but never the language itself. Although I learned to program using various BASIC, I even like Javascript much more than VB or QB. BASIC syntax seems somehow incoherent (QBASIC: INPUT$ "Type your name"[color="red"],[/color] a$... PRINT "My name is"[color="red"];[/color] a$)

---

### Post by pmasiar on 2008-05-28
> **Mickeysofine1972 said:**
> but VB is easier to programing as you have the ability to click on a form element and go straight to the method and start programming then you can run it as soon as you wrote it by clicking a button.

That might not seem much but I saves time and energy and programming is all about holding loads of context in your head, which is made harder by extra steps in the development process.

1) there is programming beyond creating a GUI for something - in my experience, **most** programming is non-GUI related.

2) such "wizards" etc make for "trained monkey" programming, where you copy/paste and autogenerate code, instead of properly factoring things out.

That might not seem much but **properly refactoring** saves time and energy **when you have to maintain the code later** and programming is all about **writing the code in such obvious way** that you **do not have to hold loads of context in your head** :-)

---

### Post by slavik on 2008-05-28
> **pmasiar said:**
> 1) there is programming beyond creating a GUI for something - in my experience, **most** programming is non-GUI related.

2) such "wizards" etc make for "trained monkey" programming, where you copy/paste and autogenerate code, instead of properly factoring things out.

That might not seem much but **properly refactoring** saves time and energy **when you have to maintain the code later** and programming is all about **writing the code in such obvious way** that you **do not have to hold loads of context in your head** :-)

1. I agree, but then I point you back to an article that you linked to by Joel Spolsky where he said that in the Windows culture, the GUI comes first and command line is an afterthought.

2. Then lets throw out all UML programs and UML code generators!!!

---

### Post by pmasiar on 2008-05-28
> **slavik said:**
> 1. I agree, but then I point you back to an article that you linked to by Joel Spolsky where he said that in the Windows culture, the GUI comes first and command line is an afterthought.

You mean, in Windows nice buttons come first and any functionality is just afterthought? :-)

I was not talking about commandline interface to any code - I was talking about refactoring the **code**.

---

### Post by scourge on 2008-05-28
I always disliked the VB programming language, but for creating small applications with a GUI, it was very simple to use: Drag widget on the form, double-click widget, write code, and it works. Compared to that, most gui designers for Linux are frustrating. QT Designer is pretty awesome, but Glade and wxGlade are just painful to use.

---

### Post by Mickeysofine1972 on 2008-05-29
> **pmasiar said:**
> 1) there is programming beyond creating a GUI for something - in my experience, **most** programming is non-GUI related.

2) such "wizards" etc make for "trained monkey" programming, where you copy/paste and autogenerate code, instead of properly factoring things out.

That might not seem much but **properly refactoring** saves time and energy **when you have to maintain the code later** and programming is all about **writing the code in such obvious way** that you **do not have to hold loads of context in your head** :-)

1) Check the context I said that,(I know you dislike holding context in your head but its an important part of all language and interaction).

2) Isn't re-usable code snippets part of most OOP languages? after all, do you re-write your printf function every time you use C? (oops forgot I shouldn't suggest you use anything other than Python, that might start a flame war LMAO)

Mike

---

### Post by aquavitae on 2008-05-29
> **Mickeysofine1972 said:**
> 1) Check the context I said that,(I know you dislike holding context in your head but its an important part of all language and interaction).
I agree with pmasiar. Most libraries do all the hard gui work for you, so, in comparison to the entire program, there is usually only a small part of gui code. I also tend to hold a lot of stuff in my head, but when I stick to conventions (even just my own), minimize repetition and document code well (separate issue, I know!) I find far less bugs, and they're easier to find.

> 
2) Isn't re-usable code snippets part of most OOP languages? after all, do you re-write your printf function every time you use C? (oops forgot I shouldn't suggest you use anything other than Python, that might start a flame war LMAO)

Mike
They're a useful device for saving on typing, not a substitute for well structured code. And language has nothing to do with it.

Is this maybe going a bit off topic?:)

---

### Post by Mickeysofine1972 on 2008-05-29
> **aquavitae said:**
> I agree with pmasiar. Most libraries do all the hard gui work for you, so, in comparison to the entire program, there is usually only a small part of gui code. I also tend to hold a lot of stuff in my head, but when I stick to conventions (even just my own), minimize repetition and document code well (separate issue, I know!) I find far less bugs, and they're easier to find.


They're a useful device for saving on typing, not a substitute for well structured code. And language has nothing to do with it.

Is this maybe going a bit off topic?:)

I agree will everything you have said. Although, I dont think you quite got the context that I was saying that under :lolflag:
I am a particular fan of Apps Hungarian which has made a huge difference to my C++ projects since I started to use it.

Finally, there is no substitute for well structured code as you say but surely once written you would not think twice about re-using your good code even if it meant cut&pasting it into another project?

Mike

---

### Post by pmasiar on 2008-05-29
> **Mickeysofine1972 said:**
> 1) Check the context I said that,

maybe it's **you** who should clear out context, if you were apparently misunderstood?

> I shouldn't suggest you use anything other than Python, that might start a flame war LMAO)

I am not sure why you choose to say this attack  on people who like Python. You know very well that **I** do not oppose other languages, just IMHO most posters would be better server by Python, in average. I used (and still use) many many other languages, and my all-time favorite is Forth. Python is just so much more practical. :-)

---

### Post by Mickeysofine1972 on 2008-05-29
> **pmasiar said:**
> most posters would be better server by Python, in average.

Perhaps if you could read and write English properly you might calm down and stop trying to be sarcastic and critical.

Are you even you know what I said? :lolflag:
BTW I'm not attacking Python and that was never suggested either. go back and re-read my posts before you get shirty.


Mike

---

### Post by pmasiar on 2008-05-29
> **Mickeysofine1972 said:**
> Perhaps if you could read and write English properly you might calm down and stop trying to be sarcastic and critical.

You again choose personal attack against clearing misunderstanding.

English is not between my first 3 languages. Maybe if you learned some other language, you will have more appreciation for people who learned your native language and use it to communicate with you for your convenience.

---

### Post by Wybiral on 2008-05-29
> **Mickeysofine1972 said:**
> I really hate to say this but VB is easier to programing as you have the ability to click on a form element and go straight to the method and start programming then you can run it as soon as you wrote it by clicking a button.

That might not seem much but I saves time and energy and programming is all about holding loads of context in your head, which is made harder by extra steps in the development process.

If someone would build that in to Glade then I could scratch that last statement.

Mike

What's the point in having something that works when you can have something that looks pretty? The trick is to combine your functionality with your interface so they become inseparable, this is the best way to write sane and reusable code.

</sarcasm>

The problem is that your GUI _should_ be an afterthought, not the premise of your entire design. When you use those "point-and-click" then "fill-in-callback" editors, you're building your program around the GUI, instead of building the GUI around the program. Does that make any sense? The sane way is to start on your code, the raw functionality of your application. Write everything as though it were intended to be a library or a module (reusability in mind), and only AFTER it works should you ever worry about hooking it into some callbacks.

---

### Post by nvteighen on 2008-05-29
> **Wybiral said:**
> 
The problem is that your GUI _should_ be an afterthought, not the premise of your entire design. When you use those "point-and-click" then "fill-in-callback" editors, you're building your program around the GUI, instead of building the GUI around the program. Does that make any sense? The sane way is to start on your code, the raw functionality of your application. Write everything as though it were intended to be a library or a module (reusability in mind), and only AFTER it works should you ever worry about hooking it into some callbacks.

In summary: the GUI should work as a front-end. Think of how many applications in your GNOME or KDE or whatever desktop are just GUIs for something that works behind silently that also can be accessed from a command-line application.

---

### Post by LaRoza on 2008-05-29
> **Mickeysofine1972 said:**
> Perhaps if you could read and write English properly you might calm down and stop trying to be sarcastic and critical.

Are you even you know what I said?
BTW I'm not attacking Python and that was never suggested either. go back and re-read my posts before you get shirty.


Please don't point out trivial errors in English in otherwise perfect posts. Also, don't use misspellings to avoid the automatic censor (don't use those words either). All of this is in the Code of Conduct...

---

### Post by lestrade on 2008-05-29
As the OP I want to say thanks and I should have known that I would start a war.  However, I did get a LOT of good information. Now let's calm down and close out this thread.

JP

---

### Post by Mickeysofine1972 on 2008-05-30
> **LaRoza said:**
> Please don't point out trivial errors in English in otherwise perfect posts. Also, don't use misspellings to avoid the automatic censor (don't use those words either). All of this is in the Code of Conduct...

I meant no disrespect to him but he has consistently attacked me and my ideas for over a year now and quite frankly I am sick of it!

Don't believe me? 

[http://ubuntuforums.org/showthread.php?t=743119](http://ubuntuforums.org/showthread.php?t=743119)
[http://ubuntuforums.org/showthread.php?t=455561&page=3](http://ubuntuforums.org/showthread.php?t=455561&page=3)

These are only examples, if you search the forums you will see that this kind of attitude is very common from him.

He has also on more than one occasion attempted to form elite group of so call 'forum experts' who are supposed to be people who have been approved as being more trust worthy than other in their opinions:

[http://ubuntuforums.org/showthread.php?t=597210](http://ubuntuforums.org/showthread.php?t=597210)
[http://ubuntuforums.org/showthread.php?t=597268](http://ubuntuforums.org/showthread.php?t=597268)

Those of you whom where involved in those debacles will remember how they ended.

Before you go taking the moral high ground you might consider this video from the developers of 'subversion' on how to protect you open source community before you are so quick to judge my actions:

[http://video.google.co.uk/videosearch?q=open+source&hl=en&sitesearch=#](http://video.google.co.uk/videosearch?q=open+source&hl=en&sitesearch=#)

I agree this is the end of this thread, and I agree this has to stop, I am sorry towards OP that I did this here, but if someone doesn't take a stand against this deliberate attempt to enforce his 'one true way' attitude, then when will the stand made?

When will we all have a chance to contribute to this forum without arrogant fools trying to steer people into some hierarchy where you have to be in the  boys club to have a valid viewpoint.

The underlying attitude of his is this:

"I am always right and your always wrong. And if you have a idea I haven't had yet then I will oppose it."

Tell me how many Open source project he's involved in? my guess is its zero.

With all due respect to the forum staff I have respect and support for every member of this community, and I care about it, BUT I will not stand for this outright opposition to my and others efforts to share ideas, (wright or wrong or even just experimental).

King Regards

Mike

---

### Post by Lau_of_DK on 2008-05-30
Mickey,

I can see where you're coming from, and being a fundamentalist at heart, I also get why pmasiar says the things he does. To be honest a forum like this contains so many zealous programmers who spend so much time and energy on "their thing", so we're bound to bump heads once in a while. I think that the attitude of the forum (or atmosphere) should be safeguarded to help keep it productive.

I imagine one way of doing this, is that if you have a problem with pmasiar, take it up with him 1on1 in private messages, and do it as a friend sharing in the same online community, where you have the common goal of keeping things friendly and productive. (and I actually think you guys could agree on this). 

And if you and pmasiar (or whoever) cannot reach an agreement either stay clear of public confrontations, or pass the case on to a moderator, or somebody who can enforce the code of conduct or if need be modify it to meet the circumstances.

How does that sound?
/Lau

---

### Post by Migs on 2008-05-30
Maybe after this post i will have less friends here but why could the topicstarter not choose a solution in between instead of learning something completely new. 

Why not stay with VB and continue with Mono? [http://www.mono-project.com/Main_Page](http://www.mono-project.com/Main_Page)

All your requests about userforms are being answered.

---

### Post by Mickeysofine1972 on 2008-05-30
> **Lau_of_DK said:**
> Mickey,

I can see where you're coming from, and being a fundamentalist at heart, I also get why pmasiar says the things he does. To be honest a forum like this contains so many zealous programmers who spend so much time and energy on "their thing", so we're bound to bump heads once in a while. I think that the attitude of the forum (or atmosphere) should be safeguarded to help keep it productive.

I imagine one way of doing this, is that if you have a problem with pmasiar, take it up with him 1on1 in private messages, and do it as a friend sharing in the same online community, where you have the common goal of keeping things friendly and productive. (and I actually think you guys could agree on this). 

And if you and pmasiar (or whoever) cannot reach an agreement either stay clear of public confrontations, or pass the case on to a moderator, or somebody who can enforce the code of conduct or if need be modify it to meet the circumstances.

How does that sound?
/Lau

I agree, but to be honest I even though of not posting on this thread when I saw his name in the previous posts. The I thought why should I avoid contributing just because he might be watching and I would risk attracting his attention?

If you look at the posts I quoted I've never asked for this kind of treatment from him and he has often done the same to other too.

I would do this privately but whats the point, its already in the public domain and I dont think its good for newer members to see him going around the forums randomly castigating members without any visible consequences. If a bully doesn't get put in his place publicly the rest might think there is no form of justice in our community and that is poison to our group. 

After all who's next? you, someone else? and who will be watching when this happens?

I have the spine to stand up and fight for the right thing and I have done so. 

If this costs me my account on this forum then so be it but I will never be known as a coward that allows bullies to walk over me in the name of keeping the peace.

The reason I started referencing the past threads is that I dont think that the forum staff have notice the trend that occurring in this forum of 'RTFM' type answers and arrogance of more mature members of which pmasair is a more prominent member.

I really enjoy that fact that we have a good amount of altruism in our forum but its not good that we have some whom are only here to massage their egos and  participate in posturing for the sake of thier so called 'forum expert' persona

Mike

---

### Post by Wybiral on 2008-05-30
> **Mickeysofine1972 said:**
> I agree, but to be honest I even though of not posting on this thread when I saw his name in the previous posts. The I thought why should I avoid contributing just because he might be watching and I would risk attracting his attention?

But you're no longer contributing in this thread, now you're just arguing with pmasiar :p

Did you happen to read my response as to why "point and click" VB-style tools suck? I think pmasiar was getting to the same points (tbh, I don't think he was even that abrasive in this thread, he was just arguing against your post, which is normal in a public forum). Keeping grudges is bad for your health and bringing up dead arguments is bad forum etiquette.

---

### Post by Mickeysofine1972 on 2008-05-30
> **Wybiral said:**
>  Keeping grudges is bad for your health and bringing up dead arguments is bad forum etiquette.

When he stops doing it, I will forget he keeps doing it, until he stops, he will remind me. And as for grudges? who is it that keep attacking who? Find the post where I deliberately come in guns blazing with him? you wont find one.

And finally, just because I have an issue with him does not mean I disagree with what he said, I just don't like his attitude. Its hard to agree with anyone who doesn't have a basic respect for others dignity, even if they have something valid to say.

I happen to agree with the way Python and Unix/Linux developers work but if you look at the context we where talking about making guis and I said that I preferred the form building then installing functionality approach and wished you could have that choice of development workflow in Glade.

But now that we are split in our purposes I can see that his work in our community is done.

Mike

---

### Post by ugm6hr on 2008-05-30
> **lestrade said:**
> As the OP I want to say thanks and I should have known that I would start a war.  However, I did get a LOT of good information. Now let's calm down and close out this thread.

JP

Sensible sentiments.

Moderator input: This thread is now closed.

Individual posts are being reviewed.

---

### Post by LaRoza on 2008-05-30
> **Mickeysofine1972 said:**
> I meant no disrespect to him but he has consistently attacked me and my ideas for over a year now and quite frankly I am sick of it!

He has also on more than one occasion attempted to form elite group of so call 'forum experts' who are supposed to be people who have been approved as being more trust worthy than other in their opinions:

When will we all have a chance to contribute to this forum without arrogant fools trying to steer people into some hierarchy where you have to be in the  boys club to have a valid viewpoint.

Tell me how many Open source project he's involved in? my guess is its zero.

With all due respect to the forum staff I have respect and support for every member of this community, and I care about it, BUT I will not stand for this outright opposition to my and others efforts to share ideas, (wright or wrong or even just experimental).


Those two threads are old and closed.

I don't think it had anything to do with being elite. On this forum, anybody that responds is usually considered an "expert" in some way by new programmers. So, if someone posts a question, someone who knows nothing is the same as a true expert. So, because of the internet, a programmer with many years of programming experience (pmasiar) is the same as a self taught programmer with no real contributions or work eperience in the field (me) and a clueless person posting whatever keys they happened to press (it happens). 

pmasiar is a programmer with many years experience. This means he will have strong opinions based on experience, instead of what his teacher taught him or what he was taught. His strongly formed opinion are there for a reason, and I am grateful I am able to learn from people like him. (I doubt his intention was to form a boy's club ;))

Just because I may not agree with what he may say all the time, I do find it valuable to listen (so to speak) to his reasons. 

As far as open source projects he's involved in, I know of one. See his sig. (It is quite cool)

Sharing ideas goes both ways. Even though I still use SQL and PHP, I find his posts about ORM and MVC most interesting (and if I were working on larger projects, I'd probably use such predefined frameworks)

---

