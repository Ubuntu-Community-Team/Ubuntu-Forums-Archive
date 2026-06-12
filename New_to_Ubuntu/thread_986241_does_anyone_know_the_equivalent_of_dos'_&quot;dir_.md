---
title: "does anyone know the equivalent of dos' &quot;dir /p&quot;?"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by pluckypigeon on 2008-11-18
I am aware that typing "dir" works in a linux and dos command line.

Does anyone know the equivalent of "dir /p"?

That command lists the directories and files but it breaks the list down in to parts. You can select the next part by pressing the Return key.

Any ideas?

Thanks in advance!

---

### Post by bscbrit on 2008-11-18
Whenever you want to divide data into a page at a time you should pipe the data into 'less'.

The pipe command is '|', without the quotes, and it is the character to the left of z on an English keyboard, shifted.

So you would type 'dir | less' in this instance.  It works for any command however, not just for 'dir'.

---

### Post by Keen101 on 2008-11-18
[http://www.justlinux.com/forum/archive/index.php/t-5842.html](http://www.justlinux.com/forum/archive/index.php/t-5842.html)

---

### Post by Bölvaður on 2008-11-18
you should also read upon "ls" which is the original "dir".


```
ls --help
```
and then try out some of those to see how it works (gives you the feel and comfort when you will need to use it in the future).

for an example you could do:

```
ls -C
```
The C makes columns and R reverses the list. (note that capital R will make ls show everything in the directory recursively, so R is not same as r)


Then we can feed that into the less function so you can scroll up and down as you wish. And quit by typing q
```
ls -C | less
```

---

### Post by egalvan on 2008-11-18
> **pluckypigeon said:**
> Does anyone know the equivalent of "dir /p"?

 lists the directories and files but breaks the list down in to parts. You can select the next part by pressing the Return key.

Ancient Trivia...

the 'p' option  stood for 'page'

it displayed the output by pages, and waited for an 'enter' to continue.

:)

---

### Post by tjwoosta on 2008-11-18
if you have questions about how to use a command you can always read the manual 

(the man pages will tell you all of the options and what each of them do)

so for instance, to read the manual for the ls command you would type

```
man ls
```

or to read the manual for the dir command you would type

```
man dir
```

---

### Post by amauk on 2008-11-18
```
ls | more
```should have almost identical results as DOS's dir /p

---

### Post by pluckypigeon on 2008-11-18
Thank you all for your quick responses!!

This is my favourite

> **amauk said:**
> ```
ls | more
```

---

### Post by handydan918 on 2008-11-18
> **egalvan said:**
> Ancient Trivia...

the 'p' option  stood for 'page'

it displayed the output by pages, and waited for an 'enter' to continue.

:)

That IS ancient.


Remember the "w" switch that went with "p"? It would allow you to fill  the "w"idth of the "p"age.

---

### Post by bcd87 on 2008-11-18
> **pluckypigeon said:**
> Thank you all for your quick responses!!

This is my favourite

Personally I like less more than more (lol that sounds weird :P)
The reason being that less has more options and you can scroll both backwards AND forwards in stead of just forwards like with more.

---

### Post by egalvan on 2008-11-18
> **handydan918 said:**
> That IS ancient.


Remember the "w" switch that went with "p"? It would allow you to fill  the "w"idth of the "p"age.

Oops... someone as ancient as I am?:(

Uh, sorry, I mean, someone with as ancient knowledge as mine?:)

I started in personal computers in 1979.
Started in mainframes in 1969.
:popcorn:
ErnestG

---

### Post by pluckypigeon on 2008-11-18
> **handydan918 said:**
> That IS ancient.


Remember the "w" switch that went with "p"? It would allow you to fill  the "w"idth of the "p"age.

Ancient but still in use!

I wish Microsoft had kept dos

---

### Post by egalvan on 2008-11-18
> **handydan918 said:**
> 
Remember the "w" switch that went with "p"? It would allow you to fill  the "w"idth of the "p"age.

Forgot to mention that I stayed in a Holiday Inn last night.

And technically,

 "w" stood for "w"ide display

:lolflag:

Careful, we'll be banned for necromancing!
:KS

---

### Post by handydan918 on 2008-11-18
> **egalvan said:**
> Oops... someone as ancient as I am?:(

Uh, sorry, I mean, someone with as ancient knowledge as mine?:)

I started in personal computers in 1979.
Started in mainframes in 1969.
:popcorn:
ErnestG

Nah, yer still older, but the bookshelf in my childhood home had strange titles like "Cobol" and Fortran". 
And I used to have boxes of punchcards to play with.
If I had known I would live this long, I'd have taken better care of myself...

---

### Post by anewguy on 2010-04-18
egalvan - you beat me into mainframes by about 5 or 6 years.  Micro's we had back in high school, but PC's as they think of them now (what used to be called IBM compatible) since they first came out.

handydan918 - Your "childhood home" had these things - as in when you were a kid (maybe I'm missing some subtle humor here ;) )?  Is so, then you aren't as old as me - I learned COBOL and FORTRAN in college (as well as the requisite machine code and assembler) and used those on the job, and for many years all we HAD were punch cards!  We had reproducers where you could wire boards to make certain things punch certain ways, etc..  Heck, when we first got terminals I had to write a reproducer program so people could use it online to generate JCL files, etc., they normally would have done with punch cards!  I also remember the days when it still said RCA under the label on some mainframes.

The thing I miss the most from those days?  The pieces of the systems were huge (we're talking 6ft tall and as wide as they could get in a door), and always came with tons of bubble wrap around them.  Once you unloaded the things off the truck without dumping one of the heavy ones (these WERE heavy!) either over the edge or down the ramp (or in more than 1 case, luckily not the computers I worked with, trying to hoist them with a crane through an opening in a wall several stories up and having the thing slip out of the sling and fall), well, then you had this big pile of bubble wrap, and a huge smooth elevated floor in the computer room, and a roll-around office chair.  Lay the bubble wrap all over the floor and you could have "hours" of fun as long as the boss didn't catch you!

Dave ;)

---

