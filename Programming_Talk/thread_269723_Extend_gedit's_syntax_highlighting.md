---
title: "Extend gedit's syntax highlighting"
date: 2006-10-02
forum: Programming Talk
---

### Post by punkinside on 2006-10-02
Hey gang,

anybody know how to incorporate new syntax highlighting in gedit like its possible in ConTeXT?

I cant remember exactly the proyect I needed this for as I had to make do in the little time I had without syntax highlighting. But say I wanted to write something in some obscure language and wanted to "add" syntax highlighting for it in gedit. Does anybody know how to do this?

---

### Post by colo on 2006-10-02
I'm sorry I do not really contribute to an answer for that specific question, but I still want to stress that no serious programmer uses gedit, anyway. There's [x]emacs and [g]vim, and at least for the latter it's perfectly documented how to write syntax definition files.

---

### Post by punkinside on 2006-10-02
I'm a serious java programmer and for that I use eclipse but I dont feel like learning 6,02x10^28 shortcuts to be able to use vi(m) for a simple sudoku-solution generator project in prolog. I was just curious.

---

### Post by DirtDawg on 2006-10-02
Sorry, but I too am not contributing directly to the asked question.

But I would like to point out [Cream]("http://cream.sourceforge.net/") has ConTeXT highlighting built in. It's in the repos.

---

### Post by KoRnholio on 2006-10-02
I believe the answer is 'no'. I'm not 100% sure of this, however.

I think that'd be something worth requesting on their site - [http://www.gnome.org/projects/gedit/](http://www.gnome.org/projects/gedit/)

---

### Post by Wolki on 2006-10-03
gedit uses the gtksourceview widget for text display, including syntax highlighting. See [http://gtksourceview.sourceforge.net/docs.html](http://gtksourceview.sourceforge.net/docs.html)

> FAQs

   1. Language XYZ is not supported by GtkSourceView. I cannot live without it. How can I do?
      Write a XYZ.lang file describing the syntax of the XYZ language. It is a simple XML file. Look in the gtksourceview/language-specs directory for some examples.

---

### Post by DarkW0lf on 2007-05-28
The language spec on that site gives me errors when I click on the link.
This page from gnome shows the format but I think it is a confusing description.

[http://live.gnome.org/GtkSourceView/NewLangFormat?highlight=%28highlighting%29%7C%28syntax%29](http://live.gnome.org/GtkSourceView/NewLangFormat?highlight=%28highlighting%29%7C%28syntax%29)

---

### Post by engla on 2007-05-28
Produce a .lang file and install it into this hard to guess spot: ~/.gnome2/gtksourceview-1.0/language-specs/


I made [Markdown syntax files myself once..]("http://www.student.lu.se/~cif04usv/wiki/gedit.html"), use them and improve them if you want.

---

### Post by kknd on 2007-05-28
> **punkinside said:**
> I'm a serious java programmer and for that I use eclipse but I dont feel like learning 6,02x10^28 shortcuts to be able to use vi(m) for a simple sudoku-solution generator project in prolog. I was just curious.

Vim is not so hard to use. Actually, making your "environment" its like Eclipse, but without a fancy window (I like fancy windows!).

---

### Post by DarkW0lf on 2007-06-02
What is the snippet file for ?

---

### Post by firecrow8 on 2008-03-27
I'm a gedit fan. the day I can use a mouse with vim is the day i'll give it a second thought.

as for the syntax. it's configurable with a few xml files once you know how they link up.

I've outlined it here:
[http://ubuntuforums.org/showthread.php?t=736843]("http://ubuntuforums.org/showthread.php?t=736843")

it works great.

---

### Post by mssever on 2008-03-27
> **firecrow8 said:**
> the day I can use a mouse with vim is the day i'll give it a second thought.

You can use a mouse with vim. In vim, type ```
:set mouse=a
``` To make the setting permanent, put the following line in your ~/.vimrc: ```
set mouse=a
```

---

### Post by firecrow8 on 2008-03-29
Cool thanks. 

the more I get into ubuntu the more I'm liking doing things right in the comand line. I may end up using vim after all. 

and now is the part where I eat crow as they say hehehehe

---

### Post by mssever on 2008-03-29
> **firecrow8 said:**
> Cool thanks. 

the more I get into ubuntu the more I'm liking doing things right in the comand line. I may end up using vim after all.Yes, Windows users tend to think of the command line as primitive, but once you give it an honest try, you discover that it's anything but primitive. I started using Linux back in the day when I didn't have anything but the CLI. Now, I don't want to return to those days, but as a result, I can't be happy anymore on any system that doesn't have a decent CLI.

If you decide to learn vim, be sure to run through vimtutor--several times, if necessary.

> and now is the part where I eat crow as they say heheheheJudging from your nick, is this a regular occurance? :) What's the best recipe? I might need it sometime.

---

### Post by firecrow8 on 2008-03-31
hehehe. yeah it's a regular occurence but it's rare that I admit it so consider yourself privelaged. 

here's the best recipe:
leap before you look. and when someone wakes you up. thank 'em.

the anti vim comment was out of character for me actually I was more defending gedit and why someone would be attracted to it. but a week or two before that I was looking into a tui cause I was so enchanted with the terminals simplicity.

I'm totally sold on vim. spent the last two days learning it. it's soooooooooooooooooooooooooooooo awsome. i don't even need a mouse.

I've been using computer graphics for years and always noticed that the gui is very attention intensive. I've since moved into web programming and am really liking simple interfaces.

I wish I could boot up an empty X session and just launch a TUI for organizing thoughts and things. 

there's something elegant about the computer only doing what it needs to do and nothing more.

---

### Post by kmolnar on 2008-12-23
Call me crazy, but I vastly prefer gedit to text-mode editors, and as a hobbyist programming language developer (how many of those do you know?), being able to define syntax highlighting like this in my favorite editor is a real treat. =)

My current project superficially resembles Ada but is almost entirely Python-inspired. Smalltalkists beware: reserved words abound!

Okay, it's not my *favorite* editor. I prefer Eclipse for Java, SPE for Python. What can I say? I like IDEs. For markup and small tasks, however, gedit works perfectly for me.

---

### Post by t0nedef on 2009-03-03
> **firecrow8 said:**
> I wish I could boot up an empty X session and just launch a TUI for organizing thoughts and things.

sawfish is good for that, Also, mwm, or twm. There are a few others that are good. But why even load x, use twin, lol

---

### Post by shadow_code on 2009-03-03
> **colo said:**
> I'm sorry I do not really contribute to an answer for that specific question, but I still want to stress that no serious programmer uses gedit, anyway. There's [x]emacs and [g]vim, and at least for the latter it's perfectly documented how to write syntax definition files.

right...

at least half the worlds programmers are no longer serious. :roll:

---

