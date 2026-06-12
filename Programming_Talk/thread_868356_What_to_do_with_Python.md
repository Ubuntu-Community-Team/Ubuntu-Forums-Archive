---
title: "What to do with Python?"
date: 2008-07-23
forum: Programming Talk
---

### Post by tiachopvutru on 2008-07-23
I haven't know Python for very long, but I'm looking for something to do with it. Here's a list of what I have been considering
[LIST]
[*]Learn pygame and try to create a simple game with it.
[*]Learn a library for creating GUI and try to make GUI out of a program.
[*]Do something that requires mathematical skills to hone my math.
[*]Use it as a scripting language.
[/LIST]

I haven't gotten to any of those yet so I don't know how big of a hurdle they are. What I need is some directions on where to go from here and out of the above, which one is most realistic for a beginner (probably the last two).

As for what I have done with Python, I have only finished 10 Project Eulers. Not saying that it's enough, and I will continue to do more, but I want to move somewhere. :)

---

### Post by Kadrus on 2008-07-23
> Do something that requires mathematical skills to hone my math.
[ProjectEuler]("http://projecteuler.net/")

---

### Post by LaRoza on 2008-07-23
> **tiachopvutru said:**
> 

[*]Learn pygame and try to create a simple game with it.

Sure. Go for it.

> 
[*]Learn a library for creating GUI and try to make GUI out of a program.

Why not? See my wiki for GUI toolkits.

> 
[*]Do something that requires mathematical skills to hone my math.

That could work well also.

> [*]Use it as a scripting language.

Do you have a choice?

---

### Post by Wybiral on 2008-07-23
Why did you learn it? What type of programming do you want to do?

---

### Post by ghostdog74 on 2008-07-23
Read all the documents on the Python website.

---

### Post by Kadrus on 2008-07-23
I don't see the rush in doing anything GUI yet,but it's your choice.GUI doesnt mean much to me.And I agree with Wybiral,ask yourself those questions,and you'll find answers.

---

### Post by tiachopvutru on 2008-07-23
> **Kadrus said:**
> [ProjectEuler]("http://projecteuler.net/")

Actually, I have done about 10 of it before I created this thread. I'll continue to do more, though (although they are looking to get increasingly harder).

> **LaRoza said:**
> 
Do you have a choice?

Can you point me to resources on using Python for scripting? I know that scripting will come handy for me on everyday-computing, but I don't know how yet. 

> **Wybiral said:**
> Why did you learn it? What type of programming do you want to do?

When I was learn Python, I wanted to create some games. Along the way, I kind of have this wanting to create an open source project when I will be skilled enough, and that was when I thought about wanting to create GUI out of existing open source programs. Then just recently, I decided that doing something that are heavy on math (like image manipulation programs) would be cool, too.

Basically, anything works. While some of those are beyond my level, I just have to pick one.

> **ghostdog74 said:**
> Read all the documents on the Python website.

Sound like a lot of reading to do. :p

> **Kadrus said:**
> I don't see the rush in doing anything GUI yet,but it's your choice.GUI doesnt mean much to me.And I agree with Wybiral,ask yourself those questions,and you'll find answers.

When I said GUI programming, I meant creating GUI out of existing programs. I suppose the pro is that I will be exposed to and work on someone else's code.

---

### Post by LaRoza on 2008-07-23
> **tiachopvutru said:**
> 
Can you point me to resources on using Python for scripting? I know that scripting will come handy for me on everyday-computing, but I don't know how yet. 
I do not understand. It is a scripting language and anything you do with it would be scripting...

---

### Post by ghostdog74 on 2008-07-23
> **tiachopvutru said:**
> 
Sound like a lot of reading to do. :p


you did that in school too, remember?

---

### Post by days_of_ruin on 2008-07-23
> **tiachopvutru said:**
> I haven't know Python for very long, but I'm looking for something to do with it. Here's a list of what I have been considering
[LIST]
[*]Learn pygame and try to create a simple game with it.
[*]Learn a library for creating GUI and try to make GUI out of a program.
[*]Do something that requires mathematical skills to hone my math.
[*]Use it as a scripting language.
[/LIST]

I haven't gotten to any of those yet so I don't know how big of a hurdle they are. What I need is some directions on where to go from here and out of the above, which one is most realistic for a beginner (probably the last two).

As for what I have done with Python, I have only finished 10 Project Eulers. Not saying that it's enough, and I will continue to do more, but I want to move somewhere. :)

For pygame I would recommend you start here
[http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html]("http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html")

and for a gui I would recommend pygtk.

---

### Post by tiachopvutru on 2008-07-23
> **LaRoza said:**
> I do not understand. It is a scripting language and anything you do with it would be scripting...

Well... err, basically, I don't know a lot about scripting. For example, I haven't came across a way to change filename in Python yet.

> **ghostdog74 said:**
> you did that in school too, remember?

Yes, from which the memories mostly come off as nightmares. :p

> **days_of_ruin said:**
> For pygame I would recommend you start here
[http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html]("http://www.pygame.org/docs/tut/chimp/ChimpLineByLine.html")

and for a gui I would recommend pygtk.

Thank you very much.

---

### Post by arist0tle on 2008-07-23
Leave it aside.......use Perl :-)

---

### Post by ghostdog74 on 2008-07-23
> **tiachopvutru said:**
> Well... err, basically, I don't know a lot about scripting. For example, I haven't came across a way to change filename in Python yet.
that's why you have to read the documentations. If you do, you will come across [this page](http://docs.python.org/lib/os-file-dir.html).
All the functions that deals with OS is there. For renaming files, rename() is the one. Also, study the tutorial by Guido.

