---
title: "Python 2.5/2.6 vs Python 3.1?"
date: 2010-06-06
forum: Programming Talk
---

### Post by McRat on 2010-06-06
Our family started to learn Python last night.  We found a textbook that was very "child friendly" and was oriented towards game development (to make it fun).

The textbook wants the students to do everything in 3.1 Python, but we have found that most computers are running 2.5/2.6.  A little research shows that 3.1 is not gaining acceptance very well.

I put Python 3.1 on all the machines, but I got to wondering whether Python 3.x will make learning harder if there is less "real world" support, code samples, and 3rd party libraries.  

For those with Python experience, what is your take on the 2.6 vs. 3.1 situation?

---

### Post by beastrace91 on 2010-06-06
The reason 3.1 is struggling to gain acceptance is because it broke **alot** of backwards compatibility from 2.x applications. Honestly, I prefer 2.6 but that is just because it is what I learned on.

Intentionally breaking backwards support is just a dumb idea.

~Jeff

---

### Post by McRat on 2010-06-06
> **beastrace91 said:**
> The reason 3.1 is struggling to gain acceptance is because it broke **alot** of backwards compatibility from 2.x applications. Honestly, I prefer 2.6 but that is just because it is what I learned on.

Intentionally breaking backwards support is just a dumb idea.

~Jeff

Thanks.  From my reading, it seems a lot of serious coders agree with the Dumb Idea comment.

I hate to say it, but not all "improvements" survive, even if they are a better idea, even if they work better.  There is no reason to fix things that aren't broken.

I don't know if Python 3.x is one of those things.


It might be like the "line numbers" in BASIC.

Using line numbers is not really a good way to program, but efforts to remove it completely were fought.  Most BASIC versions that don't need line numbers still permit them so you can run old code snippets.

---

### Post by del_diablo on 2010-06-06
Was not the entire point of 3.x to break compitablity with 2.x?
2.6 got some compitablity with 3.0 so the programmers got a shot at getting accustomed to the changes.

---

### Post by insane_alien on 2010-06-06
i'm a fan of python 3.1.

most of the programming i do is not dependant on any of the third party libraries and none of it is so dependant on them that i can't just port one or two functions into the body of the program.

i learned on python 2.5, i did think that python3 would be adopted by everyone more quickly  but, meh, what you going to do.

---

### Post by philinux on 2010-06-06
Moved to Programming Talk forum.

---

### Post by McRat on 2010-06-06
Well, it wasn't intended to be a technical discussion, just looking for opinions of if 3.1 will be around in 5 years.

But OK.

---

### Post by LeifAndersen on 2010-06-06
Well...it probably will be around in 5 years...but by then, there will likely be a new version of python out...or some other language that promotes the same feature set as python (simple, easy to pick up, etc. etc.).

I like python 3.  There are some changes, but a lot of it is still similar to python 2.x, and you probably won't notice too much of a difference for what it sounds like your doing with it.  (For example, I still read the python 2.x documentation, and only rarely do I run into a problem do to changes).

