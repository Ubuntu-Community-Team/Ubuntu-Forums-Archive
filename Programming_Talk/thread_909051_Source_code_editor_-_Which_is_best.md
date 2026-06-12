---
title: "Source code editor - Which is best?"
date: 2008-09-03
forum: Programming Talk
---

### Post by JagDragon on 2008-09-03
Hey all,

I'm looking for a good source code editor to use under Ubuntu. I use Notepad++ under Windoze, and I'm looking for one under Linux that has all of the features that I need. I have already tried Bluefish editor, and didn't really like it at all, so I'm looking for alternatives. Here are the features I have found useful on Notepad++:
[list]
[*]Very clean look - not much clutter
[*]Tabbed editing
[*]Syntax highlighting for
[list]
[*]Batch scripts
[*]Python
[*]C/C++
[*]PHP
[*]HTML/XML
[*]Javascript
[/list]
[*]Regular expression searching and replacing
[*]**Very** fast and efficient
[/list]
So, what is out there, and what is good? Thanks.

---

### Post by pmlxuser on 2008-09-03
if you like notepad ++ why dont you just install wine and then you can run it even in ubuntu.
```

$sudo apt-get install wine

```
download notepad ++ 
install using wine
```

$ wine notepad++.exe (whatever)

```

have you tried vi (of course this is very advanced and only advanced programmers prefer it.) so i would advice you that if you did not like bluefish just follow the above advice you will be happy with your editor and you will be happy in Ubuntu.

---

### Post by cabalas on 2008-09-03
This can be a dangerous question ;) it's a bit like asking what colour the bike shed should be.

For stock Ubuntu gEdit is a good editor which fulfills most of what you list there and comes installed by default. I believe the only thing it is really missing is the searching via regex which chances are there is a plugin which does it.

---

### Post by JagDragon on 2008-09-03
Thanks for the replies. I have been using vim for about 5 years now, I was just wanting something graphical and native to Linux. Where could I find plugins for gEdit?

I just got onto this thing called "scite", which uses the same "engine" as Notepad++, so I'm trialling that for a while. If any of you want to try it, just get it using apt-get.

---

### Post by roelpeeters on 2008-09-03
As said by cabalas, this is a very dangerous question. With the risk of starting a never-ending editor war ;-) I'd go with emacs. It has a learning curve that is a bit steeper than your usual Windows editor, but once you get the hang of it you ask yourself, how did you ever do all this before.

Emacs can be installed with the usual installation mantra:
```

sudo apt-get install emacs

```

Some of the  features:

* progressive search
* regex search and replace
* regex alignment
* column copy and paste 
* syntax highlighting for any imaginable language
* after compiler run, jump directly to the source and line containing the error
* split windows in any direction and synchronize the cursor between them
* and best of all: you can built anything you like into the editor

Emacs also has the following integrated:
* Shell
* Calender
* Calculator
* Directory & File Management
* mail reader
* news reader
* Psychologist (no kidding!)

- Roel.

---

### Post by leg on 2008-09-03
Try gedit with some plugins or have a look a Geany.

---

### Post by hyper_ch on 2008-09-03
emacs is a good operating system, it just lacks a decent editor ;)

there's many... open synaptic and search for editor...

---

### Post by annatar on 2008-09-03
Another good choice (at least to me) is Editra, which is written in Python with the WxWidgets toolkit. 
All your requirements are fulfilled, and you can install/write plugins to extend the application. Plus it (claims to, never tried it) has 'vi keybinding support'.

One caveat is that you have to compile and install from source.

Editra's website : [http://editra.org](http://editra.org)

---

### Post by Reiger on 2008-09-03
You can also use Kate; as of yet I haven't come across any killer features which would make me say 'Kate before Gedit' both appear to me to be essentially Linux equivalents (or is it the other way around) to Notepad++ on Windows.

Then again, I use(d) Gedit and use Kate like I use Notepad++.

---

### Post by ad_267 on 2008-09-03
I second Gedit with the regex search and replace plugin ([http://live.gnome.org/Gedit/Plugins](http://live.gnome.org/Gedit/Plugins)) or Geany. They're both pretty good but you'll probably find there's one you prefer over the other.

---

### Post by SeanHodges on 2008-09-04
GVim or Cream are good options if you come from a Vim background and want the best of both worlds...

Personally I use GVim, but I've heard good things about Cream.

---

