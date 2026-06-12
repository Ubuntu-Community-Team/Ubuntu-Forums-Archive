---
title: "Where to start, where to start???"
date: 2005-08-12
forum: Programming Talk
---

### Post by noob_Lance on 2005-08-12
Hey, ive decided that im going to make my own application, but the question is where do i start. I dont know ANY programming languages except for a few web codes. And thats where this comes in. i want to create a program that will actually let me create and edit my own scripts (php) in it. But the thing is, i want to be able to preset code snippets so that i can just click on it and it inserts. i know most of this dosnt even matter, i just wanted ot give a little insight as to what it was going to be like. Since i have no clue where to start, any help or suggestions would be good, any good programs to help me along my way??? 

Thanks Alot, and best regards
~Lance

---

### Post by DJ_Max on 2005-08-12
You need to crawl before you can walk. Meaning, you actually need to learn a language before you can create applications, especially GUI apps. There are loads of information on the net, quite a few exist on these forums.

[http://ubuntuforums.org/showthread.php?t=50916](http://ubuntuforums.org/showthread.php?t=50916)
[http://ubuntuforums.org/showthread.php?t=13507](http://ubuntuforums.org/showthread.php?t=13507)

---

### Post by noob_Lance on 2005-08-12
before i check the links... is java a good start?

---

### Post by DJ_Max on 2005-08-12
Yes & no. Java can be overly complicated, but has a lot of good ideas. It'is proprietary software, so may be a little difficult to get installed. Start with something easier like Ruby or Python. I just don't care much for Java anymore after I found Ruby.

---

### Post by Buffalo Soldier on 2005-08-13
If you're thinking of developing apps for Ubuntu, according to [http://www.ubuntulinux.org/community/bounties/](http://www.ubuntulinux.org/community/bounties/)
> Ubuntu prefer the community to contribute work in Python. We develop our own tools and scripts in Python and it's much easier for us to integrate your work if you use the same platform.A good intro page would be:

[http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

[https://wiki.ubuntu.com/WelcomeToPython](https://wiki.ubuntu.com/WelcomeToPython)

---

### Post by noob_Lance on 2005-08-13
oh man, this is gunna take a while... lol. which is easier... python or ruby?? lol

---

### Post by Buffalo Soldier on 2005-08-13
[QUOTE=noob_Lance]oh man, this is gunna take a while... lol. which is easier... python or ruby?? lol[/QUOTE]Supporters for either language has many arguments and counter-arguments for which one is easier, better, faster and bla bla bla. And some discussions has turn into flamewars when regarding this matter.

I think both have their pros and cons. I guess you just have to give it a try and see which fits your taste or objectives.

---

### Post by DJ_Max on 2005-08-13
[QUOTE=Buffalo Soldier]Supporters for either language has many arguments and counter-arguments for which one is easier, better, faster and bla bla bla. And some discussions has turn into flamewars when regarding this matter.

I think both have their pros and cons. I guess you just have to give it a try and see which fits your taste or objectives.[/QUOTE]
 Thats probably the best response I've seen to a post like that in a while.

Just use what you like when you look at them both.

---

### Post by wtd on 2005-08-13
You'll likely find that both have their uses.

---

### Post by noob_Lance on 2005-08-13
which one can i do the following basically... In a GUI mind you


-save a file
-read from the file, and use items in the menu
-Insert code snippets from a pop up in the program itself (like entering a URL here when ya hit the hyperlink button)
-- Well i have Many many other things id need to do, but wont list here... thats the major stuff id need lol.
-possibly even a php.ini editor built in... to make it easy to edit and such..

Regards
~Lance

---

### Post by npaladin2000 on 2005-08-14
I did a little looking at Ruby.  Been trying to decide whether to learn Ruby or Python.  They're fairly equal from the perspective of not knowing either one, but there are a couple of major differences:

1. More graphical tools available for Python
2. Python more widely in use

And I'm not sure if 3 causes 2 or if 3 is caused by 2, but:

3. MUCH better documentation available for Python, including free "learning python" books, tutorials, and commercial textbooks. I've hardly found any for Ruby.

Ruby might be a good enough language (and from what I've read and managed to understand it IS rather elegant), that doesn't help if you can't learn it and get help with it.  With Ubuntu, you're more likely to get more help with Python.

Hence, I picked Python.

---

### Post by noob_Lance on 2005-08-14
how do i compile python to test it :S!

~Lance

---

### Post by jerome bettis on 2005-08-14
python is interpreted, not compiled.  well you can actually compile the source files into bytecodes (like in java).  but you can just type python x.py to run it.  or you can put #!/usr/bin/env python as the first line in your file (this is called the shebang line that tells the shell that this is a script to be interpreted with that program).  then do chmod 755 x.py and you can run it directly with ./x.py ... this is what i do, it's the same thing but less typing.  also if you want to do this it has to have a py extension, which is not neccessary (but still recommended) if you're going to run it the other way.

sounds like you need to start here:
[http://www.python.org/doc/2.4.1/tut/node3.html](http://www.python.org/doc/2.4.1/tut/node3.html)

---