Also, if your looking for a real world example of a program using python 3.1, check out blender: [http://blender.org](http://blender.org), while the program itself is written in C, it has a python API, which uses python 3.  (Well, blender 2.5x does, 2.4x has the old API which uses python 2).

---

### Post by diesch on 2010-06-06
Python 3.x is certainly the future. But today a lot of important libraries are not yet compatible with 3.x so depending on what you want to do it may be a good idea to stay with 2.x for some more time.

But the differences aren't that big, so if you learn 3.x it shouldn't be much a problem to get used to 2.6 or later if you need that.

What do you want to do with Python?

---

### Post by McRat on 2010-06-06
> **diesch said:**
> Python 3.x is certainly the future. But today a lot of important libraries are not yet compatible with 3.x so depending on what you want to do it may be a good idea to stay with 2.x for some more time.

But the differences aren't that big, so if you learn 3.x it shouldn't be much a problem to get used to 2.6 or later if you need that.

What do you want to do with Python?

Teach my children programming.

I was going to use BASIC, but it's been dead for a long time now, only VB is in significant use, and it's platform dependent.

I don't want to teach them a syntax that will be gone is a few years.

It's very hard to tell by reading, what the differences are between 2.5 and 3.1.  They say alot about syntax, but very little about features.

To be honest, I haven't been able to figure out what 3.1 does that 2.6 won't, other than syntax differences.  A **WITH** statement?

---

### Post by twright on 2010-06-06
If you are teaching/learning a language why start with a legacy version? Most new programs will be using the newer version and you will only have to relearn it sometime anyway.

---

### Post by McRat on 2010-06-06
> **twright said:**
> If you are teaching/learning a language why start with a legacy version? Most new programs will be using the newer version and you will only have to relearn it sometime anyway.

I assumed I'd just use the 2.6 that was on Ubuntu and the Mac already, but then we opened up the textbook (which is very well written, and game oriented) and it is all done in 3.1.

The book states that you should do everything in 3.1 for the lessons.

Then I got to wondering if I should just ditch the book, or the 2.6?

Well, I decided to do the 3.1 since the book is excellent.  Hard to find good beginners textbooks that are fun to do.  If I can't make learning fun for kids, then it becomes a lot harder.

But I'm not absolutely sure 3.1 will be adopted, but learning programming methods is more important that the actual language used.

---

### Post by McRat on 2010-06-06
For informational purposes:

The book we are using is _Python Programming for the absolute beginner 3ed_ by Michael Dawson.

Chapter One is "Game Over" instead of "Hello World".

Last Chapter is "Astrocrash Game", which is full graphics and sound project.

All the chapters involve writing simple computer games to teach programming skills, and have "homework" at the end.

---

### Post by LeifAndersen on 2010-06-06
You know, the syntax isn't that big of a deal.  Most languages have syntax which is either easy to grasp, or based very heavily on other languages (although there are a few exceptions which will go unnamed here...).

The moral of the story is to just pick one and go, eventually you'll likely know all of the languages you were trying to decide, and every minute you spend trying to figure out which language you want to learn, is a minute you could spend getting better at programming.

---

### Post by McRat on 2010-06-06
> **LeifAndersen said:**
> You know, the syntax isn't that big of a deal.  Most languages have syntax which is either easy to grasp, or based very heavily on other languages (although there are a few exceptions which will go unnamed here...).

The moral of the story is to just pick one and go, eventually you'll likely know all of the languages you were trying to decide, and every minute you spend trying to figure out which language you want to learn, is a minute you could spend getting better at programming.

Yup.

Anyhow, whatever decision I make it will be wrong.  Murphy is my best friend ...:mad:

---

### Post by LeifAndersen on 2010-06-06
Oh, and to cite my point, my very first exposure to programming was LTP Basic ([http://www.amazon.com/Learn-Program-Basic-Windows-Macintosh/dp/B000N3W2L4](http://www.amazon.com/Learn-Program-Basic-Windows-Macintosh/dp/B000N3W2L4)), which isn't used by ANYONE anymore (save probably about 10 people in the entire world).  But it still was a very helpful tool.

Although, for the record, even though it was designed to make programming fun for kids, by doing graphical stuff, it started with Hello World. :P  (Although it was a hello world banner).

---

### Post by McRat on 2010-06-06
> **LeifAndersen said:**
> Oh, and to cite my point, my very first exposure to programming was LTP Basic ([http://www.amazon.com/Learn-Program-Basic-Windows-Macintosh/dp/B000N3W2L4](http://www.amazon.com/Learn-Program-Basic-Windows-Macintosh/dp/B000N3W2L4)), which isn't used by ANYONE anymore (save probably about 10 people in the entire world).  But it still was a very helpful tool.

Although, for the record, even though it was designed to make programming fun for kids, by doing graphical stuff, it started with Hello World. :P  (Although it was a hello world banner).

I remember doing Hello World in Pascal and Fortran.  It was about 11 lines of code.  :confused:

BASIC is a great learning language IMO.  I wrote code in at least a dozen versions of it, some of it was even very complex commercial software, like 3D transformations for IGES files, Plotter Drivers, Scalable Font Generation, etc.  Well, that was 20-30 years past.  I wrote some assembler, C, C++, CADL, and probably some I forgot, but I can still write BASIC on most anything that supports it.  I never did really master the other languages.

But times change.  I'm thinking Python is the new BASIC.  We wrote Hello World (in 2.6) last night on a Linux, OS X, and XP machine at the same time.

---

### Post by Vox754 on 2010-06-06
> **McRat said:**
> ...

Well, I decided to do the 3.1 since the book is excellent.  Hard to find good beginners textbooks that are fun to do.  If I can't make learning fun for kids, then it becomes a lot harder.

If it works for you that's fine. What worries me is that you say the book uses sound and graphics and stuff. Hopefully the libraries they are using for that part are already stable for Python 3.x, otherwise, oops!, you may find they actually changed one little thing and it doesn't run anymore.

> 
But I'm not absolutely sure 3.1 will be adopted, but learning programming methods is more important that the actual language used.
Python 3.x will be definitely adopted in the future. It is not a matter of *if*, but *when*. Everyone that has any experience with Python 2.x will tell you that. It is simply better.

Besides, the changes are not big. Yes, Python 3.x purposely breaks compatibility with Python 2.x, that's precisely why it is given a new major version number, but this is so things can be greatly improved.

The Zen of Python remains the same: the whitespace, the easy use of object oriented programming, the use of the standard libraries whenever possible, etc. Essentially, it is the same but improved in some technical aspects for programmers, besides a gazillion improvements under the hood in the C code implementation.

In Python, you hardly code everything yourself anyway, because there are so many libraries that do the job. You basically just connect or transform objects with calls from libraries.

Every person that uses Python 2.6 is essentially waiting for Python 3.x to become mature enough, and to support the third-party library they need, so they can make the switch.

With that said, some people are like "Don't learn the *obsolete* language Python 2.6, learn 3.0 instead."

They are totally wrong, Python 2.6 is not obsolete by any means. It will stay well supported for many years to come. Many mainstream open source programs will not be using it in 5 years, mainly because the open source world moves fast!, but it will be used in legacy code, or for in-house programs not meant to be released.

Right now, if you want to learn to program *proficiently* in Python, you really should start with the widely supported 2.6. Once you realize all the power, all the libraries at your disposal, all the things you can do, the switch to 3.0 will be painless.

However, since you already found a good book (apparently good for absolute beginners) that uses Python 3.1, go with that.

---

### Post by MCVenom on 2010-06-06
Go with 3.1... Eventually the 2.x series will be superceded completely by the 3.x series, and your kids will have learned an obsolete language so to speak, like you were hoping to avoid with BASIC. There are syntax differences at the most basic command of 'print("Hello World!")', so learning 3.x after 2.x will be like learning another language (albeit a very similar one).

If it makes you feel a little more secure in the decision, most books are going with Python 3 now, libraries and tools are being ported to Python 3, the transition may be a bit slow, but it's going to happen. And the syntax changes were mostly out of a need for greater clarity; I don't think we'll see another *major* syntactic change in the next five years.

---

### Post by BoneKracker on 2010-06-06
3.1 is the new Python.  If you are writing new programs, do it in 3.1.  If you are learning Python, learn 3.1.

I imagine that all the distros are in the process of migrating to 3.1.  I don't know what Ubuntu's strategy is for that.

The distro I use (which has a "rolling" release model) currently has both 3.1 and 2.6 installed, with 2.6 being the default when an application just calls python (3.1 is run if called explicitly).  After a while, when developers have had a chance to remediate their products, that will be reversed.  Then ultimately, 2.6 will be removed.

Ubuntu, which has periodic releases, might be using more of a "big bang" approach, where everything is on 2.x for one Ubuntu release, and then everything is migrated en masse to 3.1 for the next release.  Maybe someone can advise you about this.

At any rate, for your purposes backward compatibility is not an issue.

---

### Post by MCVenom on 2010-06-06
> **McRat said:**
> For informational purposes:

The book we are using is _Python Programming for the absolute beginner 3ed_ by Michael Dawson.

Chapter One is "Game Over" instead of "Hello World".

Last Chapter is "Astrocrash Game", which is full graphics and sound project.

All the chapters involve writing simple computer games to teach programming skills, and have "homework" at the end.
:D ^this^ :D

It's what I'm using to learn anyway. The only thing is, it's Windows-centric and doesn't teach you about the shebang; if you want to run your applications outside the Python shell, you'll want to make sure you add this line to the top of your script:

```
#!/usr/bin/env python3
```

---

### Post by Vox754 on 2010-06-06
> **BlackOtaku said:**
> Go with 3.1... Eventually the 2.x series will be superceded completely by the 3.x series, and your kids will have learned an obsolete language so to speak, ...

Lol! This is the dude I'm talking about.

He is new in this forum. Search his posts: *Python 2.6 is obsolete!*

No. It is not.

---

### Post by MCVenom on 2010-06-06
You might also want to look into PyJunior on Ubuntu (you'll need to be running Lucid though), it's a kid friendly environment for learning Python.

You can read about it here: [Jono Bacon: Making Programming Easier for Kids With PyJunior]("http://www.jonobacon.org/2010/04/08/making-programming-easier-for-kids-with-pyjunior/")
And get it here: [https://launchpad.net/pyjunior](https://launchpad.net/pyjunior)

---

### Post by MCVenom on 2010-06-06
> **Vox754 said:**
> Lol! This is the dude I'm talking about.

He is new in this forum. Search his posts: *Python 2.6 is obsolete!*

No. It is not.
I am not, nor have I ever said that, and I've searched my posts.

I'm not saying it's obsolete. I'm saying that for all intents and purposes it will be as the world finally moves to Python 3. Don't put words in my mouth.

---

### Post by Bachstelze on 2010-06-06
You guys are funny, talking like it's a really important issue, almost a matter of life and death. :p

It's not, really. The vast majority of the language is the same with both versions, so as long as you take care of, for example, using [font=monospace]print(x)[/font] instead of [font=monospace]print x[/font], your programs will work just as well in both versions. And if a book says [font=monospace]print x[/font], write [font=monospace]print(x)[/font] anyway. The book will not get mad at you.

So my take on this is: use 3.x, beause it's the newest, if you have no reason to use 2.x. But if you do (e.g. because you need a 2.x-only library), then use 2.x. It's that simple. When the time comes when your library will be ported to 3.x, your program will only need minor adjustments (if at all).

---

### Post by McRat on 2010-06-06
> **Bachstelze said:**
> You guys are funny, talking like it's a really important issue, almost a matter of life and death. :p

It's not, really. The vast majority of the language is the same with both versions, so as long as you take care of, for example, using [font=monospace]print(x)[/font] instead of [font=monospace]print x[/font], your programs will work just as well in both versions. And if a book says [font=monospace]print x[/font], write [font=monospace]print(x)[/font] anyway. The book will not get mad at you.

So my take on this is: use 3.x, beause it's the newest, if you have no reason to use 2.x. But if you do (e.g. because you need a 2.x-only library), then use 2.x. It's that simple. When the time comes when your library will be ported to 3.x, your program will only need minor adjustments.

It's certainly not life-or-death.:P

It is the reason web forums exist.  You exchange questions, experience, and opinions with others.

With the automotive boards, this is a "Should I run synthetic oil?" thread.  ;)

---

### Post by BoneKracker on 2010-06-06
> **McRat said:**
> With the automotive boards, this is a "Should I run synthetic oil?" thread.  ;)
Excellent metaphor.

Except, I heard that if you don't have all your stuff ported to 3.1 by 2012, the code will collapse under the gravitational pull of the Galactic Alignment.

[IMG]http://omploader.org/vNGl4eQ[/IMG]

---

### Post by McRat on 2010-06-06
> **BoneKracker said:**
> Excellent metaphor.

Except, I heard that if you don't have all your stuff ported to 3.1 by 2012, the code will collapse under the gravitational pull of the Galactic Alignment.

[IMG]http://www.2012eyeoftheshaman.com/wp-content/uploads/2007/03/2012__alignment2.jpg[/IMG]

There are a bunch of dead Mayan's looking down and laughing at us ...:)

---

### Post by diesch on 2010-06-06
> **McRat said:**
> Teach my children programming.

Then I'd go with 3.x



> **McRat said:**
> 
It's very hard to tell by reading, what the differences are between 2.5 and 3.1.  They say alot about syntax, but very little about features.

To be honest, I haven't been able to figure out what 3.1 does that 2.6 won't, other than syntax differences.  A **WITH** statement?

The main goal of the changes in 2.x -> 3.x was to finally remove some deprecated features and features that duplicate functionality and make the language a bit more polished. 

Most 3.x featrures that don't break backwards compatibility are backported to 2.6 so there is much that 3.1 does that 2.6 won't.

---

### Post by McRat on 2010-06-06
Thanks all!

Uh...

One question though.  On the Windows machines, and the Mac, we can execute a **program.py** directly by double clicking it.

With Ubuntu and Python 3.1 it just opens it up in Gedit.

What's the fix for association?

---

### Post by BoneKracker on 2010-06-06
> **McRat said:**
> Thanks all!

Uh...

One question though.  On the Windows machines, and the Mac, we can execute a **program.py** directly by double clicking it.

With Ubuntu and Python 3.1 it just opens it up in Gedit.

What's the fix for association?

Long time since I used Nautilus, but somewhere buried in there is a "what to do when I double-click on this type of file" dialog, offering you the choice of "edit" vs. "run".  Try right-clicking on it and/or selecting the file and seeing what's offered in the menus and dialogs.  Hopefully you'll get a more intelligent response than that.

---

### Post by MCVenom on 2010-06-06
> **McRat said:**
> Thanks all!

Uh...

One question though.  On the Windows machines, and the Mac, we can execute a **program.py** directly by double clicking it.

With Ubuntu and Python 3.1 it just opens it up in Gedit.

What's the fix for association?
First, make sure you have a shebang as the first line of your script. That would be:

```
#!/usr/bin/env python3
```**Then, you have to give it executable permissions**. This is important, because your scripts won't be executable by default in Linux. The easiest way to do this would be right-click the file, properties, Permissions tab, and check the checkbox that says 'Allow Executing file as a program'. 

After that, you should double-click it and it'll ask how you want to open it; choose 'Run In Terminal'.

Done! :D

---

### Post by slavik on 2010-06-06
The reason to break compatibility is that 2.5/2.6 do some things in certain ways that are useless/bad and not worth implementing, but putting something else in will break compatibility.

When people started working on Perl6, some features were dropped because they were too difficult to implement and not worth the trouble to implement.

As for syntax, 95% of languages (prolog, lisp, haskel being the major exceptions) by use follow algol60 syntax.

---

### Post by McRat on 2010-06-06
> **BlackOtaku said:**
> First, make sure you have a shebang as the first line of your script. That would be:

```
#!/usr/bin/env python3
```**Then, you have to give it executable permissions**. This is important, because your scripts won't be executable by default in Linux. The easiest way to do this would be right-click the file, properties, Permissions tab, and check the checkbox that says 'Allow Executing file as a program'. 

After that, you should double-click it and it'll ask how you want to open it; choose 'Run In Terminal'.

Done! :D

Yup!!  Thnks kindly.

The kids were smirking at me, because they could do the example and mine didn't work...  :P

---

### Post by BoneKracker on 2010-06-07
Does Ubuntu's Python include Idle?

That's a little IDE for Python.  Fire that up and then taunt your children.

---

### Post by MCVenom on 2010-06-07
> **BoneKracker said:**
> Does Ubuntu's Python include Idle?

That's a little IDE for Python.  Fire that up and then taunt your children.
Yeah, it's in the Software Center. :)

---

### Post by BoneKracker on 2010-06-07
Idle is a nice (if ugly) tool for learning on.

---

