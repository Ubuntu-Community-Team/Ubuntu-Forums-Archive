---
title: "?Python setup? !Help a newbie! (new to Ubuntu)"
date: 2010-03-18
forum: Programming Talk
---

### Post by pooke on 2010-03-18
Hi,

I'd just like to introduce myself.
My name is Alex and I'm 16 (soon to be 17) years old.
I discovered Ubuntu mainly because of my school course "Personal Computer".

I am a total newbie when it comes to this new system for me, Ubuntu. 
I have been using Windows for all these years - until now.

----------

What I'm looking for to know is this;

I would like to have the latest version of **PYTHON** and **all essential, useful python libraries (compilers too) to work with**.

I don't need an IDE yet (or should I? If so, recommend one). I most likely will start off with IDLE.

I don't know how the package system goes, I don't know how the terminal (command prompt?) works - I know nothing about Ubuntu.

---------

Help me, please!

---

### Post by mickie.kext on 2010-03-18
Hello,

You could start learning Python from this site - [http://wiki.python.org/moin/BeginnersGuide](http://wiki.python.org/moin/BeginnersGuide)

It has tutorials for everyone. But I think that best book for a newbie is 'Byte of Python' and you can download it from that site in PDF format. 

I recomend you to start learning Python3 directly because 2.6 is alerady on its way out. 

So you just need to fetch python3 and idle3 packeges from repositories, and you are good to go.

---

### Post by blur xc on 2010-03-18
Read [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

For python- 
```
sudo aptitude install python2.6
```
Python 2.6 isn't the latest, but from all I've read, it's still the best.  Python 3 isn't quite ready for the masses..

[http://www.swaroopch.com/notes/Python](http://www.swaroopch.com/notes/Python)
[http://diveintopython.org/](http://diveintopython.org/)
[http://inventwithpython.com/](http://inventwithpython.com/)

[http://www.swaroopch.com/notes/Vim](http://www.swaroopch.com/notes/Vim)

[http://www.google.com/search?q=vim+as+a+python+ide&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=vim+as+a+python+ide&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

But you can write python programs in gedit as well if you aren't ready for a real text editor (sorry)...  Gedit has a mode for writing python programs...

BM

---

### Post by oldfred on 2010-03-18
If you do install python 3 do not uninstall python 2.6 as just about the entire Ubuntu system runs on 2.6. You just about have to reinstall to recover from deleting python2.6.

I am learning python also and have found geany (from synaptic) a good editor with some settings set for python - like use spaces for tabs. With geany I can copy and paste someone's code, save as a .py so it knows its python, and execute from within geany with errors shown.

You will get many recommendations and one nice thing about linux is many programs are free so you can try them without having to make a major investment.

---

### Post by blur xc on 2010-03-18
> **oldfred said:**
> I am learning python also and have found geany (from synaptic) a good editor with some settings set for python - like use spaces for tabs. With geany I can copy and paste someone's code, save as a .py so it knows its python, and execute from within geany with errors shown.

Just an FYI- with some addons and some configuring (from easy online tutorials) you can make VIM do all those same things.  Syntax highlighting, executing code (shift E), hide and show blocks of code, have tab insert 4 spaces and not tab characters, etc...

BM

---

### Post by pooke on 2010-03-18
Thanks for all replies. 

So to start off I basically get the python packages off Synaptic (idle3,python3)?
Anything done in terminal I should know about?

And Vim sounds interesting.

What would I have to do to begin doing python in Vim? Packages, terminal commands e.t.c.

---

### Post by blur xc on 2010-03-18
> **pooke said:**
> Thanks for all replies. 

So to start off I basically get the python packages off Synaptic (idle3,python3)?
Anything done in terminal I should know about?

Do me a favor- go to the terminal (applications -> accessories -> terminal) and enter python and hit enter.

Chances are you will drop into an interactive python environment.  From there you can enter python commands.  If you write a program in any text editor, and start out the first line with "#!/user/bin/env python", and then give the program excutable permssions "chmod u+x filename.py", and run it with "./filename.py", it should execute.

You don't need to do much to start programming in python- but you do need (imo) to get a basic understading of Linux and the command line.  If you are doing any programming, you will be spending a fair amount of time at the command prompt.  Also, don't install python 3.  You don't need it.  Just keep programming in 2.6.

BM

---

### Post by pooke on 2010-03-19
Hi, thanks for your answer.

I would also like some answers on my question regarding Vim and its Python packages, how to set up a Vim Python environment and start.

---

### Post by blur xc on 2010-03-19
> **pooke said:**
> Hi, thanks for your answer.

I would also like some answers on my question regarding Vim and its Python packages, how to set up a Vim Python environment and start.

Follow these instructions- [http://dancingpenguinsoflight.com/2009/02/python-and-vim-make-your-own-ide/](http://dancingpenguinsoflight.com/2009/02/python-and-vim-make-your-own-ide/)

I'm sure there's more, that's just the one that I used.

BM

---

### Post by pooke on 2010-03-19
Hi!

Thank you. :)

---

