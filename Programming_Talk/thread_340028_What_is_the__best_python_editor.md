---
title: "What is the  best python editor?"
date: 2007-01-16
forum: Programming Talk
---

### Post by thenetduck on 2007-01-16
Hi, 
  I am learning python and am trying to find the best IDE out there for it. Because I'm new to it, i want something that has all the API docs included with the IDE so I can read them as I learn etc. Even better if it does something like Eclipes with finishing part of the code. Anyway this would be very helpful thanks, 

 The Net Duck

---

### Post by eteran on 2007-01-16
I'm using SPE since a short while, its definitive worth a look.
The best Editor, is the one _you_ like best.

---

### Post by gh0st on 2007-01-16
I asked a similar question a while ago and most people seemed to say Stani's Python Editor (SPE) was the best free Python IDE. You can get it from Synaptic easily, I installed it and I have to say I like it. It's a nice IDE with some good features but it's not too bulky in my opinion. Might be worth a try.

You're bound to get some people telling you to use gedit or something like that as well because they argue you can't learn anything if an IDE does too much for you. It's a fair point I suppose but it's a personal choice. Personally I choose SPE :D

---

### Post by rolando2424 on 2007-01-16
I use good old Gedit and IDLE (used edit.com in Windows once :D)

---

### Post by deadlydeathcone on 2007-01-17
I went through the same thing about a month ago and came to the conclusion that while SPE is definitely the best open source IDE, [Wing]("http://wingware.com/") surprisingly beats it by a lot.  It's unfortunately commercial, but there's a 30 day trial and you can even get it for free if you're an OSS developer. For starters it has the best command completion I've come across along with excellent documentation and a lot of polish.

Still I don't really like full IDEs and use Geany (it's like a slightly more IDEish Gedit) along with deskbar and the devhelp plugin for documentation. In the same vein [Scribes]("http://scribes.sourceforge.net/download.html") looks cool, although I haven't tried it yet.

---

### Post by maxamillion on 2007-01-17
I've been a fan of coding in gvim for some time but when I recently took on learning python I wanted something a little more friendly for development, especially since python is so interactive during development so I tried DrPython and I love it. I think anyone looking for a python IDE should give it a shot and see what they think, it is available in the repositories so you can install it via apt-get, aptitude, or synaptic. (Note: the package name is all lower case for installation)

---

### Post by gummibaerchen on 2007-01-17
> **deadlydeathcone said:**
> Still I don't really like full IDEs and use Geany (it's like a slightly more IDEish Gedit) along with deskbar and the devhelp plugin for documentation.

Same here, Geany + Devhelp. But Geany has also some **very** annoying bugs :(
Never STOP a Python program with the GUI button, that will **** your system and every program will close for example...

> **deadlydeathcone said:**
> In the same vein [Scribes]("http://scribes.sourceforge.net/download.html") looks cool, although I haven't tried it yet.

And it is written in Python itself afaik.

---

### Post by 56phil on 2007-01-17
I'm not sure about best, but I use and like eric. It's free amd easy to use.

---

### Post by mrdean on 2007-01-17
I tried several python editors and I found out that jEdit was best to me. Some IDEs I tried were a bit buggy.

---

### Post by micahkoga on 2007-01-17
Just tried out Scribes. It's looks pretty good. Fast and Slim. I'm still trying to get used to not having tabs. I usually like having a bunch of files open at once, but they all open as separate windows. Other than that, I like it.

---

### Post by jblebrun on 2007-01-17
If you're a geek, learn vim, and use gvim! It's a bit janky at first, but it's SUCH a powerful editor, once you know how to use it. 

You could try emacs, too. I think emacs is comparably powerful, even though I don't use it. If you're a fan of Lisp-like languages, you'll definitely like emacs.

---

### Post by pmasiar on 2007-01-17
to start with python IDLE if perfectly fine - and is included with install. So don't waste your time searching for IDE - dive into python!

to edit more complicated code (beyiond page or two), IMHO editor with indent guidlines is a must - because whitespace is significant in Python. SPE is good example. Once you seen that, you will require guidlines in all your editors.

Having syntax-aware editor, which can create code outline from function names is big plus when editing code modules bigger than couple pages - if you like it. Some people prefer simple universal code editors - that's why we have so many of them :-)

You can use any code editor you like (avoid plain text editors like notepad), just make sure you do not mix tabs and spaces. Usually people set editor to replace tab with either 2 or 4 spaces - default 8 is just way too much. SciTE is good example of lightweight universal code editor - and written in python too.

Vim has extra feature: you can write macros in python. I plan to learn it sometimes, honest. :-) not now :-(

It just makes sense to consider editor written in python, or extendable with python - so if you want to add some feature, or fix a bug, you don't need to do it in different language. so jEdit is nice, but unless you use for something else - don't start it for python only. Nothing personal against jEdit - I used it for a while :-)

