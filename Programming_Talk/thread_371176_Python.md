---
title: "Python"
date: 2007-02-26
forum: Programming Talk
---

### Post by Baelfael on 2007-02-26
Alright, so I've never programmed before in my life, except for making a HelloWorld program in Java. How good is Python?

Let me explain. My hero, for a long time, has been Andrew Gower. He's an extraordinary person. I wrote this article about him: ([http://en.wikipedia.org/wiki/Andrew_Gower](http://en.wikipedia.org/wiki/Andrew_Gower)) if you want to find out about him.

Basically he learned a lot of programming languages, and made a lot of useful programs and games. I want to be like him, I want to have a job someday programming games and doing something I want to do. I always knew that programming would be my thing. I've been interested in computers ever since I was an infant, to be truthful. However, I don't think I'm as smart as Andrew is. He's been programming since the age of 7. But I still want to learn how to program.

My dream, one day, is to follow his footsteps and code an RPG game or an MMORPG. He was well on his way programming an MMORPG called DeviousMUD; all by himself. I think anything is possible if you put your mind to it.

Now to the main point of this thread... I want to program games someday. Now since I'm using Ubuntu, I know that Python is a strong programming language for it, and it's recommended. I also want to follow in Andrew's footsteps and use Java though. To be simple; which programming language, in the end, would be able to create a 2D (possibly 3D and 2D) OR isometric (which is what I'm aiming for first) multi-user role playing game?

---

### Post by Wybiral on 2007-02-26
Take your pick! 2d isometric can be done in almost any language with a good graphical library.

I suggest python. It's got some great 2d and 3d libraries (OpenGL and PyGame)

If you want to get into 3d, I suggest C or C++ with OpenGL (and probably SDL for other stuff like initializing and getting user input)

But... C, C++, Java, Python... Would all work just fine for making a 2d game.

---

### Post by Mirrorball on 2007-02-26
Programming is fun and you'll love it. You don't need to be a genius to write simple programs and games. Both Python and Java are good for games, but I think Python is a simpler and easier language. In a few years you will know more than one programming language anyway, so don't worry about your first language, whatever you learn will be useful.

---

### Post by Baelfael on 2007-02-26
Thanks for the replies! :)

I think I may go for Python now, and then try out Java.

Also here's a screenshot of Andrew's DeviousMUD, which my game will be heavily inspired by...

---

### Post by Baelfael on 2007-02-26
Oh, and when that day comes when I'm ready to take on the project of making an MMORPG, I know what I'm up against. I know it's a hard thing to undertake, but I'm used to having the odds against me. I have a friend who is also interested in helping me out someday too.

My plan for that day is to write an engine for the game to run on, which I know will take ages. After the engine is complete or ready (as I may have to tweak it once I start the actual game), I will start programming the game. This will probably apply to all my early games. I want to start out learning by making simple games and some applications, and then keep on moving with making them until I'm ready.

---

### Post by pedrotuga on 2007-02-26
Sorry for being again the anti-python-hype guy.

I myself am programming python at the momment and it's ok, i just ask myself everyday why da heck all the "python, ruby = heaven, C,PHP = hell" out there. In fact learning PHP was a lot quicker and more productive than python.
This was just to  say that whatever choice you will make you will listen wonder about the new OOP languages while the C family languages will be considered a very bad thing. In the end things are not quite like that.

Not to get so off-topic:
For game programming you should go for C/C++.
You will need power and heavy-weight libraries that work
Game programming is a lot of hard working rather than finding simple and efficient solutions to a specific problem. I myself am not into it at all.

I would suggest starting with simple games with old-school ascii graphics, then when you are familiar with programming you could start using graphics libraries.

---

### Post by Wybiral on 2007-02-26
> **pedrotuga said:**
> Sorry for being again the anti-python-hype guy.

I myself am programming python at the momment and it's ok, i just ask myself everyday why da heck all the "python, ruby = heaven, C,PHP = hell" out there. In fact learning PHP was a lot quicker and more productive than python.
This was just to  say that whatever choice you will make you will listen wonder about the new OOP languages while the C family languages will be considered a very bad thing. In the end things are not quite like that.

Not to get so off-topic:
For game programming you should go for C/C++.
You will need power and heavy-weight libraries that work
Game programming is a lot of hard working rather than finding simple and efficient solutions to a specific problem. I myself am not into it at all.

I would suggest starting with simple games with old-school ascii graphics, then when you are familiar with programming you could start using graphics libraries.

A agree that if you plan to get serious with games that C/C++ is definitely the way to got (especially for 3d). But python is nice to beginners and will provide you with a pretty good idea of programming if you ever decide to check out C++ (C is much further from python though)

