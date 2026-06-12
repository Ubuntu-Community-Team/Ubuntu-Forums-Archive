---
title: "what python  idle do you use under ubuntu?"
date: 2009-05-07
forum: Programming Talk
---

### Post by wsonar on 2009-05-07
the standard python IDLE seems real buggy is there a different one I should be using or what does everyone else use? 

I've installed all the python ide's and tried them out but I like the way the idle works.

I'm using 2.5 because it had more stars than 2.6 under add/remove for whatever reason

on XP i'm running 2.6 which works how it should

Did they do something different on the linux version it looks like i'm running it through wine or something, it won't let me highlight text or click  the cursor to a position and the window's are just slow moving them around the screen.

---

### Post by wsonar on 2009-05-07
has anybody else experienced this I get the same results with the standard python idle on several box's

---

### Post by days_of_ruin on 2009-05-07
[SIZE="7"][COLOR="YellowGreen"]Vim![/COLOR][/SIZE]

---

### Post by wsonar on 2009-05-07
in a terminal if I type python it use's version 2.6

but I can't open a new window like the IDLE I like to be able to test out scripts with the run command that the idle offers

---

### Post by rogeriopvl on 2009-05-07
> **wsonar said:**
> in a terminal if I type python it use's version 2.6

but I can't open a new window like the IDLE I like to be able to test out scripts with the run command that the idle offers

I would say gedit (with the oblivion theme btw) :)

You don't need the idle. just open multiple terminal windows and test the scripts with the command "python myscript.py".

If you wish to use something more advanced, try Komodo out, it even compiles your code as you write, pointing out your syntax errors.

---

### Post by wsonar on 2009-05-07
yea I like using gedit was even going to try to compile it for windows

I had been using gedit because the IDLE coloring is not good then I was opening them in the IDLE to run because I  figured that would give me the best syntax error's for troubleshooting

guess I will just use the terminal and gedit

Thanks.

---

### Post by wsonar on 2009-05-07
I don't want to sound retarded but does VIM do code coloring?

---

### Post by raptor2552 on 2009-05-07
Give Geany a try... small, fast, configurable, with syntax highlighter, and integrated terminal window.

May be found in Synaptic Package Manger

---

### Post by Can+~ on 2009-05-07
[SIZE="5"]Eclipse[/SIZE] with [SIZE="5"]pydev[/SIZE].

---

### Post by wsonar on 2009-05-07
> **raptor2552 said:**
> Give Geany a try... small, fast, configurable, with syntax highlighter, and integrated terminal window.

May be found in Synaptic Package Manger


got it installed I like it

---

### Post by Anzan on 2009-05-07
Gedit with all plugins enabled, python interpreter abd terminal tabbed in bottom pane, file browser to the left, the Oblivion theme.

---

### Post by dodle on 2009-05-07
I use drpython:
- syntax hilighting
- integreated terminal

It's my favorite of all that I've tried out.

---

### Post by CatsRninja on 2009-05-07
> **Can+~ said:**
> [SIZE=5]Eclipse[/SIZE] with [SIZE=5]pydev[/SIZE].


Didnt know Eclipse worked with python.
Its my favorite when dealing with java.

tryed geaniy(?) hated it.

I use iddle that comes standart. im guessing its the 2.6 one.
Its a big buggy yes(the bugs only appear at full MOON!!! or when i got an important assigment to deliver), but gets the job done.


I agree perfectly that gedit works fine, i just dont like to type stuff in a shell to test things when i can just press F5.Seams only a wast of time.

---

### Post by DocForbin on 2009-05-07
I use netbeans and geany.

---

### Post by Kilon on 2009-05-08
ECLIPSE with PYDEV

IDLE 2.6

IPYTHON

---

### Post by rogeriopvl on 2009-05-08
> **wsonar said:**
> I don't want to sound retarded but does VIM do code coloring?

Yes it does, just add the line:

```
syntax on
```

in your ~/.vimrc and that's it :)

---

### Post by Bodsda on 2009-05-08
[SIZE="5"][COLOR="Red"]VIM![/COLOR][/SIZE]

Set up your .vimrc like so

```

syntax enable
filetype indent on
set et
set sw=4
set smarttab
map <f2> :w\|!python %<cr>

```

The last line is probably the most useful part of my .vimrc, at allows me to run my program just by pressing F2!, tapping away in vim, esc > : > w > enter,  F2 bam!

:)

Bodsda

---

### Post by Flimm on 2009-05-08
I use [SPE](apt://spe).

---

### Post by wsonar on 2009-05-08
> **CatsRninja said:**
> Didnt know Eclipse worked with python.
Its my favorite when dealing with java.

tryed geaniy(?) hated it.

I use iddle that comes standart. im guessing its the 2.6 one.
Its a big buggy yes(the bugs only appear at full MOON!!! or when i got an important assigment to deliver), but gets the job done.


I agree perfectly that gedit works fine, i just dont like to type stuff in a shell to test things when i can just press F5.Seams only a wast of time.

yea I had been getting used to  ctrll s f5  but I hate the color's on the default idle

---

### Post by wsonar on 2009-05-08
> **Bodsda said:**
> [SIZE="5"][COLOR="Red"]VIM![/COLOR][/SIZE]

Set up your .vimrc like so

```

syntax enable
filetype indent on
set et
set sw=4
set smarttab
map <f2> :w\|!python %<cr>

```

The last line is probably the most useful part of my .vimrc, at allows me to run my program just by pressing F2!, tapping away in vim, esc > : > w > enter,  F2 bam!

:)

Bodsda

pretty interesting may have to investigate further

---

### Post by imdano on 2009-05-08
I use vim or WingIDE, depending on the size of the project I'm working on.  Vim can be a little confusing at first, wsonar, but if you stick with it and really learn how to use it you'll find it's very powerful.

---

### Post by thornmastr on 2009-05-08
**[SIZE="6"][/SIZE]**Wing Personal.A few dollars more but worth every penny.

---

### Post by Bruce Sherwood on 2009-06-19
If you like IDLE, you might want VIDLE available at vpython.org. It's a recent version of IDLE done by David Scherer that corrects many of the more serious bugs in IDLE that had accumulated over the years (Scherer started the modern IDLE in the year 2000). There is a Google Summer of Code project being done by Guilherme Polo to fix a long list of bugs in Tk and IDLE, and he expects to fold the VIDLE improvements into the official IDLE. (And while you're at vpython.org, take a look at VPython, too -- it lets you add real-time 3D animations to Python programs with remarkably little effort. This too was a creation of Scherer's in 2000.)

---

