---
title: "[SOLVED] learning python, need some advice"
date: 2008-11-14
forum: Programming Talk
---

### Post by jimmy the saint on 2008-11-14
It was recommended to me that if I am going to learn python, I may as well learn python 3 rather than learn 2 and immediately relearn 3.  Makes sense to me.  Unfortunately, I have run into a problem.  Gedit's python console does not seem to work with python3, only with 2.  I cannot install IDLE3 because the repos do not have a dependency (why they would inculde a package, but not its dependencies in the repos is beyond me).

Gedit is ok, but its tab system is a little wonky.  I could live with it if I could get the console to work with python3 though.  I am completely new to this, so I may be missing something.  Is there a better editor to work with python3 or am I just expecting too much?

Thanks All,

JTS

PS, any general advice for a total newbie is welcomed and appreciated!

---

### Post by quimico69 on 2008-11-14
Hmmm... AFAIK the stable python release is version 2.6, and 3.0 is still in beta.  That may explain why gedit does not handle it well.  Maybe when it is the stable release gedit will get up to speed.

You could try emacs, in my experience it has nice syntax highlighting for several programming languages, python included.

---

### Post by pmasiar on 2008-11-14
Learning Python 3 does **NOT** make sense for following reasons:
- all books and tutorials are for Py2
- most people still use Py2, and will for couple years (untill all libraries and frameworks will get upgraded - may take couple years, depending)
- Difference is mostly trivial. Main one is that print is not statement but function. Well, big deal! 

So don't worry and learn 2.5 or 2.6, whatever is installed in your system.

See wiki in my sig for selected best tutorials and training tasks.

---

### Post by jimmy the saint on 2008-11-14
yeah, I was thinking of delving into emacs or vi, but one step at a time.  I work and am a full time student.  For some reason I figured I needed to take on another little project.  Both vi and emacs seem more like a summer project to learn though!  I guess thats what it takes to do it right though!

---

### Post by Greyed on 2008-11-14
> **pmasiar said:**
> - Difference is mostly trivial. Main one is that print is not statement but function. Well, big deal! 

And for those of us who have been using print("spam") the entire time anyway the difference is even more trivial than that.  ;)

> **jimmy the saint said:**
> Gedit's python console does not seem to work with python3, only with 2.

What does the console provide you that would not be available from running a separate instance of Python in another window?

> PS, any general advice for a total newbie is welcomed and appreciated!Aside from the above?  

Don't try to over-think the language and preoptimize.  Just concentrate on learning the straight-forward way of doing things.  More often than not there are good reasons for doing things that way and until you learn those reasons you cannot know when to break them.

(edit)  Just saw your message about vi/emacs.  Give vim a whirl.  I started using vim about 10 years ago.  Up until then I programmed mostly in joe which uses Wordstar bindings.  To get comfortable in vim took about a week.  I just ran the tutorial and slapped the ESC key a lot.  It certainly wasn't a summer-long project.  On the other hand 10 years on I'm still learning ways to do things in vim.  ;)

---

### Post by jimmy the saint on 2008-11-14
wow, I didn't think I'd get many responses so soon!  So basically I jumped the gun by skipping python2?  I guess I'll get another book!   I am just trying to get my feet wet with programing.  Is python a good place to start or is there something better?  I don't have time for formal classes.  I am good with computers (the rallying cry of those who arent!) and I build and tinker with them in my spare time.  I am totally new to programing though.  Will learning python be a good starting point in general or is it too different from everything else?

---

### Post by Gilabuugs on 2008-11-14
> **jimmy the saint said:**
> yeah, I was thinking of delving into emacs or vi, but one step at a time.  I work and am a full time student.  For some reason I figured I needed to take on another little project.  Both vi and emacs seem more like a summer project to learn though!  I guess thats what it takes to do it right though!

vi is actually probably a week of working in it to learn to a point you can use it well, emacs can take a very long time and probably won't be of very much use to you

if you do learn vi go through a basic tutorial, i think there is something called vitutor or something to help you along

then use it and just look up commands if you forget them