---

### Post by jaboc83 on 2007-01-17
VIM with syntax highlighting on! The only way to go :)

---

### Post by Wybiral on 2007-01-17
> **pmasiar said:**
> ...(avoid plain text editors like notepad)...

*** Shakes head in disapproval ***

---

### Post by jblebrun on 2007-01-17
> **Wybiral said:**
> *** Shakes head in disapproval ***

Disapproval of notepad, or the suggestion?

---

### Post by Wybiral on 2007-01-17
I do almost all of my programming in simple text editors... Disapproval of someones ability to say that a text editor isn't efficient enough for programming... Especially if you know the language, why do you need all the other junk (syntax highlighting/auto complete/etc...)?

And python... It's so easy, and you don't even have to compile anything, what could possibly make text editors so absurd to people?

---

### Post by Mirrorball on 2007-01-17
I know I can't do anything without syntax highlighting. It's extremely useful. Sometimes I forget to close a comment block or a string and with syntax highlighting these mistakes are obvious.

---

### Post by pmasiar on 2007-01-17
> **Wybiral said:**
> I do almost all of my programming in simple text editors... Disapproval of someones ability to say that a text editor isn't efficient enough for programming... Especially if you know the language, why do you need all the other junk (syntax highlighting/auto complete/etc...)?

And python... It's so easy, and you don't even have to compile anything, what could possibly make text editors so absurd to people?

I like simple editors too. But when beginners asks me what is best for her, I do not force *my* preference - I say what in my best opinion is *best for her* - not me. *Especially* if she does not know the language.

Or you try tell me I should let beginner to learn that tabs and spaces don't mix by editing her first program in notepad? It's plain evil IMHO. She *will* mix tabs and spaces (been there done that), *will* get confused and may give up on python or programming. With IDLE (or any other decent python-aware editor), learning curve is not as steep and learning is more fun. And we are here to have fun - at least i am :-)

---

### Post by phossal on 2007-01-18
> **Wybiral said:**
> I do almost all of my programming in simple text editors... Disapproval of someones ability to say that a text editor isn't efficient enough for programming... Especially if you know the language, why do you need all the other junk (syntax highlighting/auto complete/etc...)?

And python... It's so easy, and you don't even have to compile anything, what could possibly make text editors so absurd to people?

You do know where this is going, right? After all, the guy has a reputation. Not only does your opinion not count, in the end he whines about no one listening to *his* opinion. It's lose/lose. Get out while you can. lol The only good that can come of it is that you'll vent in a few angry posts. (Let me tell you, it was worth the ban) ;)

[edit] 99% of everything you *should* do in Python is documented as an example in an OReilly book. Skip the IDE; just copy and paste the code you need. You can spend the time savings learning a *man's* language.

---

### Post by ianare on 2007-01-18
My favorite is the editor  found in boa-constructor. the GUI builder is pretty outdated and buggy, but as an editor it's hard to beat. Otherwise gEdit or notetab++.

If you're using a plain text editor, make sure to set "insert tabs as spaces", and to set the tab width to 4. Otherwise you may get problems.

---

### Post by gummibaerchen on 2007-01-18
What I think is pretty important for a good Python Editor are only 3 things.

1) The ability to show "Spaces" and "Tabs" (as grey dots and arrows or whatever)
2) Insert 4 "Spaces" when "Tab" is pressed
3) Syntax highlighting

That's all ;)

---

### Post by thenetduck on 2007-01-18
Wow thanks, I think I found what I was looking for :). I got another question about Python's API. I find it well a little tricky to both find and understand. Does anyone know of a good site to look up good documentation for Python? In particular Tkinter? I ususally can google all of this (the docs for Java are really good) but have been having trouble with Python. For now I have been using this [http://wiki.python.org/moin/Intro_to_programming_with_Python_and_Tkinter]("http://wiki.python.org/moin/Intro_to_programming_with_Python_and_Tkinter")

Thanks, 

The Net Duck

---

### Post by ianare on 2007-01-18
personally, i can't stand tkinter. overly complicated and wordy, not enough features, and looks awful on every system you run it on.
only advantage is it's installed with every python install.

Take a look at wxPython

