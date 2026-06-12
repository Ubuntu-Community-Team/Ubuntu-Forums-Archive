---
title: "[SOLVED] Python troubles :("
date: 2008-02-21
forum: Programming Talk
---

### Post by hungryOrb on 2008-02-21
Ehm, Sorry about this, I did a search (even for one of my previous posts which answered one of my queries about a recommended editor) but couldnt find exactly what I was looking for.

Im trying to learn Python, and ideally, i've just set up ubuntu and would like to reserve it for developing. Ofc I need to learn how first, and following some tutorials have been offputting because they refer to functions that exist in windows python, like simply trying to 'open a new window' yields no success in python 2.5 in ubuntu :(

So, either wondering if there is a tutorial suited to built in ubuntu python for beginners, or if there is an editor around that will surely handly everything other tutorials have to offer?

Thanks :]

P.S. Not related but, I was browsing earlier, and suddenly Ubuntu went to the login screen, is there a key combo that shortcuts there? I dont really know any shortcuts.. or perhaps an error?

---

### Post by amingv on 2008-02-21
Python it's an excellent choice to begin programming. The best guide so far it's in the python webpage (made by python's creator himself), you can find it here:
[http://docs.python.org/tut/tut.html](http://docs.python.org/tut/tut.html)

Also read the sticky in the programming talk (you should post your programming questions there, too), you will find lots of information.

Out of curiosity, what is this function you use in windows? Most of python's modules/functions are cross-platform.

---

### Post by jachymc on 2008-02-21
what about [http://diveintopython.org](http://diveintopython.org)

---

### Post by housam on 2008-02-21
Take a look at [[COLOR="Red"]this site[/COLOR]]("http://www.awaretek.com/tutorials.html#begin")

---

### Post by hungryOrb on 2008-02-21
Thankyou for the answers :D 
The tutorials expect you to dive straight in which is FINE with me, BUT, opening Python 2.5 in Ubuntu brings up an editor which is not like other simple editors I've used. It confuses me.. I was wondering if there was a simple IDE that does EVERYTHING that I need it to do, including compile for a ubuntu environment. That way I can just open a tutorial and start typing straight away.. Please forgive my naivety and don't let it disgust you :) 
Having said this I'd probably need a cross platform one, I'm not sure why.. though I have dual boot, like most ppl so i expect that it would cover any issues i'd have regarding laziness and rebooting to another OS ;D

If you guys would help me with this, I would endeavour to share all I learn in a blog or tutorial which hopefully could help other nabs like me, although if any, im sure there arent many quite as nab as I :]]]

Thanksyou!!1

---

### Post by Martin Witte on 2008-02-21
take a look here for many Python development environments: [http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments). I stick with Idle, which is part of the Python distribution

---

### Post by hungryOrb on 2008-02-21
Awesome thanks :)
I'm a little unclear on IDE's.. Apart from editing and compiling, what else do they do?

---

### Post by CptPicard on 2008-02-21
If I were you, I wouldn't care about IDEs just yet... Python doesn't really need one, either. Just take any text editor you're comfortable with, type your code in that, save and run with the python interpreter -- as in, if you've got "myfile.py" containing your source, the command would then be "python myfile.py". I suppose you've been sitting in the Python shell which is not really a "coding environment" unless you're a total masochist :)

---

### Post by hungryOrb on 2008-02-21
TBH, I'm a little submissive, and would be happy with an editor that someone else tells me to use. But all I really need is an editor and compiler right?

p.s. I dont drink Ubuntu coz its not liquid and don't even like coffee, so don't believe the misleading thing beneath my name

---

### Post by CptPicard on 2008-02-21
> **hungryOrb said:**
> TBH, I'm a little submissive, and would be happy with an editor that someone else tells me to use. But all I really need is an editor and compiler right?


Yes. Source is text you produce whichever way you want, feed it into Python and Python does what it's told.

Now... :twisted: **spank* *use... **spank* *SciTE/Kate/Emacs **spank* *and ... **spank* *it's actually more like the Python *interpreter*, although it does compile into bytecode.

---

### Post by hungryOrb on 2008-02-21
Well.. I dont understand the compile process yet, so i'll stick with your first offer of Scite ;D Thanks for all help so far, was wondering if perhaps you could tell me why it is called scite? Is it simply a play on the word cite? Of which I guess it could share some minor relation..

WHAT is bytecode? Thanks for the spanks, really helps to focus my attention.

---

### Post by CptPicard on 2008-02-21
> **hungryOrb said:**
> Well.. I dont understand the compile process yet, so i'll stick with your first offer of Scite ;D

They're all just editors... 

> Thanks for all help so far, was wondering if perhaps you could tell me why it is called scite?

