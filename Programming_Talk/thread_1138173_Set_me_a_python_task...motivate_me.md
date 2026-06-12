---
title: "Set me a python task...motivate me"
date: 2009-04-26
forum: Programming Talk
---

### Post by aaronp on 2009-04-26
Hey all,

I've been trying to learn Python for a fair while now but just can't get into it because I don't have any problems that need solving!
I'm not good at learning programming languages by just reading tutorials and doing menial little tasks that result in comparing a few strings or printing calculation results to stdout. I can only really get motiviated by having a reasonable sized project in front of me and fumbling my way around until I've made every mistake there is to make.
I have experience with OO programming languages (Java, C++) and also a bit of Visual Basic, plus some ActionScript2 and php.

Just wondering if anyone has a little project that might be good to get me stuck into it and learn some of the basics and differences of python? It doesn't have to be a real one, if you want to make something up and then review my developed product for me then feel free but I am not good at making up my own projects without having a real problem to solve.

Cheers
Aaron

---

### Post by Bodsda on 2009-04-26
I struggled with the same thing and this is the task I chose.

Find the track name and artist of the song you are playing in <insert name of favorite media player> then go off and get the lyrics for that song. Then display those lyrics using graphics modules or maybe pygame, or if you dont like/not good at graphical programming just use 'zenity'

Hope this gets you going,

Bodsda

---

### Post by simeon87 on 2009-04-26
I'm going to say the following anyway, despite the fact that you've opened a thread for it. I think the project that works best is one that you have chosen yourself. There are many types of software but you may not feel like programming them.. for example, we could suggest to create a game but perhaps you'd rather work on a text editor or something mathematical, like a theorem prover. It's harder to stay motivated when the Oh-Now-I-Need-To-Debug phase of your new project begins when you're working on a project that you've not chosen yourself.

---

### Post by stimpack on 2009-04-26
The one I used was to create a PasswordHasher, it took a website name and a master password and created a long secure password for logins.

As simeon87 said, you need the right project for you however, this was highly motivating for me as Firefox3 had just broken my PasswordHasher addon..

---

### Post by aaronp on 2009-04-26
> **stimpack said:**
> The one I used was to create a PasswordHasher, it took a website name and a master password and created a long secure password for logins.

As simeon87 said, you need the right project for you however, this was highly motivating for me as Firefox3 had just broken my PasswordHasher addon..

thanks guys. Yeah I was figuring there'd be a few varied responses then I'd start by picking the one that most interested me. However, my motivation is just to learn the language so I'd probably be happy doing any project as long as it is reasonably well defined and allows me to stuff up a bit before i get the right solution.

---

### Post by Flash858 on 2009-04-26
I don't know if this is something that could be done in Python, as I am not a programmer, but there is one utility I have always wanted:

During install, Ubuntu, and several other distros scan all partitions looking for operating systems to add to the grub loader. 

It would be fantastic to have a stand-alone utility that does just that from a boot cd for when you hose your loader adding new distros to partitions. It would then create a new MBR, fstab, and menu.lst, including all the bootable OSes on the system (even Windows and LiLo loaded distros).

LMK if that is possible.

---

### Post by ashmew2 on 2009-04-26
Something that will probably keep you busy for a few days would be making F.L.A.M.E.S = FriendShip / Love / Affection / Marriage / Enemy / Sister .

You basically input two names ,strike off count the common characters , use the number of characters left after striking off common characters and using that number to calculate one of the 6 letters (FLAMES).
Tell me if you need any more info about this.

I made this in C++ after struggling for a bit and i am at the same level as the OP and i needed something to motivate myself. I found out about this from a girl in High School and thought to myself that it would be interesting to write an algorithm. ;)

PS - Nice Ideas from the people who replied before me..Cheers! ::D

---

### Post by Barriehie on 2009-04-26
I chose to write a python script that emulates [Conway's Game of Life]("http://en.wikipedia.org/wiki/Conway%27s_Game_of_Life").  It's rather slow but it works!  Let me know if you'ld like the code.

Barrie

---

### Post by nvteighen on 2009-04-26
Write a Python program that chooses a program you may write... :)

No, seriously: look up what kind of programming you like. Theorical algorithmics, system utilities programming, network, games, applications?

---

### Post by amingv on 2009-04-26
> **Flash858 said:**
> I don't know if this is something that could be done in Python, as I am not a programmer, but there is one utility I have always wanted:

During install, Ubuntu, and several other distros scan all partitions looking for operating systems to add to the grub loader. 

It would be fantastic to have a stand-alone utility that does just that from a boot cd for when you hose your loader adding new distros to partitions. It would then create a new MBR, fstab, and menu.lst, including all the bootable OSes on the system (even Windows and LiLo loaded distros).

LMK if that is possible.

You mean like supergrub?
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

It does some of those things you say.

---