[http://en.wikipedia.org/wiki/WxPython](http://en.wikipedia.org/wiki/WxPython)

---

### Post by gpolo on 2007-01-18
well.. I don't love tkinter at all, but I have used it before for a comercial program. Sometimes you don't need things wxPython has, and tkinter comes with Python. So, use what will do better. 
If you are just doing projects for yourself or things like this, wxPython would be a good recommendation then.

now, to the question.. I forgot if answered on this topic or not ;P But, like the other post I said.. for small projects any editor will do good, and preferable one without much features, so you can really learn Python. For a not so small project, when you start getting lost, I would go with Eclipse. I don't tests all editors out there, I just tested some and liked Eclipse and that is why I'm recommending it.

---

### Post by gummibaerchen on 2007-01-18
> **gpolo said:**
> well.. I don't love tkinter at all, but I have used it before for a comercial program. Sometimes you don't need things wxPython has, and tkinter comes with Python. So, use what will do better. 
If you are just doing projects for yourself or things like this, wxPython would be a good recommendation then.

now, to the question.. I forgot if answered on this topic or not ;P But, like the other post I said.. for small projects any editor will do good, and preferable one without much features, so you can really learn Python. For a not so small project, when you start getting lost, I would go with Eclipse. I don't tests all editors out there, I just tested some and liked Eclipse and that is why I'm recommending it.

Why does everyone say, Tkinter is included in Python?

At least speaking for Debian and Ubuntu it is not included in "python-minimal", and you need an import for it, so it's not really really included.

Just because it's mantained from py.org (is it anyway?) doesn't mean it's "included in every Python installtion", or?

Maybe I am completely wrong here, then pls excuse me ;)

---

### Post by ianare on 2007-01-18
whoa you're right. i had no idea debian/ubuntu removed it. when you get python from python.org it is included, at least in windows and mac.

---

### Post by gpolo on 2007-01-18
You can separate a application in several pieces, but that doesnt mean Tkinter isnt in Python source

---

### Post by thenetduck on 2007-01-19
I have been learning a little bit Tkinter and haven't really like the way it looked. What is the most popular GUI package that most people program with? I think xwPython is what is used most because it looks similar to most applications I see in Ubuntu.

---

### Post by maddog39 on 2007-01-19
Yeah, I love wxPython, its very easy and the code is normally clean and uncluttered compared to PyGTK. It also doesnt require many lines of code to make a fairly intuitive GUI.

---

### Post by gummibaerchen on 2007-01-19
> **maddog39 said:**
> Yeah, I love wxPython, its very easy and the code is normally clean and uncluttered compared to PyGTK. It also doesnt require many lines of code to make a fairly intuitive GUI.

But wxPython does never look really native on any platform.

For Gnome GTK is best, and Qt for KDE.

I think a toolkit (wrapper) for both would be cool.

---

### Post by maddog39 on 2007-01-19
I normally cant tell the difference from a wxWidgets app to a GTK app. For example if you've ever used RapidSVN, I thought it was made in GTK for the longest time until I read the about dialog and it said: Made with wxWidgets 2.6.3.

---

### Post by thenetduck on 2007-01-19
Thanks, Ill check out GTK. BTW I found a nice site if anyone is interested (mainly for new guys in programming) that really has helped me out. it's [www.showmedo.com](www.showmedo.com) It's videos etc. Showing now to program or use apps ect. Though you guys might be interested in sending new guys that way. 
 
The Net Duck

---

### Post by gummibaerchen on 2007-01-19
> **maddog39 said:**
> I normally cant tell the difference from a wxWidgets app to a GTK app. For example if you've ever used RapidSVN, I thought it was made in GTK for the longest time until I read the about dialog and it said: Made with wxWidgets 2.6.3.

But that definetly NOT count for SPE.