But, for 2d games, python will do just fine. You can also look into writing modules for python in C/C++ to work out any slow spots you run into if it's ever a problem.

I think learning all of the above is a good idea, I just think python is a good place to start.

---

### Post by pmasiar on 2007-02-27
> **pedrotuga said:**
> Sorry for being again the anti-python-hype guy.

I myself am programming python at the momment and it's ok, i just ask myself everyday why da heck all the "python, ruby = heaven, C,PHP = hell" out there. In fact learning PHP was a lot quicker and more productive than python.
This was just to  say that whatever choice you will make you will listen wonder about the new OOP languages while the C family languages will be considered a very bad thing. In the end things are not quite like that.

PHP might be better for simple websites - in python, you need extra templating and CGI which is included in PHP. But unlike PHP, Python is universal language - so you can use it also for non-web projects, and Python is also object oriented, which leads to *much* cleaner structure of bigger projects.

I have no problem if experienced programmer decides to invest extra time to C/C++ program to gain extra speed, but for a beginner? I strongly disagree. Dynamicaly typed language with automatic memory management will be 10-20 times more productive to learn programming and create basic simple games than unforgiving languages like C/C++/C#/Java.

> 
For game programming you should go for C/C++.
You will need power and heavy-weight libraries that work
Game programming is a lot of hard working rather than finding simple and efficient solutions to a specific problem. I myself am not into it at all.

For your first games, I would suggest [Game maker]("http://en.wikipedia.org/wiki/Game_maker") - specializing to write games, and make writing games easy and fun. But it runs on Windows only. On Linux, you can use Python with pygames library - it will handle much of hard problems for you.

"games require C/C++" is a common misunderstanding repeated by people who heard it themselves and repeat it without understanding why, to pretend they have experience. It is not true. Of course it is nice to have extra performance which C/C++ gives you, but in most cases current processors are fast enough. Some popular games written in Python are [galcon]("http://renesd.blogspot.com/2006/12/galcon-released.html") and [Eve online]("http://en.wikipedia.org/wiki/EVE_Online") [link mentioning Python]("http://www.eve-online.com/faq/faq_07.asp") if you don't believe me :-) There are many others. 

With Python, you can make program work, profile it to find bottlenecks, and reimplement those in C. Don't guess what to optimize - measure. With C/C++, you are forced to optimize whole program :-) I heard myself why (Google) does not promote Python like Sun does java: they consider Python their competitive advantage, and they will keep it as long as other companies use less productive languages ;-) So it is against their interests to promote Python - they just hire people smart enough to learn it.

> I would suggest starting with simple games with old-school ascii graphics, then when you are familiar with programming you could start using graphics libraries.

Good advice. Learn walk before trying to run.

[learn python wiki]("http://learnpydia.pbwiki.com/HowToStart") is a wiki with links to online books good for beginner, intro to data structures (yes you need to learn it too), and simple problems to solve.

---

### Post by pedrotuga on 2007-02-27
> PHP might be better for simple websites - in python, you need extra templating and CGI which is included in PHP. But unlike PHP, Python is universal language - so you can use it also for non-web projects, and Python is also object oriented, which leads to *much* cleaner structure of bigger projects.
That's actually a mistake repeted over and over again out there, php is a general puprose language. Just because it's widely used on web applications doesnt mean that it's all it does. On the contrary, i sucessefully use it as an improved replacement of shellscript and in all my text manipulation snippets where typically perl would be used. I've done some mathematics with it too and is pretty straitforward in basicaly everything. For those who don't know there is PHP bindings for the win32 native api and other graphical toolkits like gtk.

( ... )

Ok, i got all messed up in my head, pmasiar, you edited you message, i spent a couple of minutes figuring out that you have done so as the message i got by email is slighty diferent than this one.

( ... )

Anyway, i never intended to say that C/C++ is easy, in my opinioin they are not even suited for writting regular desktop applicaitions. On the other hand, when it comes to graphics i think they are more suited because of all the controll they offer and because of the set of libraries avaluable ( opencv, opengl, etc )

To make a big story small, game programming is massive complicated work that requires 'complicated' tehnologies.

---

### Post by pmasiar on 2007-02-27
> **pedrotuga said:**
> That's actually a mistake repeted over and over again out there, php is a general puprose language. Just because it's widely used on web applications doesnt mean that it's all it does. On the contrary, i sucessefully use it as an improved replacement of shellscript and in all my text manipulation snippets where typically perl would be used. I've done some mathematics with it too and is pretty straitforward in basicaly everything. For those who don't know there is PHP bindings for the win32 native api and other graphical toolkits like gtk.