[Probably for the same reason Emacs is called Emacs and the Venom Incarnate editor is called "vi".]("http://www.dina.kvl.dk/~abraham/religion/")

> 
WHAT is bytecode? 


Generally in this context it means a binary form of your code that does not run directly on top of the CPU, but on top of the Python interpreter. It's more low-level and efficient than interpreting the source directly, but requires some compilation work. Python does this transparently to you, so you don't need to care :)

> Thanks for the spanks, really helps to focus my attention.

No problem. When I was your age, I got the default Emacs keybindings spanked into me and I turned out just fine...

---

### Post by hungryOrb on 2008-02-21
Laughing
I detect a bias to Emacs over that last reply,. which is shaking my newborn faith in your first offer. I guess I'll 'switch' to emacs then. 

Would you allow me to pester you some more Mr. Picards, if I (USING EMACS) try the baby tutorials for Python and end up eating a handful of sand?

btw. it looks like this guy is blessing an [xbox](http://www.stallman.org/saintignucius.jpg), isnt that a little blasphemous? (from link)

---

### Post by CptPicard on 2008-02-21
> **hungryOrb said:**
> Laughing
I detect a bias to Emacs over that last reply,. which is shaking my newborn faith in your first offer. I guess I'll 'switch' to emacs then. 

In all seriousness, don't start with Emacs... :) Also, as I'm not on Ubuntu (but on Kubuntu, the KDE version), I forgot to mention gEdit, pretty much the default editor on Gnome.

> 
btw. it looks like this guy is blessing an [xbox](http://www.stallman.org/saintignucius.jpg)

Wow.. you're probably right. He's not just some guy btw, he's Richard Stallman.. :)

---

### Post by hungryOrb on 2008-02-21
> **CptPicard said:**
> In all seriousness, don't start with Emacs... :) Also, as I'm not on Ubuntu (but on Kubuntu, the KDE version), I forgot to mention gEdit, pretty much the default editor on Gnome.



Wow.. you're probably right. He's not just some guy btw, he's Richard Stallman.. :)

Allright! going going gone to gEdit. I can open this up and start tapping aye? I'm trying to master lucid dreaming atm to defeat my insecurities, I hope you don't mind my incessant need for clarification.

---

### Post by CptPicard on 2008-02-21
> **hungryOrb said:**
> I can open this up and start tapping aye?

Yes... hacking is all about experimentation though, you won't get far if you need to make sure from some outside source first before you try yourself :)

---

### Post by hungryOrb on 2008-02-21
ARITE! Thanks, I'll get onto it this evening..!:guitar:

---

### Post by hungryOrb on 2008-02-21
Erm, how do you mark as solveD? :O

---

### Post by CptPicard on 2008-02-21
Under the horizontal bars at the top of the page there is the link "thread tools". Click on that and from there, "mark as solved".

---

### Post by hungryOrb on 2008-02-21
Thanks

---

### Post by Martin Witte on 2008-02-21
> **hungryOrb said:**
> TBH, I'm a little submissive, and would be happy with an editor that someone else tells me to use. But all I really need is an editor and compiler right?
We'll Idle is actually an editor which has a few extra options to run your script from within the editor in a window which runs the interpreter (by pressing the F5 key) Afaik most mentioned editors don't have an option to run the code, you have to go to the commandline and run your script; IDE's typically are capable of running your code from within

---

### Post by LaRoza on 2008-02-21
> **Martin Witte said:**
> We'll Idle is actually an editor which has a few extra options to run your script from within the editor in a window which runs the interpreter (by pressing the F5 key) Afaik most mentioned editors don't have an option to run the code, you have to go to the commandline and run your script; IDE's typically are capable of running your code from within

Gedit has a plugin for Python and the shell, so you can run programs from the editor.

---

### Post by pmasiar on 2008-02-21
Ridiculous. All these Python "experts" did not suggested the one IDE **designed** for beginners like OP: **IDLE.** Shame on you, guys. You repeatedly suggest **your** preferences (as experienced programmers), instead of suggesting what is good for a beginner.

And "dive into Python" being suggested **again** for a complete beginner. Author itself says that book is intended for programmers in other languages, who understand programming and just need to "dive" into Python. **It is not book for beginners**, yet is is suggested for beginners again and again. Frustrating.

---

### Post by LaRoza on 2008-02-21
> **pmasiar said:**
> Ridiculous. All these Python "experts" did not suggested the one IDE **designed** for beginners like OP: **IDLE.** Shame on you, guys. You repeatedly suggest **your** preferences (as experienced programmers), instead of suggesting what is good for a beginner.


A text editor with syntax highlighting is best for beginners in my opinion.

I will try IDLE now, to see what it is like...

<edit>
IDLE doesn't seem all that great... Gedit with the Python plugin seems better to me.
</edit>

---

### Post by pmasiar on 2008-02-21
> **LaRoza said:**
> 
IDLE doesn't seem all that great... Gedit with the Python plugin seems better to me.


IMHO (not like I want to argue with forum mod, of course :-) ):

OP wanted some simple editor integrated with Python. IDLE knows syntax, can run program and debug it, and as editor is very simple - less time skipping over un-needed functions.

Gedit needs Python plugin - yet another step. 

Of course if OP has any preferred editor, and it has Python mode, it will be fine too, but apparently it was not the case.

---

### Post by hungryOrb on 2008-02-21
thanks for the extra thoughts :) On my list is gEdit and IDLE, so I guess I'll just have a play with both and make a naive decision :D (probably based on colours)

