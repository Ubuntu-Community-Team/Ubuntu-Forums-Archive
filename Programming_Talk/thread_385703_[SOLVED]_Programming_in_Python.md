---
title: "[SOLVED] Programming in Python"
date: 2007-03-16
forum: Programming Talk
---

### Post by Cariboo1938 on 2007-03-16
Hi,
I want to learn programming in Python. I want to install the newest release Python 2.5.I also wand to use IDLE. 
In the repositories are so many python files that I don't know what I have to install.
Can somebody tell me which packages I need to install? And which are optional?
Thanks for any reply

---

### Post by peabody on 2007-03-16
python should be installed per default, just type "python" into the terminal program.

Is there a reason you'd need 2.5 specifically?

Idle should be located installable via:
sudo apt-get install idle

---

### Post by pmasiar on 2007-03-16
If you need just play around with Python syntax and try stuff, you can do it directly in Python shell. In shell, you can import modules, create objects, try object methods, all from shell command line, without need to write code to test your ideas.

Later, to edit your files with more comfort, you may want to upgrade to more advanced editors. SPE is one of popular editors, and it's author (stani) recently switched to Ubuntu and joined this forum, so Ubuntu is his main development platform now :-) SPE has some important advantages over IDLE, like intendation guides, and left panel with code outline (function names etc) for quick orientation in your longer modules.

When you need some simple tasks to train your new skills, I maintain wiki for Python beginners: [http://learnpydia.pbwiki.com/TasksBeginners](http://learnpydia.pbwiki.com/TasksBeginners) You can find there also links to online books about data structures and other usefull info.

Have fun!

---

### Post by Smerity on 2007-03-16
In general terms, as said before, you really won't need Python 2.5 for 99% of the things you'd be doing - especially if you're just testing the waters proverbially.

Other than IDLE and Python though, especially at the start, you'd need literally nothing else. One of Python's basic goals is to come with the kitchen sink included, so for most tasks it will all be there already, all you'll have to do is import them.

I'd also suggest having a look at [Dive into Python]("http://diveintopython.org/") as you go along your way ^_^

---

### Post by pmasiar on 2007-03-16
> **Smerity said:**
> In general terms, as said before, you really won't need Python 2.5 for 99% of the things you'd be doing - especially if you're just testing the waters proverbially.

Agree - and tutorials do not use 2.5 featurs anyway, so Python 2.4 is more than adequate

> Other than IDLE and Python though, especially at the start, you'd need literally nothing else. One of Python's basic goals is to come with the kitchen sink included, 

no, kitchen sink is *not* included - **"batteries included"** is how we call it. :-) Modules for most common functions, including building your own simple webserver in Python in 7 lines of Python code :-)

> I'd also suggest having a look at [Dive into Python]("http://diveintopython.org/") as you go along your way ^_^

Dive Into Python is good book if you have previous experience in programming in other languages, otherwise is way too steep. So if you are real beginner, take a look at   tutorials linkes from [http://learnpydia.pbwiki.com/HowToStart](http://learnpydia.pbwiki.com/HowToStart) : instant hacking is exactly what it says - intro to using Python from shell and IDLE, and two good online intro books for beginners with no previous programming experience.

---

### Post by Cariboo1938 on 2007-03-16
> **peabody said:**
> 
Is there a reason you'd need 2.5 specifically?

No, not really. 
For me this is entering a new world anyway, so I thought I could go with the latest version. 
I don't know about the advantages of Vers. 2.5 over 2.4 and it is probably irrelevant for beginners anyway, you are right. 
I only thought the newest version may be have some features which make live easier for beginners.

---

### Post by Cariboo1938 on 2007-03-16
Thank you, pmasiar and Smerity,
for the links....great help...I'm rather at the point where I "Dive in deep, cold, black ocean water without a life belt".):P 
Out of curiosity: 
How important/useful are the 2.5 features over 2.4?
Is Stan's Editor in the repositories? 
Can I use 'apt-get install ....' to get it?

---

### Post by Mirrorball on 2007-03-16
Python 2.5 is in the repositories. You can have both versions at the same time, the executable will be different (it will be python2.5 for Python 2.5 and python2.4 or just python for Python2.4). BTW, the features added in version 2.5 are not relevant for a beginner.

---

### Post by pmasiar on 2007-03-16
> **Cariboo1938 said:**
> I'm rather at the point where I "Dive in deep, cold, black ocean water without a life belt".):P 

then don't dive (via "Dive Into Python"): use slower approach from wikibooks. :-)


> Out of curiosity: 
(1) How important/useful are the 2.5 features over 2.4?
(2) Is Stan's Editor in the repositories? 
Can I use 'apt-get install ....' to get it?

(1): not very importnat. More important is which python is easier to install - and 2.4 is already installed in your Ubuntu Edgy, no worries.

(2) Yes. I use synaptic, and package is called spe.

---

### Post by Cariboo1938 on 2007-03-17
> **pmasiar said:**
> 
(2) Yes. I use synaptic, and package is called spe.

Quick question: Does SPE run on Ubuntu _**6.10-amd64**_ with kernel ..**_17.11_**?

> **Mirrorball said:**
>  BTW, the features added in version 2.5 are not relevant for a beginner.

Thanks Mirrorball, for the hint!

---

### Post by pmasiar on 2007-03-17
> **Cariboo1938 said:**
> Quick question: Does SPE run on Ubuntu 6.10-amd64 with kernel 17.11?!

Why you care? Whatever kernel and libraries are in 6.10, python runs on them, and comes with right libraries to run SPE. When will be time to upgrade, all dependent libraries will be upgraded as needed, and it will *just work*. Some smart people worked really hard to solve all those dependency problems so we don't have to. That's why I use Linux and not Windows. I install whatever version works with whatever libraries I have with couple clicks, and can go on with my life solving real problems.

And if it does not work and you fond bugs, report them and in most cases they are fixed in next release. 

BTW stani was looking for testers for new release of SPE - you may want to install it and check it out. Check threads for last week or so.

---

### Post by Cariboo1938 on 2007-03-17
> **pmasiar said:**
> ....and it will *just work*. Some smart people worked really hard to solve all those dependency problems so we don't have to. 
Yes, it *just works*. And many thanks to all the smart people who get this done!
> **pmasiar said:**
> 
BTW stani was looking for testers for new release of SPE - you may want to install it and check it out. Check threads for last week or so.
Wow...it blows me away. 
I started a Python totorial some time ago in WindowsXP using IDLE for writing/running the programs. 
And today, in Linux Ubuntu, with "givré's ntfs - 3g" I can access all the saved *.py files residing in my WindowsXP partition and open/read/write/execute them with SPE!
I'm in awe...and probably not qualified enough to really test SPE. I just have to much to learn about it.
Anyway...Fantastic...That's Ubuntu...:guitar:

---

