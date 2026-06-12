---
title: "I know you really aint suppose to ask, but?"
date: 2010-07-31
forum: Programming Talk
---

### Post by k33bz on 2010-07-31
I know nothing of programming, other than html (if that is even considered programming). (as well as a few bash programs, very simple ones I might add). I really want to learn. I have looked over several different languages, but it all seems complicated. 

Now I have alot more time on my hand, so finding time to learn is not much of a problem anymore.

I am not good with math. Basics yes for the most part, but algebra, geometry, calculus, hell even fractions I have problems with.

I have my eye on two different languages, which is why I am here to ask.
perl and python.

I here good and bad things on both. I done a quick tut I found online with perl (actually it is linked in this forum) however still do not know what I am doing.

I am on my own, no mentors or teachers. So really what would be better for me, perl, python, or some other language?

---

### Post by Bachstelze on 2010-07-31
Python is definitely a better choice for beginners IMO. The Python tutorial is clear enough and intended at beginners, it will probably be a good starting point:

[http://docs.python.org/py3k/tutorial/index.html](http://docs.python.org/py3k/tutorial/index.html)

Feel free to ask here if you don't understand something, that's what this forum is for.

---

### Post by k33bz on 2010-07-31
> **Bachstelze said:**
> Python is definitely a better choice for beginners IMO. The Python tutorial is clear enough and intended at beginners, it will probably be a good starting point:

[http://docs.python.org/py3k/tutorial/index.html](http://docs.python.org/py3k/tutorial/index.html)

Feel free to ask here if you don't understand something, that's what this forum is for.

Oh I guarantee I will be back with more questions, lol. But I like trying to figure stuff on my own before I post. In the past I have looked for answers very little or not at all. Then post how to do something, 5 mins later I find my answer, lol, no joke.

But when a problem arises, that I cant seem to find the answer, best believe I will be asking :)

Imma go take a look at that link. Thanks :)

---

### Post by k33bz on 2010-07-31
ok so quick question, according to that guide they are using python3.1. Which I have python installed, but apparently not 3.1. So I installed it. However it appears I have two different versions. Which is best to use:

```
keebler@mobile:~$ python3.1
Python 3.1.2 (r312:79147, Apr 15 2010, 12:35:07) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> quit()
keebler@mobile:~$ python
Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> quit()

```

a little side not :) == I think I like python more than perl already. I never saw where I could do basic math or any kind of math with out naming something, python does, built in logic?

---

### Post by Bachstelze on 2010-07-31
> **k33bz said:**
>  Which is best to use:



[http://wiki.python.org/moin/Python2orPython3](http://wiki.python.org/moin/Python2orPython3)

Python 3, unless you really need Python 2.

By the way, the tutorial for Python 2 is here if you want it: [http://docs.python.org/tutorial/index.html](http://docs.python.org/tutorial/index.html)

---

### Post by 23dornot23d on 2010-07-31
I just saw this thread and I just started using Python a few weeks ago, 

Have you got [ERIC]("http://eric-ide.python-projects.org/") ..... 

It just makes it a bit easier to edit and run programs - to test them.

---

### Post by k33bz on 2010-07-31
Nice, I have it now, thanks for the link :)

Ok, I have it downloaded, but having dependecy problems

```
Sorry, please install PyQt4.
```

however I have python Qt4 installed :(

---

### Post by 23dornot23d on 2010-07-31
Install it from the repository ..... (you look as if you have gone and got the latest version)

I too have that same warning on the latest version eric5
( I am in the process of doing a aptitude safe upgrade now on Maverick to see if I can solve it )
( even after the the upgrade and adding the [Python ppa]("https://launchpad.net/%7Emedigeek/+archive/ppa-python") no luck with the eric5 ) 
Error: No module named PyQt4.QtCore

But the one in the repository although older works fine ..... sorry should have said it was
there,

---

### Post by k33bz on 2010-07-31
> **23dornot23d said:**
> Install it from the repository ..... (you look as if you have gone and got the latest version)

I too have that same warning on the latest version eric5
( I am in the process of doing a aptitude safe upgrade now on Maverick to see if I can solve it )
( even after the the upgrade and adding the Python ppa no luck with the eric5 ) 
Error: No module named PyQt4.QtCore

But the one in the repository although older works fine ..... sorry should have said it was
there,

its all good, guess I should of checked the repo to see if it was there first anyway :)

---

### Post by 23dornot23d on 2010-07-31
Ok good to know ..... 

I should have looked at the readme ..... seems to get the latest eric5 to work needs a bit more work.

If the required packages (Qt4, QScintilla2, sip and PyQt4) are not installed, 
        please get them and install them in the following order [COLOR=Red](order is important).[/COLOR]
        
            1. Install Qt4
            
            2. Build and install sip
            
            3. Build and install QScintilla2
            
            4. Build and install PyQt4
            
            5. Build and install QScintilla2 Python bindings
            
            6. Install eric5

---

### Post by k33bz on 2010-07-31
I think I will work with the one from the repo. But from the looks of it I am going to have to read a manual. Not use to working within IDEs and debuggers and the such. Just been doing mine from interactive.

---

### Post by 23dornot23d on 2010-07-31
Ok I started with gedit and created a small file

test.py

with something simple in it like this

a=2+2
b=4+4
print a
print b
print a+b


then to run the file in its current directory

just type

python test.py


With eric ..... load in that same file ......

(File - open .... choose Python Files)

and just press start or F2
Then press return to get rid of the pop up

The program output is shown at the bottom of the page

---

### Post by k33bz on 2010-07-31
o ok, so just use eric as a debugger?

I thought I could use it to help with the writing out the code as well.

---

### Post by 23dornot23d on 2010-07-31
I started with it and then moved on ,,,,, my main interest is to use it in Blender for 3D work I do

this is where I was about a [month ago with Python]("http://sites.google.com/site/blenderlearn/assignments/project035")

I am just learning so what I am doing is finding quick ways of producing useful things.

I like Blender - it has a Python editor built in and I like to be able to see what it is I am producing
quickly.

It depends what you are going to do with it ..... there is a good link to qt4 ...... and a small video showing
how to use it .

---

### Post by k33bz on 2010-07-31
nice,
Im just learning myself. For years I wanted to get into programming, but neither understood and dint have the time to learn, or just got to lazy. Now I have the time, and really want to pursue it. Im in my 30s so I feel like I am late in the game. But guess it is never to late to learn something new. 

So I am here :)

---

### Post by 23dornot23d on 2010-07-31
Thats good ,,,, me I am 52 and always learning ..... I love it  and with linux there are so many things to do ..... 

I keep going from one thing to the next - but always interesting ..... 

I like visual results as I do not learn well from books ..... 
So thats why the 3D things suit me ..... everybody is different I suppose ....

But I like to have a go and see what things do ..... if they work fine 
If not ..... I find another way to do what I want to do ....

If you have a plan for what you want to do ......
I find creating a blog page and foillowing up on my ideas works ,,,, and keeps a history too.


The basics of programing I picked up a long time back ...... but from trying things like BASIC
 So Loops and IF statements are useful to learn ..... and lots of Variables .....;)

Just give us an idea of what you want to do .... have a look through my pages there are loads of
ideas ..... I go from one thing to another quickly though .......

My main interest is to create a 3D animation at some point ..... once I know enough

---

### Post by ghostdog74 on 2010-07-31
> **k33bz said:**
> 
I am on my own, no mentors or teachers. So really what would be better for me, perl, python, or some other language?
Perl, Python, they are just as good at doing their job. The thing i like about Perl is its vast amount of libraries at CPAN, and its ability to create one liners (easily). try to learn both.

---

### Post by k33bz on 2010-07-31
> **23dornot23d said:**
> Thats good ,,,, me I am 52 and always learning ..... I love it  and with linux there are so many things to do ..... 

I keep going from one thing to the next - but always interesting ..... 

I like visual results as I do not learn well from books ..... 
So thats why the 3D things suit me ..... everybody is different I suppose ....

But I like to have a go and see what things do ..... if they work fine 
If not ..... I find another way to do what I want to do ....

