---
title: "Help with Python"
date: 2005-06-29
forum: Programming Talk
---

### Post by Zatani on 2005-06-29
hey guys,
im a new face here, just getting ubuntu for the first time and im really excited...however, i wanted to learn "useful" programing...i started programing 2 years ago on Darkbasic, a basic language designed for 3d game creation ([www.thegamecreators.com](www.thegamecreators.com) if your interested), however, this is not a very useful language...i played around in c++ a little but not serious right now and i found Python...now to my question  ;-) 

when i ran python, it was like a command line interface...ive never seen something like this in a language, im used to an IDE and a "compile" button, so im a little overwelmed by how Python works...is there an IDE i could download for it? any help would be much appreciated...

thanks in advance,
Zan

---

### Post by sapo on 2005-06-29
[QUOTE=Zatani]hey guys,
im a new face here, just getting ubuntu for the first time and im really excited...however, i wanted to learn "useful" programing...i started programing 2 years ago on Darkbasic, a basic language designed for 3d game creation ([www.thegamecreators.com](www.thegamecreators.com) if your interested), however, this is not a very useful language...i played around in c++ a little but not serious right now and i found Python...now to my question  ;-) 

when i ran python, it was like a command line interface...ive never seen something like this in a language, im used to an IDE and a "compile" button, so im a little overwelmed by how Python works...is there an IDE i could download for it? any help would be much appreciated...

thanks in advance,
Zan[/QUOTE]

[http://byteofpython.info](http://byteofpython.info)

i ve started last week with python.. start reading this book.. its a very quick reading.. ;)

---

### Post by thumper on 2005-06-29
I find KDevelop for Scripting a nifty editor for python scripts.

I use kubuntu so KDE stuff is more natural for me.  Not sure what you are using.  KDevelop has a built in konsole for testing the scripts as well.

Since python is interpreted not compiled, you won't find a compile button anywhere.

I find the best way to test stuff is interactively using the interactive python interpreter.  So you make your python file, lets say bob.py.  Start python in the same directory and import bob.  You can then call the methods in your file interactively and check that they work.

If you need more info or examples just ask.

---

### Post by sapo on 2005-06-29
[QUOTE=thumper]I find KDevelop for Scripting a nifty editor for python scripts.

I use kubuntu so KDE stuff is more natural for me.  Not sure what you are using.  KDevelop has a built in konsole for testing the scripts as well.

Since python is interpreted not compiled, you won't find a compile button anywhere.

I find the best way to test stuff is interactively using the interactive python interpreter.  So you make your python file, lets say bob.py.  Start python in the same directory and import bob.  You can then call the methods in your file interactively and check that they work.

If you need more info or examples just ask.[/QUOTE]

i think that i m the only one that program python in gedit...  ](*,)

---

### Post by thumper on 2005-06-29
[QUOTE=sapo]i think that i m the only one that program python in gedit...  ](*,)[/QUOTE]
Well, at work I use XEmacs  ;-)

---

### Post by Topper on 2005-06-29
[QUOTE=sapo]i think that i m the only one that program python in gedit...  ](*,)[/QUOTE]

I use Gedit too :roll: but in combination with iPython(great interactive interpreter, try it!).

If someone could suggest a better Gnome-editor for Python, I would be happy...

---

### Post by Zatani on 2005-06-29
hey guys thanks for the quick responses :) 

yeah that book was a great way to get started thanks for the link  :) for an IDE i got PyScripter...kinda randomly selected it, but its nice enough

i didnt know anything about python being interpreted rather than compiled, but this book explained things to me, im on the right track now 

thanks for all the help,
Zan

---

### Post by Zatani on 2005-06-29
sry to double post, but i just ran into a problem in python  ](*,) 

whenever i try to run this statement:
      number=int(raw_input("Enter a number: "))

i get an error:  EOF error while reading line...anybody got any ideas?

thanks in advance,
Zan

---

### Post by sapo on 2005-06-29
[QUOTE=Zatani]hey guys thanks for the quick responses :) 