---

### Post by ghostdog74 on 2008-07-23
> **arist0tle said:**
> Leave it aside.......use Perl :-)

don't start it. OP states Python.

---

### Post by estyles on 2008-07-23
> **LaRoza said:**
> I do not understand. It is a scripting language and anything you do with it would be scripting...

My assumption when someone says to use as a "scripting language" is that of writing something akin to a batch file in DOS/Windows.  That is, writing a script to do something that you could do by hand, but faster.  And no, I don't mean like playing a game, or drawing.  Sure you can draw by hand, but that doesn't make the GIMP an "image scripter".  Something like backing up files on startup, or copying over certain configuration data and then starting a program.  Something that does essentially mundane operation and/or calls other more ponderous programs to do any heavy lifting that's needed.  

Frex., I wrote a VBScript at work to query all the machines in Active Directory and find their name, IP, processor speed, Windows Version, virus definitions date, version of MS Office (should be nil after I finish), and version of Open Office (should be 2.4 after I finish).  That's all stuff I could easily find out by hand by remoting into 200+ machines, but scripting it is easier.

Granted, Python may be considered a scripting language even when it's used to make GUI programs and games, but I wouldn't consider those games to be "mere scripting", unless they're something like "guess the number I'm thinking of".

---

### Post by tiachopvutru on 2008-07-23
> **ghostdog74 said:**
> that's why you have to read the documentations. If you do, you will come across [this page](http://docs.python.org/lib/os-file-dir.html).
All the functions that deals with OS is there. For renaming files, rename() is the one. Also, study the tutorial by Guido.

I'm more concern about the massive amount of functions and methods there are... I guess I will make note of them in the back of my head as oppose to completely memorize them, which is what I always do. The only way I will be able to remember them is when I use them a lot.

> **arist0tle said:**
> Leave it aside.......use Perl :-)

Since Perl is one of the language recommended to learn in [here]("http://www.catb.org/~esr/faqs/hacker-howto.html#skills1"), I will do that... two years from now. :)


@estyles: Thank you, that's what I meant. :)

---

### Post by Wybiral on 2008-07-23
> **arist0tle said:**
> Leave it aside.......use Perl :-)

How exactly would the OP benefit from this?

---

### Post by days_of_ruin on 2008-07-23
> **arist0tle said:**
> Leave it aside.......use Perl :-)
Perl is leaving the building no matter how many trollish posts you make.

---

### Post by Can+~ on 2008-07-23
> **arist0tle said:**
> Leave it aside.......use Perl :-)

I would suggest learning Perl too, but just to know how to read that mess.

---

### Post by LaRoza on 2008-07-23
> **tiachopvutru said:**
> Well... err, basically, I don't know a lot about scripting. For example, I haven't came across a way to change filename in Python yet.


The docs have everything you need, and google has the rest.

> **estyles said:**
> My assumption when someone says to use as a "scripting language" is that of writing something akin to a batch file in DOS/Windows.
That is a very narrow assumption, especially on a Linux forum. 

> 
That is, writing a script to do something that you could do by hand, but faster.
Like every single program in existance? They make super computers to do things they know how to do, but need to do faster.

>  
Something like backing up files on startup, or copying over certain configuration data and then starting a program.  Something that does essentially mundane operation and/or calls other more ponderous programs to do any heavy lifting that's needed.
Specific definitions to a vaque term?

> 
Frex., I wrote a VBScript at work to query all the machines in Active Directory and find their name, IP, processor speed, Windows Version, virus definitions date, version of MS Office (should be nil after I finish), and version of Open Office (should be 2.4 after I finish).  That's all stuff I could easily find out by hand by remoting into 200+ machines, but scripting it is easier.
Sounds like system administration. "Scripting" can also be used to do to other tasks.

> 
Granted, Python may be considered a scripting language even when it's used to make GUI programs and games, but I wouldn't consider those games to be "mere scripting", unless they're something like "guess the number I'm thinking of".

That is an interesting statement. "Scripting" has a negative sound to it, because of what we call "speed kiddies". I like to think of it as the computer doing work that it can afford to do, while I can't. 

Python is compiled to byte code, so it is no more a scripting language than Java. Of course, one can also use an interpreter to use C (I use tcc), does that make it a scripting language?

---

### Post by estyles on 2008-07-23
> **LaRoza said:**
> Python is compiled to byte code, so it is no more a scripting language than Java. Of course, one can also use an interpreter to use C (I use tcc), does that make it a scripting language?

Umm... I never said Python was a scripting language - you did.  Anyway, I was trying to interpret what the OP meant when he said "use it as a scripting language", sorry if I struck a nerve or something...

---

### Post by LaRoza on 2008-07-23
> **estyles said:**
> Umm... I never said Python was a scripting language - you did.  Anyway, I was trying to interpret what the OP meant when he said "use it as a scripting language", sorry if I struck a nerve or something...

Yes, I did.

I was just showing how not clear cut things are.

---

### Post by pmasiar on 2008-07-23
Seems like you are bored by Euler's problems but not ready to get into real project. And you are right, you have holes in your knowledge. Force yourself to read once through Guido's tutorial, especially quick overview of available modules. Modules is one of strengths of Python - it's part of "batteries included" motto. 

For more training tasks, try also PythonChallenge website, and also [http://learnpython.pbwiki.com/#Trainingtasks](http://learnpython.pbwiki.com/#Trainingtasks) from wiki in my sig.

---

### Post by slavik on 2008-07-24
if you want to learn how to make games, then make a tetris clone (or some kind of a maze thingy).

---

