---
title: "[SOLVED] obtaining c"
date: 2009-01-07
forum: Programming Talk
---

### Post by smurfgod on 2009-01-07
i was wandering if someone knew were i could get a copy of c that will run on linux(ubuntu)???thanks


smurf    :D

---

### Post by jimi_hendrix on 2009-01-07
sudo apt-get install build-essentials

compile your program with

```

gcc -o executableNameGoesHere file.c

```

run the executable with 

```

./executableNameGoesHere

```

---

### Post by ggaaron on 2009-01-07
You mean C compiler? If yes, you want GCC, you can get it from repositories (use synaptic).

---

### Post by mali2297 on 2009-01-07
Install the package build-essential from the official repositories (with the applications apt-get, aptitude or synaptic). Then you will get the GNU C Compiler (GCC). 

Also see [http://ubuntuforums.org/showthread.php?t=689635](http://ubuntuforums.org/showthread.php?t=689635).

---

### Post by smurfgod on 2009-01-07
i was actually wanting everything...from the ground up.my internet is gonna get cut off for about a week and i was wanting to fool around with it.i mean i need EVERYTHING to program with c.anything that will let me run c on linux.thanks,but in the meantime i will get the compiler.thanks

smurf    :D

---

### Post by jimi_hendrix on 2009-01-07
what do you mean "run C"

---

### Post by ggaaron on 2009-01-07
Isn't this compiler + libraries? GCC should be everything you need, build-essential will surely be enough.

---

### Post by smurfgod on 2009-01-07
i did the sudo apt get thing and it said the package didnt exist.i installed from the add/remove--eclipse,kwsdl compiler,anjuta ide,and KDevelopment.what else do i need??when my internet gets cut off i want to be able to play around with it.


smurf   :D

---

### Post by smurfgod on 2009-01-07
i went to synaptic and i already have gcc-4.3 installed
i went ahead and installed .base,.doc,.locales,.multilib,and .source.they were right below the gcc-4.3.what else do i need???and how do i get to it???


smurf  :D

---

### Post by smurfgod on 2009-01-07
> **jimi_hendrix said:**
> sudo apt-get install build-essentials

compile your program with

```

gcc -o executableNameGoesHere file.c

```

run the executable with 

```

./executableNameGoesHere

```

when i did it,terminal said it could find a build package???i dont have anything built yet if thats what thats for.

---

### Post by smurfgod on 2009-01-07
ok....i did it again and it says its the newest version...but i cant find it???were is it..i went to the programming tab under apps and all i have is KDevelopment stuff...is that it???


smurf  :confused:

---

### Post by smurfgod on 2009-01-07
ok...is KDevelopment the same as c and if so can i get the c help me books???

---

### Post by ggaaron on 2009-01-07
I think that you rally should get some tutorial how to do c programming and read how it is really done, because you are messing up with things. You don't run c, you compile c source code to executable with a compiler like GCC. And half of the programs you've installed are IDEs.

---

### Post by ggaaron on 2009-01-07
You can look on this resources:
[http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/)
[http://www.faqs.org/docs/learnc/](http://www.faqs.org/docs/learnc/)

---

### Post by smurfgod on 2009-01-07
can u tell me what i have messud up???all i want to do i write a program for c.what program do i need to do that???thats all im asking


smurf  :D

---

### Post by shadylookin on 2009-01-07
> **smurfgod said:**
> can u tell me what i have messud up???all i want to do i write a program for c.what program do i need to do that???thats all im asking


smurf  :D

well you write programs in C not for C. C is a programing language for which you need a compiler to make sense of. 

if you get build-essential from synaptic then you'll be able to compile C code that you(or anyone else) have written.

Since you're a beginner to computer programing you might want to consider choosing something easier than C to start off with.

---

### Post by jimi_hendrix on 2009-01-07
typo...build-essential is the package

---

### Post by smurfgod on 2009-01-07
what would u recodmend other than c???i folled around with vb6 enterprise for a while but didnt get anywere.i have eclipse installed also..thats for java...right???anyway,i am new to peogramming and would just like to fool around with whatever will work for linux.ubuntu to be exact.thanks..

smurf   :D

---

### Post by cmay on 2009-01-07
the languages for linux is c  bash c++ perl python and so on. if you want to learn c i think you should  just use the library and find some good books like brian kernighans the unix programming enviroment and the c programming language. if you just make sure as already suggested to have the build-essential package installed it will be enough to get you started. one more package could be gnome-devel which installs some stuff useful for the development of gnome.(ubuntu default desktop enviroment)

---

### Post by ggaaron on 2009-01-07
To write code you need a text editor. To compile it you need compiler. Eclipse is an IDE - an editor with some features for programmers, you can develop in many languages using it. For start try python - you don't have even to compile it, there is a great manual for python:
[http://docs.python.org/tutorial/index.html](http://docs.python.org/tutorial/index.html)

---

### Post by jimi_hendrix on 2009-01-07
id find a bunch of programming challanges if i were you too...keep you busy...

also pick a goal project to work on...get tutorials for what you think you will need...and get hacking after you learn the language of yoru choice

---

### Post by .Maleficus. on 2009-01-07
First of all, I second the Python vote.  You already have it installed on your computer and it's *much* easier than C.  It will help you get a grasp on the neccessary skills for migrating to C.

Second, jimi_hendrix has a good idea with finding programming challenges.  I would recommend Project Euler - the are all math based, will require you to use loops and learn good program structure.  All of them are designed to take less than 1 minute to execute so it's very obvious if you do it wrong/badly.

After that, once you have a good handle on the language and it's functions, check out this thread on [DreamInCode]("http://www.dreamincode.net/forums/showtopic78802.htm").  It will keep to going for a very, very long time.

Good luck.

---

### Post by jimi_hendrix on 2009-01-07
your probably fine with C as long as you get a good book and you dont mess around with pointers too early (you shouldnt need to)

---

### Post by smurfgod on 2009-01-07
people were talking about python...i cant find it anywere.i went to the programming tab and clicked PIDA and it said it was starting and that it loved me...but thats it.can someone direct me on how to make it actually open???


smurf   :confused:

---

### Post by Sorivenul on 2009-01-07
Okay. Easy answer - read the Stickies:
[LIST]
[*][Read Before Posting: Forum FAQ's, how to learn to program, and Linux programming]("http://ubuntuforums.org/showthread.php?t=1006666")
[*][Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662")
[/LIST]

I personally don't suggest C for beginners, but ultimately it is your choice. Python, which has already been mentioned is, IMO, faster and easier to learn the basics of. The Stickies have excellent links on this as well.

That said, you won't find "Python" or "C" in your menu, as they are languages, not graphical programs themselves. You are probably looking for Integrated Development Environments (IDEs), of which many are covered by the Stickies. For C/C++ I liked Anjuta or Geany to begin with, and SPE (Stani's Python Editor) for Python. 

Good luck!

---

### Post by smurfgod on 2009-01-07
ok...i have spe and all the files that came with it.also i have anjuta.is there some sort of book to get me started???


smurf   :D

---

### Post by Sorivenul on 2009-01-07
> **smurfgod said:**
> ok...i have spe and all the files that came with it.also i have anjuta.is there some sort of book to get me started???


Okay, this is also covered by the stickies. Also, before you lose your internet, Google is your friend as well.

The best python resource to start with, IMO, is the [LearnPython wiki]("http://learnpython.pbwiki.com/"). For C check out [http://www.cprogramming.com/]("http://www.cprogramming.com/") and look at the links on the left-hand side of the page.

Cheers.

---

### Post by smurfgod on 2009-01-07
i just downloaded some 135 'for dummies' books and im gonna go to my library tomorrow and actually check out the c for dummies book.do u know were i can download the python for dummies...if there is one???

---

### Post by Sorivenul on 2009-01-07
> **smurfgod said:**
> i just downloaded some 135 'for dummies' books and im gonna go to my library tomorrow and actually check out the c for dummies book.do u know were i can download the python for dummies...if there is one???
Unless you buy it digitally through a retailer, I couldn't say. The LearnPython wiki I already mentioned is, again IMO, the best way to get started. 

If you're looking for a book to download [Dive into Python]("http://www.diveintopython.org/"), [How to Think Like a Computer Scientist: Learning with Python]("http://openbookproject.net//thinkCSpy/"), [A Byte of Python]("http://www.swaroopch.com/notes/Python"), or the [Python Programming Wikibook]("http://en.wikibooks.org/wiki/Python_Programming"), may be a start.

---

### Post by smurfgod on 2009-01-07
i got em....thanks for all the help

smurf  :D

---

### Post by Sorivenul on 2009-01-07
> **smurfgod said:**
> i got em....thanks for all the help
No problem. No doubt you will find this Forum invaluable as you start and continue your programming and Linux journey. Good luck!

---

### Post by jmartrican on 2009-01-07
> **Sorivenul said:**
> 

I personally don't suggest C for beginners,

When I was in school it was the opposite.  C was taught to beginners so that they can easily master the other languages.  I'm sure its easier to go from C to other languages then from other languages to C.  C teaches you fundamentals.

---

### Post by Sorivenul on 2009-01-07
> **jmartrican said:**
> When I was in school it was the opposite.  C was taught to beginners so that they can easily master the other languages.  I'm sure its easier to go from C to other languages then from other languages to C.  C teaches you fundamentals.

I may agree, but it would almost have to be in a University/College setting. My attempts to teach myself C when I was a bit younger were mostly in vain. When I finally took a class I had to unlearn so many bad practices I had gotten myself into it was like learning an entirely new language. 

There are many articles and posts around here on C vs other languages, including the ease of the move from C to other languages and vice-versa. I don't personally buy that moving from C to another language would be easier than Python to the same language or Java to the same language. Many classmates of mine had a hard time moving from C to Java when our university switched the curriculum. 

Almost any mainstream language can teach you the fundamentals, and the ease of the move depends on the user and the language moved to, IMO. 

Just my two cents.

---

### Post by namegame on 2009-01-08
> **jmartrican said:**
> When I was in school it was the opposite.  C was taught to beginners so that they can easily master the other languages.  I'm sure its easier to go from C to other languages then from other languages to C.  C teaches you fundamentals.

I'm currently a Computer Science major at Clemson University, a school known for Engineering and Science.

Currently, the typical language progression, from beginning to end, is C to C++ to Java, then it varies depending upon what you focus on.

---

### Post by pmasiar on 2009-01-08
> **namegame said:**
> I'm currently a Computer Science major at Clemson University, a school known for Engineering and Science.

Currently, the typical language progression, from beginning to end, is C to C++ to Java, then it varies depending upon what you focus on.

MIT starts with Python, and I would guess they are also "a school known for Engineering and Science" at least a little bit :-)

---

### Post by cmay on 2009-01-08
before you loose your internet you could print all the online matrial you find to pdf files . i did that when i first started on linux. just got to use them now after 3 years. the official debian docs are kinda hard on newbies to linux but i just thourgth i would mention the idea even that it could take some time to do. 
good luck.

---

### Post by CptPicard on 2009-01-08
> 
Currently, the typical language progression, from beginning to end, is C to C++ to Java, then it varies depending upon what you focus on.

That sounds so wasteful... the basic idea of all those languages is essentially the same, so it gives no opportunities to paradigm-shift your mindset, and besides, the "progression" doesn't progress :) Starting with Java would at least get one programming ASAP.

> **pmasiar said:**
> MIT starts with Python, and I would guess they are also "a school known for Engineering and Science" at least a little bit :-)

And to think that they used to start with Scheme...

---

### Post by namegame on 2009-01-08
> MIT starts with Python, and I would guess they are also "a school known for Engineering and Science" at least a little bit.

I almost applied to MIT. I have great respect for the school, but then I realized that I could not afford the tuition without a significant scholarship.

> **CptPicard said:**
> That sounds so wasteful... the basic idea of all those languages is essentially the same, so it gives no opportunities to paradigm-shift your mindset, and besides, the "progression" doesn't progress :) Starting with Java would at least get one programming ASAP.


Unfortunately, a small handful of students can't change the curriculum. If money weren't an issue I would look into transferring to a more "open-minded" school. As a matter of fact, I was sitting in my "Software Development Foundations" class and the instructor was rattling off various "popular" languages today. C++, Java, and the .Net languages were all mentioned. I mentioned Python and the instructor refused to acknowledge it as a "real computer language." It was frustrating to say the least. 

The school seems to be focused on developing "code-monkeys" and/or "blub-programmers," as many members of this forum have called them. As of now, I am forced to follow the University mandated curriculum, but what I decide to learn/code in my own time is my business.

---