woohOO!

---

### Post by LaRoza on 2008-02-21
> **pmasiar said:**
> IMHO (not like I want to argue with forum mod, of course :-) ):

OP wanted some simple editor integrated with Python. IDLE knows syntax, can run program and debug it, and as editor is very simple - less time skipping over un-needed functions.

Gedit needs Python plugin - yet another step. 

Of course if OP has any preferred editor, and it has Python mode, it will be fine too, but apparently it was not the case.

Actually, you are better off arguing with a mod because I (we) won't moderate the discussion, but defer it to another If it isn't tagged with red, it is just a regular post.

IDLE, in my brief use of it, has several problems. One, it using Tkinter (besides the looks of it) it may have trouble running with Compiz. I am using Metacity, so I don't know if it does.

The usability of it was questionable to me as well, as it didn't behave like most GUI editors.

I am not saying that it is bad, just that you won't see me recommending it much.

---

### Post by LaRoza on 2008-02-21
> **hungryOrb said:**
> thanks for the extra thoughts :) On my list is gEdit and IDLE, so I guess I'll just have a play with both and make a naive decision :D (probably based on colours)

woohOO!

For Gedit you should install the plugins.

If you do use Gedit, remember to set tabs to four spaces.

[http://img171.imageshack.us/img171/4083/screenshoteu9.png](http://img171.imageshack.us/img171/4083/screenshoteu9.png)

---

### Post by pmasiar on 2008-02-21
> **LaRoza said:**
> If it isn't tagged with red, it is just a regular post.

IDLE, in my brief use of it, has several problems. One, it using Tkinter (besides the looks of it) it may have trouble running with Compiz. I am using Metacity, so I don't know if it does.

The usability of it was questionable to me as well, as it didn't behave like most GUI editors.

I know you will not abuse your mod's superpowers, i said in in jest. Actually, I think we are very lucky we have mod like you in this forum who can relate to programming - in some past flamewars about a year ago, lack of deeper understanding by mods why some posts were inflaming for programmers resulted in skewed (IMHO) resolution, which hurt community. It is hopefully better now, and we will miss your constant presence when you will find the job. BTW how is job search? Did you found "What color is your parachute" book? Do you like it?

I agree with you that IDLE is pretty ugly. I was not aware (or forgot) about issues with compiz - I have no use for bling, I used it for all 30 seconds and disabled it. :-)

Might be interesting project to port IDLE to wxPython. I am not doing it tho :-)

But suggestion to start with "Dive into Python" was a bad one, and no-one called poster on that.

---

### Post by LaRoza on 2008-02-21
Job search is going well. I found a job (3, actually) that I will most likely get.

I ordered the book, for $0.01. 

I didn't follow the entire thread, and just jumped in for that post. I am frusterated by the DiP recommendations as well.

---

### Post by Martin Witte on 2008-02-21
> **pmasiar said:**
> Ridiculous. All these Python "experts" did not suggested the one IDE **designed** for beginners like OP: **IDLE.** Shame on you, guys. You repeatedly suggest **your** preferences (as experienced programmers), instead of suggesting what is good for a beginner.

And "dive into Python" being suggested **again** for a complete beginner. Author itself says that book is intended for programmers in other languages, who understand programming and just need to "dive" into Python. **It is not book for beginners**, yet is is suggested for beginners again and again. Frustrating.

please check item #6 in this thread

---

### Post by pmasiar on 2008-02-21
> **Martin Witte said:**
> please check item #6 in this thread

OK, you did suggested Idle (it is IDLE BTW: not to be confused with  [Eric Idle](http://en.wikipedia.org/wiki/Eric_Idle) :-) ) but I missed it. Sorry.

I still need to disagree with something you said :-) to keep discussion on this [Solved] thread alive, so I  just note that you should have trimmed what you quoted (deleting second para as irrelevant to what you said.). :-)

Yes, let's have "if you quote, trim" day today! :-)

---