It is SO ugly under Gnome :(

---

### Post by ianare on 2007-01-19
> **gummibaerchen said:**
> But wxPython does never look really native on any platform.

For Gnome GTK is best, and Qt for KDE.

I think a toolkit (wrapper) for both would be cool.

wxPython uses system API's to draw its widgets, this means that an app WILL look like a native app on its platform. The only major exception is KDE, since there are bindings for GTK, but not for QT. In KDE it will use the GTK bindings, so it will look like a gnome app.

Take a look here for some screenshots of an app i made in wxPython under different OS
[http://file-folder-ren.sourceforge.net/index.php?page=Screenshots](http://file-folder-ren.sourceforge.net/index.php?page=Screenshots)

---

### Post by gummibaerchen on 2007-01-19
I had now a look at different wxWidget apps.

Xara Xtreme looks ok under Gnome, but SPE is (as already said) a real crapp.

And for the fact that wxW uses GTK under KDE, then I can directly use GTK :)

---

### Post by jblebrun on 2007-01-19
> **Wybiral said:**
> I do almost all of my programming in simple text editors... Disapproval of someones ability to say that a text editor isn't efficient enough for programming... Especially if you know the language, why do you need all the other junk (syntax highlighting/auto complete/etc...)?

And python... It's so easy, and you don't even have to compile anything, what could possibly make text editors so absurd to people?

Sure, you CAN code in a text editor like notepad, but why on earth would you wish that on anyone? Reading flat, un-highlighted code becomes tedious very quickly. Sorry, I don't see any case where someone would choose notepad over a text editor with at LEAST basic syntax highlighting capability. 

On top of that, there's no relationship between the ease of a language and whether or not it is compiled. They are completely orthogonal issues.

---

### Post by Wybiral on 2007-01-19
I'm not saying "EVERYBODY USE TEXT EDITORS"

I'm just saying... I do. And that it's not only possible, but I am more productive with them. Maybe I have some kind of disorder because IDE's are usually too bulky and distracting for me. But for someone to just say "you can use text editors, nobody does that" is wrong... I'm not the only person.

Now, I DON'T use notepad (I don't use windows at all), but I do use Gedit and I love it, my loading time plus the amount of code I can see in it makes me much more productive than when I use a bulky IDE. Plus, I use multiple languages and can't afford to switch back and forth between IDEs just for something like code completion and auto builds.

I am not saying that its for everyone, I am just defending the fact that a lot of people use them, and a lot of people prefer it. Thats all.

---

### Post by Mirrorball on 2007-01-19
But gedit does have syntax highlighting, line numbers, etc. It's not like Notepad. I think that the older versions of Notepad didn't even have search and replace.

---

### Post by jblebrun on 2007-01-19
> **Wybiral said:**
> I'm not saying "EVERYBODY USE TEXT EDITORS"

I'm just saying... I do. And that it's not only possible, but I am more productive with them. Maybe I have some kind of disorder because IDE's are usually too bulky and distracting for me. But for someone to just say "you can use text editors, nobody does that" is wrong... I'm not the only person.

Now, I DON'T use notepad (I don't use windows at all), but I do use Gedit and I love it, my loading time plus the amount of code I can see in it makes me much more productive than when I use a bulky IDE. Plus, I use multiple languages and can't afford to switch back and forth between IDEs just for something like code completion and auto builds.

I am not saying that its for everyone, I am just defending the fact that a lot of people use them, and a lot of people prefer it. Thats all.

Gedit != notepad. It has syntax highlighting, autotabbing, and better tab options. It is a big improvement over notepad, in general. I guess the problem is that I would not classify gedit as a "plain text editor" which is what the OP suggested to avoid. The poster was not insisting that people use IDEs. 

I use vim, myself. Vim is great because it's lightweight, and can do just about anything. It has integrated development features for just about any language!

---

### Post by geek_Man on 2007-01-19
I'm just starting out with Python and I like Pida a lot.

I would say go with GTK. I'm also starting with GTK2-Perl and it is nicer and easier than Tkinter. I know this like comparing apples to oranges, but if something is easier in Perl than in Python, you Python-Lovers... :wink:

---

### Post by Wybiral on 2007-01-19
> **jblebrun said:**
> Gedit != notepad. It has syntax highlighting, autotabbing, and better tab options. It is a big improvement over notepad, in general. I guess the problem is that I would not classify gedit as a "plain text editor" which is what the OP suggested to avoid. The poster was not insisting that people use IDEs. 

I use vim, myself. Vim is great because it's lightweight, and can do just about anything. It has integrated development features for just about any language!

I know, my initial post was directed towards pmaiser because we've been in the debate about simple editors vs IDEs... Like I said... I wasn't referring to notepad (or any windows app for that matter... ha ha ha...)

I was just referring to non-IDE editors in general.

---

### Post by po0f on 2007-01-19
There have been several threads I wanted to post this in, but I guess this is as good as any:

Can we please not argue over stupid stuff?  Sure, someone might not think GEdit is a "simple" text editor, and someone else does.  (Just as an example.)  There are more important things in life; I don't know about you, but the simplicity of a text editor doesn't rank very high.  ;)

Stay on topic, keep it civil, and have fun!  :D

---

### Post by phossal on 2007-01-20
> **po0f said:**
> There have been several threads I wanted to post this in, but I guess this is as good as any:

Can we please not argue over stupid stuff?  Sure, someone might not think GEdit is a "simple" text editor, and someone else does.  (Just as an example.)  There are more important things in life; I don't know about you, but the simplicity of a text editor doesn't rank very high.  ;)

Stay on topic, keep it civil, and have fun!  :D

Personally, there is nothing I enjoy more than giving someone a big shove toward the understanding that they're *medium*-smart in the midst of a few of us who are *ridiculously*-smart. If a good way to do that is by arguing over a programming language, IDE's,  or just simple name-calling, I'm in favor of it. 

Most of us who are constantly engaged in a battle of wits and words in these forums have managed to help a few people, and I think we all go away from each confrontation being a little more knowledgeable - if not about the topic, at least about what we're going to say to humiliate our adversary next time. 

So, if you're kind of a wuss, you should probably stick to giving advice (especially advice about *giving* advice) to noobs who aren't prepared to verbally bash your skull in when you make a mistake. I don't just speak for myself when I say many of us like the challenge.

---

### Post by phossal on 2007-01-20
:p That's the first post I've written in a few days that made me laugh out loud. lol I'm an idiot sometimes. Sorry.

---

### Post by po0f on 2007-01-20
phossal,

[quote=phossal]Personally, there is nothing I enjoy more than giving someone a big shove toward the understanding that they're medium-smart in the midst of a few of us who are ridiculously-smart. If a good way to do that is by arguing over a programming language, IDE's, or just simple name-calling, I'm in favor of it.[/quote]

Arguing does serve a purpose (I'm not denying that), it's just that I have seen too many a thread degenerate into a flame war.  I just tried to preempt this one.  Besides, I've seen some posts that have been made just for the sake of argument and/or postcount++ (not so much postcount++ in PT, but in other sections of the forum).

[quote=phossal]... at least about what we're going to say to humiliate our adversary next time.[/quote]

If ammunition for humiliating another user is the only thing you learn from a thread then something went wrong.  I'm not here to humiliate or belittle other users, I'm here to help them out.

Sure, sometimes I think some of the users can be obnoxious, rude, ignorant, entirely too newbish, outright stupid, whatever.  I try to ignore it and help out where I can.  At the end of the day I think to myself, "How many people have I helped today?" (not only with computer issues and these forums), not "How many people have I totally humiliated on a public forum that boasts thousands of users?"

[quote=phossal]So, if you're kind of a wuss, ...[/quote]

Did I give that impression?  From now on, I'll try to make my posts more "manly" for you.

[quote=phossal]... you should probably stick to giving advice (especially advice about giving advice) to noobs who aren't prepared to verbally bash your skull in when you make a mistake. I don't just speak for myself when I say many of us like the challenge.[/quote]

I like it when my mistakes are pointed out.  In the process of another's learning, I like it when I get a chance to learn as well.

I also like a challenge.  Arguing/flaming someone else isn't a challenge, all it takes is an Internet connection and a keyboard; really, anyone can do it.

In other words:  :p

[EDIT]

Sorry for the thread-crapping, on hind-sight I should have PMed that.

---

### Post by phossal on 2007-01-20
> **po0f said:**
> Sorry for the thread-crapping, on hind-sight I should have PMed that.

lol I suggest not.

---

### Post by thenetduck on 2007-01-20
This is accually kind of entertaining. ;)

---

### Post by pmasiar on 2007-01-20
> **po0f said:**
> Can we please not argue over stupid stuff?  Sure, someone might not think GEdit is a "simple" text editor, and someone else does.  (Just as an example.)  

I agree but to 50% only :twisted:

I am thinking about creating some master-sticky-candidate thread about Editors.

Some terminology, categories like plain text editors (notepad), wordprocessing editors (not for programming), simple programmer's editor like gedit, jedit, scite etc, advanced text editors like vi and emacs, lightweight IDEs, and heavy-duty IDEs. So at least we compare apples with oranges, and not apples with whales :-) 

Part of the problem description is - how big edit change I plan to do. To change one constant, even notepad is sufficient enough. :-)

Also, some languages almost require IDE: java without IDE is royal pain, python is just fine in anything above notepad (what can handle tab/spaces). 

Not sure if we can avoid flamewars, but we can at least try, WDYT?

Every tool was created as a solution to some problem - so unless it is worthless crap with no users, it *does* solve some problem, and if it does have users, solves is at least at the decent level of competency (for some values of "decent").

