---
title: "Best Python IDE?"
date: 2006-01-11
forum: Programming Talk
---

### Post by j-a-p on 2006-01-11
I've recently started programming in Python and I'd like some suggestions as to which IDE to use. Currently I'm just using gEdit, but want to move on to something where I can create GUI apps without having to code the GUI.

I've come accross Eclipse, Glade and another called eric which looks good.

Also, I want to develop platform independent apps.

Please give me your input.

Cheers

---

### Post by briancurtin on 2006-01-11
in linux i only have experience with Eric as far as IDEs go, and i think it is a pretty good one and i havent felt the need to look much further so far. 

if you use windows at all, look into ActiveState python, as it is the best IDE i've used for python, period. i havent used windows myself in about 8 months, but ActiveState python is one thing ive missed because of it's quality

---

### Post by j-a-p on 2006-01-11
[quote=briancurtin]in linux i only have experience with Eric as far as IDEs go, and i think it is a pretty good one and i havent felt the need to look much further so far. 

if you use windows at all, look into ActiveState python, as it is the best IDE i've used for python, period. i havent used windows myself in about 8 months, but ActiveState python is one thing ive missed because of it's quality[/quote] 
What kind of GUI creation does eric offer - I'm looking for a kind of drag 'n ' drop job if possible?  And is it popular?

I removed all traces of windows from my home. I think Linux and open source in general is superb. That's why I'm getting into python so I can get involved. Also, when people ask you to sort out their windows machines you can tell 'em you don't have any windows software!

---

### Post by ardchoille on 2006-01-12
I use SPE and Gazpacho

---

### Post by Azriphale on 2006-01-12
I have not used any of the others here, maybe I should look into them, but a few years ago I was using Boa Contructor. It is a wxWidgets drag and drop GUI builder, written completely in python with wxWidgets.

I don't have a URL for it, so just search for boa constructor on sourceforge.net
I don't know If they are still working on it tho, I haven't done any python work for at least a year.

[Edit]
[http://sourceforge.net/project/showfiles.php?group_id=1909](http://sourceforge.net/project/showfiles.php?group_id=1909)

You'll also need wxPython

---

### Post by pranith on 2006-01-12
hi ,
     I think pida would even be great it has compatibility with gazpacho also ....
It works on top of vim .....
hope that helps

pranith

---

### Post by sapo on 2006-01-12
I like the simplicity of the idle IDE, its ugly, but i like it :)

---

### Post by kperkins on 2006-01-12
spe, for code, and, glade for gui.  Trying out gazpacho, but doesn't seem as robust as glade, too me.
DrPython, is, also, a nice code editor.

---

### Post by gord on 2006-01-13
[QUOTE=briancurtin]
if you use windows at all, look into ActiveState python, as it is the best IDE i've used for python, period. i havent used windows myself in about 8 months, but ActiveState python is one thing ive missed because of it's quality[/QUOTE]


if your refering to the uterrly gorgeous  Activestate Komodo, it has a linux version and works very well, love it to bits and is easly the best python ide, it keeps things nice and simple but allows you to do powerfull things too. all the other ide's iv tryed have just piled as many buttons that you'll never use into it as possible

---

### Post by j-a-p on 2006-01-13
Is ActiveState Komodo free?

---

### Post by briancurtin on 2006-01-13
[QUOTE=gord]if your refering to the uterrly gorgeous  Activestate Komodo, it has a linux version and works very well, love it to bits and is easly the best python ide, it keeps things nice and simple but allows you to do powerfull things too. all the other ide's iv tryed have just piled as many buttons that you'll never use into it as possible[/QUOTE]
nah im just talking about activestate python, the free one.

ive seen komodo, and it is nice, but i dont do enough python at the moment to justify paying for it right now. its $295 for professional edition, $29.95 for personal/student and i just happen to be a student. i might check out the personal/student one though.

---