yeah that book was a great way to get started thanks for the link  :) for an IDE i got PyScripter...kinda randomly selected it, but its nice enough

i didnt know anything about python being interpreted rather than compiled, but this book explained things to me, im on the right track now 

thanks for all the help,
Zan[/QUOTE]

after you are finished with this book.. get one called "Dive Into Python" And after that "Python Cookbook"

After these 3 books you will be good enought to make a lot of cool things with python...  :grin:

---

### Post by cwaldbieser on 2005-06-29
[QUOTE=Zatani]sry to double post, but i just ran into a problem in python  ](*,) 

whenever i try to run this statement:
      number=int(raw_input("Enter a number: "))

i get an error:  EOF error while reading line...anybody got any ideas?

thanks in advance,
Zan[/QUOTE]

It works for me.  Do you hit CTRL-D when the prompt comes up?  That could cause an EOF error...

---

### Post by crashtest on 2005-06-29
[QUOTE=Zatani]

when i ran python, it was like a command line interface...ive never seen something like this in a language, im used to an IDE and a "compile" button, so im a little overwelmed by how Python works...is there an IDE i could download for it? any help would be much appreciated...

thanks in advance,
Zan[/QUOTE]

I've been using DrPython as my IDE.  It has the advantage of working cross-platform on Linux, Windows and Mac OS X.  I'm not totally in love with it, but it works well enough for now.  I should mention another advantage - it's very simple and easy to learn.  [http://drpython.sourceforge.net/](http://drpython.sourceforge.net/)

Always on the lookout for something better however.

---

### Post by jerome bettis on 2005-06-29
that line you have up there works fine over here too.  i'm pretty new to python so i can't really help.

vim is a really nice editor to use, the more you use it, the more you learn, and it's then even better.  it's different that anything you're used to but the learning curve really isn't as steep as you would think.  take a few hours and check it out, it's worth it.

---

### Post by Topper on 2005-06-29
[QUOTE=Zatani]sry to double post, but i just ran into a problem in python  ](*,) 

whenever i try to run this statement:
      number=int(raw_input("Enter a number: "))

i get an error:  EOF error while reading line...anybody got any ideas?

thanks in advance,
Zan[/QUOTE]

Works for me too. btw, 'raw_input' is usually used to let the user input text strings, while 'input' is used to let the user input numbers. So, you could use 

number = input("Enter a number: ")

instead of what you used above.

---

### Post by Zatani on 2005-06-30
well i think i found the problem...when i went to the python promt and used it it worked fine, however the problem seems to be my IDE  :?  its the one that wont do it

im d/l the drPython now so i hope that workls better :)

thanks for the help,
Zan

---

### Post by nobodysbusiness on 2005-07-02
For my IDE, I like Eclipse with the [PyDev](http://pydev.sourceforge.net)  plugin. I learned Eclipse while programming Java at work, and it's just as good for Python. To speed up GUI development, I use wxGlade.

---

### Post by Skrewdriver on 2005-07-05
[QUOTE=sapo]after you are finished with this book.. get one called "Dive Into Python" And after that "Python Cookbook"

After these 3 books you will be good enought to make a lot of cool things with python...  :grin:[/QUOTE]

You can download the complete text of *Dive Into Python* for free (PDF/HTML) at the author's homepage [http://www.diveintopython.org](http://www.diveintopython.org)
... of course if you buy the printed book the author gets some $$ for his efforts.

---

### Post by kiddo on 2005-07-05
> i think that i m the only one that program python in gedit...  ](*,) 			 		 	 	 

Well, at work I use XEmacs  ;)

Hey, call me crazy, but I use Bluefish for python XD If I was any good at programming python, then maybe I'd be using DrPython for it's integrated IDLE. Otherwise, I mean, it's just about writing a .py file, which, at the base, is a text file, am I wrong? You can do it in leafpad, or write it on a sheet of paper as far as I know (now getting your computer to interpret your sheet of paper is something else XD)

Now if I could only get rid of that stupid lag when typing with syntax highlighting, I would not need leafpad at all (bluefish, as well as gedit and drpython are affected.. very strange)

---