Somewhere I read about interview trick: manager asks about tools candidate used, what he liked and what not, and why. Then, describe tool candidate dislikes, hates, and why. After they are done, ask him about *good* features of the tool candidate just said he hates. If he cannot say anything good about it, even if asked, *big red flag*: candidate is religious about tools, probably too opinionated and narrow-minded to be asset for team. Just FYI. :-)

---

### Post by jblebrun on 2007-01-20
> **po0f said:**
> There have been several threads I wanted to post this in, but I guess this is as good as any:

Can we please not argue over stupid stuff?  Sure, someone might not think GEdit is a "simple" text editor, and someone else does.  (Just as an example.)  There are more important things in life; I don't know about you, but the simplicity of a text editor doesn't rank very high.  ;)

Stay on topic, keep it civil, and have fun!  :D

If we wanted to do the things that were more important in life, we probably wouldn't be spending so much time in forums. ;-)

But seriously... I dont' think anything in this thread was flame-war like. Just lots of people expressing their opinion. Our arguments were on-topic, and no one was being un-civil as far as I could tell... was your request pre-emptive?

---

### Post by jblebrun on 2007-01-20
> **pmasiar said:**
> I agree but to 50% only :twisted:

Also, some languages almost require IDE: java without IDE is royal pain, python is just fine in anything above notepad (what can handle tab/spaces). 


Ok, I guess I need to phrase my question very tenderly, since everyone is up-tight about flame wars. 

I am curious as to what characteristics of Java make it a royal pain without an IDE? I've done a fair amount of Java programming in gvim (whether or not to consider it an IDE is up for debate) but I didn't run into any trouble, and building at the command line is easy.... 

So I want to know what I'm missing out on!

---

### Post by jblebrun on 2007-01-20
> **po0f said:**
> phossal,

Sure, sometimes I think some of the users can be obnoxious, rude, ignorant, entirely too newbish, outright stupid, whatever.  I try to ignore it and help out where I can.  At the end of the day I think to myself, "How many people have I helped today?" (not only with computer issues and these forums), not "How many people have I totally humiliated on a public forum that boasts thousands of users?"


Ok, even though I found your post a little over-reactive (we weren't flaming each other (yet)), I think THIS point you make is a very good one! So I am saying that. And now it appears another time in the thread: if we approach this with the goal of helping people, results will be good!

I have a feeling that even the fussy people aren't setting out to humiliate as many people as possible. They're just inherently fussy. 

*grin*

---

### Post by pmasiar on 2007-01-20
> **jblebrun said:**
> Ok, I guess I need to phrase my question very tenderly, since everyone is up-tight about flame wars. 

No worry, i can take some flames. There is nothing like good opinionated discussion, if it stays civil and on-topic.

Speaking about on-topic: how about talking about python editors :-)

> I am curious as to what characteristics of Java make it a royal pain without an IDE? I've done a fair amount of Java programming in gvim 

After couple years of Perl and later Python I needed to switch to Java. I was already spoiled with expectations how easy things could be and how easy you can dive in and swim. Not with Java. So I compare Java with Perl/Python.

[LIST]
[*]**verbosity:** VeryLongUglyType someName = new VeryLongUglyType(); I see something typed twice :twisted: Why it cannot be just VeryLongUglyType someName = new(); I  just entered  the type?
[*]**Byzantine API**: depending on what team in Sun implemented it (and phase of the moon?), functionality is in static or object methods. How I am supposed to remember that?
[*]**object ravioli:** Instead of spaghetti code, we now have hundreds of small raviolis, stuffed with raviolis. Which one hides what you want? Example: ArrayList is *not* array, nor list of arrays.
[/LIST]

Everyone of my colleagues advised to use Eclipse - as a solution which was supposed me to help with all that mess. Eclipse is world by itself, but helps with noob Java editing a lot. Method autocompletion, syntax error highlighting + suggesting fix, it was better (for me) than jEdit I tried before.

Maybe you need less IDE help as you know java API by heart, advanced IDE is less needed.

OK I give up I confess: I am spoiled pythonista who became weak and spoiled :-) and cannot handle real badass strictly typed language as I was able before - my tolerance to syntax pain decreased substantially. You won. :-(

---

### Post by po0f on 2007-01-20
I apologize if anyone thought I overstepped my bounds as a regular forum user trying to "moderate".  I'm just getting tired of all the arguments.

I tried to be a totally objective forum user, I really did.  No chit-chat, get to the point, wham, bam, thank you ma'am.  I then found myself trying to inject a little personality into my posts just to liven things up.  Besides an answer, I started providing as many details and explanations about why something went wrong or why something wasn't working.  I wanted people to understand their problem, not just provide them with a fix.  There have been several occasions where I have hand-walked someone from the onset of a problem to a solution.  It made me feel good.  Pathetic as it may sound, I started caring about these forums.

Part of caring is making sure things don't go wrong, and when they do, trying to fix them.  I admit I probably have spent entirely too much time on these forums (don't we all?).  Ok, I'll step back.  Everyone needs a break.