If you have a plan for what you want to do ......
I find creating a blog page and foillowing up on my ideas works ,,,, and keeps a history too.


The basics of programing I picked up a long time back ...... but from trying things like BASIC
 So Loops and IF statements are useful to learn ..... and lots of Variables .....;)

Just give us an idea of what you want to do .... have a look through my pages there are loads of
ideas ..... I go from one thing to another quickly though .......

My main interest is to create a 3D animation at some point ..... once I know enough

Right now I just want to learn what I can. Taking steps to learn, and not rushing through any certain process. Short term goal is really to make first a good program to do backups. Which I can do in batch I guess, but there are a few obstacles. So I figure doing it in a (REAL) programming language would do the job. Plus it would give me a stepping stone, cause next I like to create a GUI app for backing up and small games.

Long term goals is to have a good understanding in several programming languages maybe help with some games as well as maybe even get a job as a programmer.

So there you have it some of my short term as well as long term goals.

---

### Post by k33bz on 2010-07-31
> **ghostdog74 said:**
> Perl, Python, they are just as good at doing their job. The thing i like about Perl is its vast amount of libraries at CPAN, and its ability to create one liners (easily). try to learn both.

I wanted to tackle perl at first, cause I see it all the time (i download alot of scripts that people have written). However going through a tut I came out not really knowing what I was doing. It would seem that I would love perl, but it also seems complicated to learn. So I went with python, after I actually learn the basics, is when I will go check out perl again. Since I read somewhere that once you know one language, it is not hard at all to learn any others. :)

No worries, I have not giving up on perl, just put it off to the side for now.

---

### Post by ghostdog74 on 2010-07-31
> **k33bz said:**
>  However going through a tut I came out not really knowing what I was doing. 
was that other people's impression imprinted in your mind or is it really that hard to understand ? Which tutorial? Please go to the official doc site and see [perlintro]("http://perldoc.perl.org/perl.html")

---

### Post by 23dornot23d on 2010-07-31
Python and Qt4 work well together ... for forms and your GUI ....
Takes a while to load ..... but worth a watch if you are starting out building a GUI

[watch this video]("http://www.wysota.eu.org/tutorials/tut_designer1.avi") its easy to follow and provided me with my first GUI
you can create the python file from it to use ..... in your main program too.

---

### Post by k33bz on 2010-07-31
> **ghostdog74 said:**
> was that other people's impression imprinted in your mind or is it really that hard to understand ? Which tutorial? Please go to the official doc site and see [perlintro]("http://perldoc.perl.org/perl.html")

that would be my impression.

this is the tut I tried:
[http://www.sthomas.net/roberts-perl-tutorial.htm]("http://www.sthomas.net/roberts-perl-tutorial.htm")

---

### Post by k33bz on 2010-07-31
> **23dornot23d said:**
> Python and Qt4 work well together ... for forms and your GUI ....
Takes a while to load ..... but worth a watch if you are starting out building a GUI

[watch this video]("http://www.wysota.eu.org/tutorials/tut_designer1.avi") its easy to follow and provided me with my first GUI
you can create the python file from it to use ..... in your main program too.


Thanks for the link, I will be checking it out first thing tomorrow while wife n kids at church. :)

---

### Post by ghostdog74 on 2010-08-01
> **k33bz said:**
> that would be my impression.

this is the tut I tried:
[http://www.sthomas.net/roberts-perl-tutorial.htm]("http://www.sthomas.net/roberts-perl-tutorial.htm")

that was in 1999 !! , Always go to the official documents because updates and new syntax to the  language are updated there. There are also tons of information regarding Perl on the site. Go there and read about them.
There are also [Qt bindings for Perl.]("http://tinyurl.com/25ozm3x")

---

### Post by k33bz on 2010-08-01
> **ghostdog74 said:**
> that was in 1999 !! , Always go to the official documents because updates and new syntax to the  language are updated there. There are also tons of information regarding Perl on the site. Go there and read about them.
There are also [Qt bindings for Perl.]("http://tinyurl.com/25ozm3x")

o wow, wish I would of known that, lol. However I do have your links book marked and will be looking at them tomorrow.

---

