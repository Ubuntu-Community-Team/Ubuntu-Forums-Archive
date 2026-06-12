---
title: "Python Dev Tools"
date: 2010-07-29
forum: Programming Talk
---

### Post by masque7 on 2010-07-29
At the moment, I'm using a text editor: VIM, or gedit if I'm lazy. I have a terminal in the directory my script is and run it. This seems quite broken, doesn't it? I probably want to be able to run my scripts in the program I used to create them... 

A lot of beginners to Python seem to be fairly happy with the* IDLE* program that comes with I believe Windows and MacOS installations of Python?

Would I see any benefits in using something like IDLE? I don't feel like using a full-bown IDE yet as I do not have amount of code to deal with, and that would be something else to learn (hey, VIM is a learning curve as it is).

One of my gripes with IDLE is that is doesn't seem to support colour schemes. I cannot stand starting at code with a stark white background! 

With some scripts I'm getting >50 lines of code, so I'm looking into external functions and modules so I'm not dealing with huge chunks of code in one place. 

Any suggestions are welcome. The sort of programs I am writing are  fairly basic: a MUD game, a space invaders type game using PyGame,  converting bytes to kb, messing about with the Twitter API, a flashcard  app, and basic practise such as while and for loops, functions, etc. :popcorn:

---

### Post by Bachstelze on 2010-07-29
You could try Emacs.  I had to use it in class, its Python mode is decent.

---