If you guys really want to argue and flame each other, go ahead.  I'll be sure to don the asbestos suit, ignore it, and *still* try to help out where I can.  So there.

</end_of_apology_soapbox_rant_confessional_whatever>



pmasiar,

I don't know if we need to sticky a thread on IDEs, but one should definitely be created.  Along with the "I want to learn how to program" threads, "which IDE should I use?" is posted quite often.

To get slightly back on topic, *is* there a "simple" (simple as in Notepad) text editor for Ubuntu?  I'm sure there's one available for Linux, but I can't think of one in Ubuntu's repos.

And to get totally back on topic: I'm sure someone has posted the "the best Python editor is the one *you* like"; I agree.

---

### Post by jblebrun on 2007-01-21
> **pmasiar said:**
> No worry, i can take some flames. There is nothing like good opinionated discussion, if it stays civil and on-topic.

Speaking about on-topic: how about talking about python editors :-)



After couple years of Perl and later Python I needed to switch to Java. I was already spoiled with expectations how easy things could be and how easy you can dive in and swim. Not with Java. So I compare Java with Perl/Python.

[LIST]
[*]**verbosity:** VeryLongUglyType someName = new VeryLongUglyType(); I see something typed twice :twisted: Why it cannot be just VeryLongUglyType someName = new(); I  just entered  the type?
[*]**Byzantine API**: depending on what team in Sun implemented it (and phase of the moon?), functionality is in static or object methods. How I am supposed to remember that?
[*]**object ravioli:** Instead of spaghetti code, we now have hundreds of small raviolis, stuffed with raviolis. Which one hides what you want? Example: ArrayList is *not* array, nor list of arrays.
[/LIST]

Everyone of my colleagues advised to use Eclipse - as a solution which was supposed me to help with all that mess. Eclipse is world by itself, but helps with noob Java editing a lot. Method autocompletion, syntax error highlighting + suggesting fix, it was better (for me) than jEdit I tried before.

Maybe you need less IDE help as you know java API by heart, advanced IDE is less needed.

OK I give up I confess: I am spoiled pythonista who became weak and spoiled :-) and cannot handle real badass strictly typed language as I was able before - my tolerance to syntax pain decreased substantially. You won. :-(


Hmm, I wasn't trying to defend Java, it was an honest question! I agree with your points, mostly. I guess I've just gotten used to looking up stuff in the API docs, so I'm faster at doing that. I never got into Eclipse because I just found it took FOREVER to load. By the time Eclipse loaded, I had found the answer to my question and recompiled the code at the command line. Maybe it's improved since then.  ;-)

The verbosity is definitely annoying. Of course, I think it's an integral part of the language, like you could in theory want:

SomeClass var = new SomeSubClass();

Of course, compilers could be fixed to make "smart" choices when things were left out, but that syntactic sugar might make erroneous situations that don't throw compiler errors.

Are there really cases where the choice between static vs. instance method is unclear? If so, that sucks! In the cases that I've programmed, it's been clear, but I've only used a small subset of the standard libraries, but I would believe that such ambiguities exist. If you could show me an example so I could add it to my repertoire, that would be nice!

I definitely agree with the ravioli (Russian Doll) argument. I don't know what it is about Java that encourages people to make class hierarchies that are 50 levels deep. And all you end up with is something that could be likened to Siamese twins connected at the intestines....

I am a huge Python fan, myself.  Actually, I prefer coding in Ruby, but the performance sucks, so I stick with Python.

---