### Post by delfick on 2009-04-26
think of a task you do often where there is a lot of repetition involved....

for example, (this wasn't my first, but one I did whilst still learning python), I go to university, and so I print out lecture notes quite often.

However, the lecture notes are usually one slide per page, and that's a lot of paper.

So, using this program here [http://multivalent.sourceforge.net/](http://multivalent.sourceforge.net/) I can make it so there are a certain number of slides per page arranged in a certain way (used to use fineprint when in windows)

however, when I first discovered multivalent, this meant I had to use the commandline and do something like 

java -classpath /usr/local/multivalent/Multivalent20060102.jar tool.pdf.Impose example.pdf -dim 2x2 -l tl

for every single one of them

(well, I made an alias in .bashrc so I didn't have to write the java stuff everytime, but you get the idea)

So I made a script so all I had to do was save the lecture notes (and prac sheets, etc) in particular folders, configure the script to assign options to files with particular names and then run my script.

whilst I don't have my original version anymore (was slightly crappy :p), I recently made it slightly better and have attached it just for the sake of attaching it).


Either way, excuse me for getting a little carried away.

The morale of the story is think of some annoying task and automate half of it with python :)

---

### Post by aaronp on 2009-04-26
> **delfick said:**
> 
The morale of the story is think of some annoying task and automate half of it with python :)

thanks delfick - I'll have to have a think about that. I'm sure there are plenty of things that I do daily or more often that I could automate. I usually end up writing a shell script though, should just start trying to do it in python. Maybe I can convert my existing shell scripts to pyhton...

Thanks for the other replies - some good ideas comnig out now, a couple that I think I'll have a go at

keep them coming though!

---

### Post by sarang on 2009-04-26
I was in the same place - I didn't want to code any of the 'Hello World' or 'Intro to Objects' kind of programs as I had already done that in other languages. Here are the two 'real' projects I started working on:

(1) A web-based photogallery using django ([http://www.djangoproject.com/](http://www.djangoproject.com/)) supporting tags, searching etc. 
(2) Metadata manipulation tool for images. Something like exiftool, but written in python instead of perl. For use with (1).

And yes, for automating annoying OS-related tasks, I mostly find shell scripts better suited for the job than python.

---

### Post by Sprut1 on 2009-04-27
I love network programming so I've made tons of server/client chat programs including IRC clients and such. Making an IRC client is insanely fun, either an full blown GUI IRC client or just an terminal based IRC bot. Just my 0,02$ if you like networking programming :)

---

### Post by Kilon on 2009-04-27
> **aaronp said:**
> Hey all,

I've been trying to learn Python for a fair while now but just can't get into it because I don't have any problems that need solving!


That is impossible. We are surrounded by billion of problems. Some of the, are not apparent until we accidently find the solution to them. 


Many discoveries happened while scientists were dealing with completely diffirent kind of problem , in some case it was not even considered a problem in the first case until a much better implementation was found. 

You must try to keep an open mind, there is a room of improvement for just about anything. 

If you just start with python, I will advice to start step by step. Start small and go bigger and bigger. Finish your project in one week and then just upgrade and upgrade and upgrade .....

Also do not pick some others project , start your own or find one that really interests you. The most important think is to enjoy yourself and you can only do this if you really believe that what you do is very important. If it is just fooling around then quickly you will loose interest.

---

### Post by Free Thinker on 2009-04-27
I needed a program earlier that would take a paragraph, or set of paragraphs and delete all of the spaces, punctuation, numbers and capitalisation, producing another text document with each word on a separate line and in alphabetical order.

I'm guessing this is fairly simple to make, but I haven't had the time to learn any programming yet. :(

---

### Post by aaronp on 2009-04-27
> **Free Thinker said:**
> I needed a program earlier that would take a paragraph, or set of paragraphs and delete all of the spaces, punctuation, numbers and capitalisation, producing another text document with each word on a separate line and in alphabetical order.

I'm guessing this is fairly simple to make, but I haven't had the time to learn any programming yet. :(

sounds like a school programming assignment :-P

---

### Post by Flash858 on 2009-04-30
Supergrub (which I use al the time) only boots and restores the mbr if you have a valid menu.lst and fstab somewhere. If there is an error in either, you have boot issues. What is desperately needed is a boot disk utility that actually creates both for you, and restores the mbr as well. Evidently it is possible, as it happens during install.

I would LOVE this utility...

---

### Post by .Maleficus. on 2009-04-30
As far as automating system tasks goes, you might be interested in this: Python for Bash scripters ([http://magazine.redhat.com/2008/02/07/python-for-bash-scripters-a-well-kept-secret/](http://magazine.redhat.com/2008/02/07/python-for-bash-scripters-a-well-kept-secret/)).

Also, for just learning Python (I'm surprised no one has mentioned these)

Project Euler - [http://projecteuler.net/](http://projecteuler.net/)
Python Challenge - [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/)

---