### Post by era86 on 2010-07-29
Gedit can be made into a powerful IDE for python.  It has a built in terminal and file browser (much like an Eclipse mimic).  But I would read this tutorial to get started:
[http://showmedo.com/videotutorials/video?name=3130000&fromSeriesID=313](http://showmedo.com/videotutorials/video?name=3130000&fromSeriesID=313)

---

### Post by Simian Man on 2010-07-29
> **masque7 said:**
> A lot of beginners to Python seem to be fairly happy with the* IDLE* program that comes with I believe Windows and MacOS installations of Python?

One of my gripes with IDLE is that is doesn't seem to support colour schemes. I cannot stand starting at code with a stark white background!

IDLE actually does work on Linux, and it does support color themes, not sure where you got those ideas.  I still wouldn't use it though because of the ugly and uncomfortable TK interface.

I haven't worked on any Python project so big where vim + terminal felt limiting, but if I did, I would try [PyDev]("http://pydev.org/") which looks very good.

---

### Post by masque7 on 2010-07-29
> **era86 said:**
> Gedit can be made into a powerful IDE for python.  It has a built in terminal and file browser (much like an Eclipse mimic).  But I would read this tutorial to get started:
[http://showmedo.com/videotutorials/video?name=3130000&fromSeriesID=313](http://showmedo.com/videotutorials/video?name=3130000&fromSeriesID=313)
Yeah, good video but very slow. Also, a lot of those don't work in the 10.04 version of gedit such as "New From Template"

I normally find myself quickly changing things, so I don't always like grabbing the mouse and such.

I guess the real answer is to improve my vim skills, don't cram all the code into one file.

---

### Post by pixel_pusher on 2010-07-29
Geany always makes me happy....[http://geany.org/](http://geany.org/)  Or, in the repos.

You can run a python script using F5 right out of the box, usually. You might want to change the default term from Xterm though. It also has a plugin for embedding a terminal. 

There are links to a number of dark syntax themes on the "extras" section of the .org. The kinda lame part is that adjusting the highlighting is done with config files... no dialog except for a color chooser.

Oh, almost forgot, the thing that first hooked me on geany: A very good symbol browser. Pretty handy as your python scripts get bigger.

---

### Post by wmcbrine on 2010-07-29
> **masque7 said:**
> This seems quite broken, doesn't it?Nope, not to me. I have no patience for IDEs.

---

### Post by pixel_pusher on 2010-07-30
> Nope, not to me. I have no patience for IDEs.Indeed, especially python IDEs, I've never found one that didn't **** me off completely. 

I got big into  pygame for awhile, and it seemed like going for an IDE would help keep things organized. Ended up spending more time trying to get the environments configured right than I did coding.....

I think that if you really want an IDE for python, the best bet is to go for the ones that are really just text editors + a few extras. Geany being my favorite, and SPE would be great if it was still being developed.

In case the OP is still interested, here are the some of the better ones I've tried along with my experiences w/ them:
**Eric 4**:
     ++ pretty QT interface, version control access from within the IDE, unit testing, project mgmt, if you end up working with pyqt eric is great, as it works very well with QT designer
      -- buggy, the error parsing tended to lock up the whole program for minutes at a time, and it would sometimes just crash for no apparent reason. It wanted to run everything through an embedded terminal, which I found annoying, esp. when working w/ gui code or pygame

**Stani's Python Editor**:
     ++ pretty stable, wxGlade is built in, my favorite part about SPE is it will generate docs for your  code (using PyDoc, i believe) and/or make UML diagrams. Not really an IDE per se, just an editor w/ some neat features.
     ** --** i think stani dropped any work on this years ago..., the version you get from the ubuntu repos   still relies on python 2.4 (IIRC) and an older version of wxPython. and no way to edit color themes.

**Eclipse + Aptana PyDev plugin**:
     **++** probably the most successful implementation of a python IDE I've tried,  most of the things that make an IDE desirable are here. (code completion, error-checking, project mgmt, testing, etc)
      **--** You have to use Eclipse and all the overhead that comes with it, just to have a python ide...

***there's also a Netbeans plugin for python.... pretty much the same situation as w/ eclipse.

**Komodo Edit:** 
    ++ Another "not just an editor, not quite an ide".... this one's got code completion, works for many different languages,  you can run your scripts from the editor ( w/ an embedded term by default) 

   -- Takes forever and some change to start up. No symbol browser. Technically, this is like a trial version of the Komodo IDE, which you'll have to pay for, but you can use K. Edit indefinitely.


and there's of course others, listed here: 
[http://wiki.python.org/moin/IntegratedDevelopmentEnvironments](http://wiki.python.org/moin/IntegratedDevelopmentEnvironments)

---

### Post by tfultz33 on 2010-08-14
I recently downloaded Boa Constructor. It does want I want but with wayyy too many steps. Does anyone know of a simpler program with the same functionality? I  am looking for a clone of Visual Basic, except for Python. Pick a window, add a button right click the button view source type the code. That is exactly what I'm looking for. 

Boa has way too many panels and steps. Pretty buggy too.

Visual Python is what Im looking for but somehow I think if someone made a visual python it wouldnt be what I want. lol Unless it was a Visual Basic clone.

---

### Post by masque7 on 2010-08-14
Taking it you mean Visual Studio? 

It depends entirely on what toolkit you're using. If it's GTK, you could try GLADE.

---

### Post by tfultz33 on 2010-08-14
I have glade. you cant insert event code. Thanks though. I am looking for visual basic but visual python. Design and code all in one.

---

### Post by tfultz33 on 2010-08-14
Drag and drop. all that windows stuff. Why code the interface when you can drag and drop it and write the event code.?

---

### Post by ssam on 2010-08-14
you can create keybaord shortcuts in VIM. in my .vimrc i have

```

autocmd FileType python map <F5> :call ExecPyFile() <CR>

func! ExecPyFile()
exec "w"
exec "!./%"
endfunc

```

i also find it handy to install the nautilus-open-terminal packages, so that i can open a terminal from nautilus. and use the alias

```

alias o='xdg-open '

```

so that i can do
```

o .

```
to open the current directory in nautilus.

---

### Post by tfultz33 on 2010-08-14
Has anyone even used visual basic? 
Do you know what it is like? 
You would think there would be VB clones a dime a dozen for python.
I wouldnt type my name in vim. That thing is primitive as cuniform.

---

### Post by eveningsky339 on 2010-08-14
I alternate between IDLE and gedit/terminal with Python.  The only IDE I'm happy with is Code::Blocks, which isn't for Python in the least.

I gave Emacs a go because it seemed like everyone was singing its praises, but I found it quite useless.  Counter-intuitive and clunky if you ask me.  Though I hear you can play tetris...

---

### Post by tfultz33 on 2010-08-15
I just downloaded monodevelop and it looks decent, but the gui designer doesn't even work with vb. LOL so im sure it wont work with python either if i ever figure out how to add python to monodevelop. It isnt in the addins repository, but they said it works with python. Man, developers just think people should automatically just know where **** is I guess.

---