OK I agree that "PHP is for web sites only" is often repeated and might not be 100% true - I also sinned I was not aware you can create windows GUI with PHP (and thanks for mentioning that, even if I do not plan to learn it ATM). Most people use PHP for websites, and because double whammy of (1) their little experience (or PHP being simple to learn - depends on the perspective :-) ) and (2) PHP being *NOT* OOP, it is easy to create messy code, and they do.

Yes I heard that it is possible to use includes/libraries to create code with decent structure - but PHP as language does not make it easy or obvious. OTOH Python *does* make better structure easier and more obvious, it gently nudges the beginner in right direction, while reading avarage PHP program does not.  If average beginners tries to learn best PHP practices by reading average PHP application - results is the mess what we have :twisted:

You may try to say that resulting mess is a proof that PHP is easier than Python :-) but I will disagree. :-)

> Ok, i got all messed up in my head, pmasiar, you edited you message, i spent a couple of minutes figuring out that you have done so as the message i got by email is slighty diferent than this one.

Sorry for confusion - I edited url tag by hand and placed single quote to close double quote for URL to Game Maker (it did not worked ) and text up to link to Galcon dissappeared. :-( Fixed now, thanks for noticing it.

> Anyway, i never intended to say that C/C++ is easy, in my opinioin they are not even suited for writting regular desktop applicaitions. On the other hand, when it comes to graphics i think they are more suited because of all the controll they offer and because of the set of libraries avaluable ( opencv, opengl, etc )

To make a big story small, game programming is massive complicated work that requires 'complicated' tehnologies.

Yup, we agre on that. We also agree that many languages exist for a reason, each trying to be best in its own niche, and languages try to learn from each other. Open-sourced languages like Python, Perl, PHP, Ruby can "learn" from each other (and borrow libraries) easier than closed-sourced languages like C# and untill recently Java.

Of course if you already are proficcient in one language (like you are in PHP) it is easier just pick up new library and continue developing in new area using old language.

My point (and you are free to call it nitpicking) related to your post is that while PHP and Python are about equally easy to start coding small projects, for average beginner Python scales better to bigger projects than PHP. One of the reasons is that for bigger web applications, you start earlier to use templates in Python - even if it means additional learning requirements.

It depends: what other projects original posters plans to work in? Does he plan to contribute to some existing project? What is the language of that project? Learning a language to get a career in big company? Does that company happens to be Google :-) ? etc etc. So many unstated assumptions...

I would also argue that even if we need "complex" technologies, they shoud strive to be not "complicated" - as complicated as necessary but not more. :-)

Python has an easter egg for this: [http://www.python.org/dev/peps/pep-0020/](http://www.python.org/dev/peps/pep-0020/)

---

### Post by Wybiral on 2007-02-27
BASIC is always a good language to start writing games in, and a fine reason for me to self advertise :) because you can always give Basic4SDL a look!!! [http://p13.wikispaces.com/B4SDL](http://p13.wikispaces.com/B4SDL)

And if you need a good module for python to initialize OpenGL (one that is simpler than pygame) you should check out viper: [http://p13.wikispaces.com/viper](http://p13.wikispaces.com/viper) (I've also ported a number of NeHe OpenGL tutorials to python+viper which you might be able to learn from)

I vote python+glut or python+pygame or python+viper

Mainly because it is easy to learn and as has already been mentioned, if you run into any performance bottlenecks (slow spots in your program) you can always pick up a little C or C++ and write a module to smooth things out.

---

### Post by bfree on 2007-06-06
> **pedrotuga said:**
> Sorry for being again the anti-python-hype guy.

Likewise - sorry for being the Perl OpenGL guy, but it's worth mentioning...

I agree that you will get the best overall 3D performance in C/C++ - but you will get nearly the same performance with Perl.  The same cannot be said about Python.

I've recently posted [OpenGL benchmarks]("http://graphcomp.com/pogl.cgi?v=0111s3B2") comparing Perl vs Python, and Perl is over 20% faster than Python, particularly in the area of array handling.  I've included a note from PyOpenGL's author explaining why Python is slower.

I hope to add Ruby benchmarks shortly.

For more on OpenGL C vs Perl and Perl vs Python performance, visit [http://graphcomp.com/opengl/benchmarks](http://graphcomp.com/opengl/benchmarks)

---

### Post by microsoft92sucks on 2007-06-06
If you still want to learn Python here's a really good online book [http://www.ibiblio.org/obp/thinkCSpy/](http://www.ibiblio.org/obp/thinkCSpy/)
it's been helping me I just started a few days ago and the has already tought me a lot.

---