### Post by pmasiar on 2007-01-21
This discussion about Java is wide off-topic here. Luckily enough, someone created thread [ What's wrong with Java??]("http://ubuntuforums.org/showthread.php?t=343149") - lets continue there. I will repost my previous answer, discussion there will have context. You might want to repost your last post.

---

### Post by theGeoffMeister on 2007-01-24
Here's the thing about Vim: although it makes simple tasks more difficult, it makes difficult tasks way more simple.

For Example:

Inserting a Character:
Gedit -> 1 character press
Vim -> 3 character presses (if you include <esc>)

Moving a line of text to another place in the document:
Gedit -> Scroll to line, Select the line, copy, backspace, backspace, scroll to new line, paste
Vim -> Scroll to line, press "dd", scroll to new line, press "p" (no mouse use necessary!)

Rename all occourances of a word:
Gedit -> Copy the new word, Go through line... by... line..., select each occourance, paste.
Vim -> press ":%s/oldword/newword/g"

There's even a command to have Vim prompt you for each occourance.

Vim has a one-week learning curve for the average programmer, but once learned, I have never even thought about going back. Typing in Word seems so slow and useless.

I heard emacs is even nicer for the programmer too.

Scripting text editors are the way to go.


theGeoffMeister

---

### Post by mkppk on 2007-02-13
> **micahkoga said:**
> Just tried out Scribes. It's looks pretty good. Fast and Slim. I'm still trying to get used to not having tabs. I usually like having a bunch of files open at once, but they all open as separate windows. Other than that, I like it.

Ouch. That would be a real deal killer for me.

I program in Python all day for my job, We use DrPython, but.. we are also developing in windows (for linux), fewer good free choices. I like it alot. But it seems to run real slow for mein Ubuntu at home though =[ 

Don't know why. Not a horribly slow machine, but it is only a 500mhz Powerbook G3.

---

### Post by Engnome on 2007-02-13
I use SciTE, basically a very text editor with many features. Takes a litte time to set it up the way you wan't it but after that it's very nice.

> **theGeoffMeister said:**
> 
Moving a line of text to another place in the document:
Gedit -> Scroll to line, Select the line, copy, backspace, backspace, scroll to new line, paste
Vim -> Scroll to line, press "dd", scroll to new line, press "p" (no mouse use necessary!)

Rename all occourances of a word:
Gedit -> Copy the new word, Go through line... by... line..., select each occourance, paste.
Vim -> press ":%s/oldword/newword/g"

Umm no, moving a line is more like:
Gedit/SciTE/anyeditor -> Scroll to line, triple click to select line, backspace, scroll to new line, middle mouse button. Very easy.

Rename:
Gedit/SciTE/anyprogrammingeditor -> select word, click replace button, type in what to replace with, click replace all or replace next. 
You can often click find and it'll mark all occurrences of that word.

---

### Post by airjaw on 2008-09-10
It takes a bit of setting up but Eclipse w/ PyDev is pretty good.
I think investing your time in one editor is a good idea.  I have about a year of experience with Eclipse already so it makes sense for me to continue using something I am familiar with.

SPE seems to be recommended quite a bit.  DrPython seems to be pretty useful for beginning programmers.

I read in an article of different python editor reviews that Wing IDE is probably the best, although you do have to pay for it if you're a commercial developer.  I'd recommend trying each editor out for a bit and seeing which one you like best.  This includes downloading Wing IDE free trial and testing that too.

---

### Post by airjaw on 2008-09-10
> **po0f said:**
> 
To get slightly back on topic, *is* there a "simple" (simple as in Notepad) text editor for Ubuntu?  I'm sure there's one available for Linux, but I can't think of one in Ubuntu's repos.

And to get totally back on topic: I'm sure someone has posted the "the best Python editor is the one *you* like"; I agree.

I thought gedit was the ubuntu "notepad".  Granted I don't like it as much as notepad++ but it seems to do the job.

---

### Post by LaRoza on 2008-09-10
> **airjaw said:**
> I thought gedit was the ubuntu "notepad".  Granted I don't like it as much as notepad++ but it seems to do the job.

Gedit has more features, try the plugins and the plugins in the repos ;)

It has more than you probably think. (Thread necromance, but we've had plenty of those...)

---

### Post by fiddler616 on 2008-09-10
-1 IDLE (annoying indentation bugs)
+1 Geany
+2 gedit + highlighting + terminal

---

### Post by Endolith on 2008-09-12
> **pmasiar said:**
> to start with python IDLE if perfectly fine - and is included with install. So don't waste your time searching for IDE - dive into python!

IDLE confused me and didn't respond the way I expected, so I gave up and tried IPython.  I like IPython much better than the default python command line or what I experienced of IDLE.  I can use it over SSH from a Windows machine, too. :)

I edit with gedit and some plugins so far, but I'd like to try a more advanced IDE.  I'll look at SPE and DrPython.

---

### Post by manoj1987 on 2009-06-25
i use Jedit as it takes care of indentations .
[http://sourceforge.net/projects/jedit/](http://sourceforge.net/projects/jedit/)   

:o

---