### Post by UbuWu on 2006-01-14
A review of 6 python IDE's:
[http://spyced.blogspot.com/2005/09/review-of-6-python-ides.html](http://spyced.blogspot.com/2005/09/review-of-6-python-ides.html)

SPE, which is not reviewed there is also a very good choice.

---

### Post by UbuWu on 2006-01-14
Wing IDE is not free but very very good. And for open source developers: "Open source developers not deriving income from their work may obtain a free license to Wing IDE upon request."

[http://wingware.com/](http://wingware.com/)

---

### Post by Wille on 2006-01-14
Actually, the situation has turned around in the last year as far as the free python IDEs go. The PyDev plugin for Eclipse has matured quite nicely, and it's definitely one to check out. Code completion works quite satisfactorily for a dynamic language.

SPE is also quite nice, but these days I just fire up Eclipse and go most of the time. Eclipse environment is worth learning for all programmers anyway, it's the one ide that seems most likely to be here for the long haul.

As far as the GUI goes, it doesn't need to be done in the IDE. Use external program like the already suggested Glade/Gazpacho.

---

### Post by stani on 2006-01-20
Don't get SPE with the package manager, download latest version at [http://pythonide.stani.be](http://pythonide.stani.be) From release 0.8.1.e SPE will be optimized for Ubuntu, see [http://pythonide.stani.be/blog](http://pythonide.stani.be/blog). Help is welcome.

---

### Post by krypto_wizard on 2006-01-20
How about VI ?

---

### Post by Wille on 2006-01-21
[QUOTE=krypto_wizard]How about VI ?[/QUOTE]
Yeah, right.

Pythonistas actually seem to use emacs more often than VI, it seems.

As far as the "small" (hah) editors (as opposed to IDEs) go, Kate is pretty handy for Python.

---

### Post by Jessehk on 2006-01-21
I use a text-editor called cream that is based on vim. Basically, it's the vim "engine", but using the features of a normal editor tacted on if you want them (like Ctrl-C for copy, etc). 

It also has different colour schemes.

```


sudo apt-get install cream


```

[http://cream.sourceforge.net/](http://cream.sourceforge.net/)

---

### Post by stani on 2006-07-18
Read my [howto install latest wxPython & SPE (Feature rich Python IDE)]("http://www.ubuntuforums.org/showthread.php?t=218001&highlight=wxpython").

---

### Post by asimon on 2006-07-18
> **Wille said:**
> As far as the "small" (hah) editors (as opposed to IDEs) go, Kate is pretty handy for Python.
If someone wants to use Kate for Python he may want to install 'kate-plugins' which isn't installed by default. Among others it contains a python browser, which can be activated by checkmark "Kate Python Browser Plugin" under "Settings->Configure Kate...->Application->Plugins". This will add an other side pan with a Python Class Browser and a new 'python' menu where one can update the browser.

---

### Post by Azriphale on 2006-07-30
There is an IDE called pida.

It uses vim as an editor, I believe. I also heard a rumour that there were plans to support emacs as an editor, but I have been out of touch with Python for a little while, so I do not know about that.

It looked to me to be a really well created IDE. I'm installing it again now so I can have a look.

pida.berlios.de

---

### Post by Cyraxzz on 2006-07-30
Looks good, i might try it, since Python is my primary language.

---

### Post by etank on 2006-08-24
I just ran across PIDA myself today. I got it installed and it looks pretty nice. Does anyone know if it will run on windows? I like to use the same tools on both platforms where available. I know that SPE is cross-platform and I like it too.

---

### Post by saracen on 2006-10-02
@stani: what's the status on [pyxides]("http://pyxides.stani.be")?

---

### Post by SuperMau on 2008-02-28
>  Also, I want to develop platform independent apps.I would recommend Dabo:

" **Desktop applications**. That's what Dabo does... and if you want to create applications that run on Windows, OS X or Linux, Dabo is for you!"

[COLOR=DarkSlateBlue][http://dabodev.com/](http://dabodev.com/)[/COLOR]

Cheers
SuperMau

---