as for python do like pmasiar said and learn 2.5 or 2.6, a byte of python was a nice introduction for me, as well as the official docs

---

### Post by jimmy the saint on 2008-11-14
haha, its funny you said that because I am using A Byte of Python!!  That's what told me to skip past python 2 and learn python 3!!  Well I'll take the advice of real live programmers!  2 it is!

---

### Post by Luggy on 2008-11-14
Here is a slashdot article that I read a while back that talked about Pythong 2.5, 2.6 and 3. [Python 2.6 to Smooth the Way for 3.0]("http://it.slashdot.org/article.pl?sid=08/10/03/2127223")

From that article and other peoples comments I would gather that learning Python 2.6 is the safe bet.

---

### Post by Greyed on 2008-11-14
> **jimmy the saint said:**
> I am totally new to programing though.  Will learning python be a good starting point in general or is it too different from everything else?

I can think of none better.  However, I am biased.  Take a look at my "computing paths" below and notice where the programming one currently sits.  ;)

---

### Post by jimmy the saint on 2008-11-15
One last question.
It seems that python 2.6 will begin to bridge the gap to 3.  Ubunty has 2.5 as default, but I also have 3.0rc1 installed alongside it with no ill effects.  Is there a way to install 2.6 on Ubuntu?  it isn't in the repositories and I did a Google search and found nothing useful which tells me it either isn't possible or is so super easy noone has asked for help.
Thanks

---

### Post by pmasiar on 2008-11-15
Again: relax. Learn the version you have installed, differences are minimal. If you don't know what are you doing (ie are sysadmin expert), you don't want to switch Python versions, because quite a lot of system tools are coded in Python: switching versions might cause bugs (in system tools) which you will have hard time to cope with and recover from.

Differences between 2.5 and 2.6 is minimal (see [What is new in Python 2.6](http://docs.python.org/whatsnew/2.6.html), as I said most features in 2.6 is to make upgrade to 3.0 as painless as possible (ie you can "import from __future__" some future features of Py3K)

---

### Post by Greyed on 2008-11-15
Let me just expand on what pmasiar is saying.  Back in.... 2000?...  I was sent by my employer O'Reilly's OSCON.  At the time I was a professional Perl hacker who was looking for something a tad less icky.  I had heard of Python but had not really delved into it.  At that conference I attended some talks on Perl and other topics relevant to my job.  But I did drop in on an introduction to Python put on by David Beazley, author of _Python Essential Reference_.  In that 4 hour talk I not only understood Python but fell in love with it as it was a lot of what I was looking for in a language not-Perl.  I have been using Python ever since.

8 years ago I started with v1.5.2 of Python.

My most recent projects larger than 1-2 functions have been in Python 2.5.

I still, to this day, refer to parts of my copy of _Python Essential Reference_ from the 1.5.2 era.

Yes, in that time a lot has changed, but the principles of the language have not.  And yes, Python 3 is going to break compatibility to address some of the hangnails of the language that have cropped up since its birth.  But if you learn Python 2.4, 2.5, 2.6 now most of that knowledge will translate over when you need to touch Python 3.  Sure, you'll have to get into the habit of print("spam") instead of print "spam" and other such quirks.  However the amount of stuff you'll have to adjust in your mind will be minute compared to the amount of knowledge and experience you have gained by not waiting.

So if you're interested in Python don't worry about the version in the repos right now or how it'll map over to Python 3 when it is finalized and let loose upon the world.  Just dive in and get those base principles solid in your head and leave the worrying about tweaking the finer points of syntax until you need to worry about them.  ;)

---

### Post by jimmy the saint on 2008-11-16
Wow, I gotta say you guys really exemplify the principles of what make this forum great.  Thanks for the tips and advice.  I just downloaded the 2.xx version of "byte of python" and will get to work with it.  I am sure that I will have questions that would be laughed at elsewhere (and by me when I realize how bone-headed they were) but at least I know where I can ask them.  It is hard jumping into something big like programming when you don't have enough knowledge to put the information you can find into perspective.  Communities like this make it easy to get that perspective and shorten the learning curve.

Thanks,

JTS

---

