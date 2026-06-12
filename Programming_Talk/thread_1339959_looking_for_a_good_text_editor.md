---
title: "looking for a good text editor"
date: 2009-11-28
forum: Programming Talk
---

### Post by s0c0 on 2009-11-28
In the windows world I would use NotePad++ so I am looking for something with similar functionality.  The big thing I am looking for in my text editor is syntax highlighting, especially SQL syntax.

---

### Post by Virtual Liberty on 2009-11-28
Have you tried Gedit and jEdit ?

---

### Post by SNYP40A1 on 2009-11-28
> **s0c0 said:**
> In the windows world I would use NotePad++ so I am looking for something with similar functionality.  The big thing I am looking for in my text editor is syntax highlighting, especially SQL syntax.

Yeah, Notepad++ is really good.  Wish there was a Linux version.  You could probably run it in Wine.

---

### Post by jzacsh on 2009-11-28
> **SNYP40A1 said:**
> Yeah, Notepad++ is really good.  Wish there was a Linux version.  You could probably run it in Wine.

Run it in Wine?... I thought Notepad++ was open sourced..?

---

### Post by ibuclaw on 2009-11-28
> **jzacsh said:**
> Run it in Wine?... I thought Notepad++ was open sourced..?

Open Source != Will Run on Linux.

Notepad++ uses a set of functions/routines that are Windows API specific.
That's not to say that it can't be ported over - you just need to rewrite a large chunk of it so that you get the same interface except in GTK or QT.

---

### Post by jzacsh on 2009-11-28
> **tinivole said:**
> Open Source != Will Run on Linux.

Notepad++ uses a set of functions/routines that are Windows API specific.
That's not to say that it can't be ported over - you just need to rewrite a large chunk of it so that you get the same interface except in GTK or QT.

Yes, I was considering it, but... just allowing the whole GUI side of the programming to slip by my thoughts. Quite important though :)

_sorry, a bit off topic_: does the interface really make up **so much** of the code (*I haven't learned to write anything outside of the command line yet*) that its a big deal to port??

**back to answer your question:**
I dont' know about SQL syntax, but you can try Bluefish. I mostly use vim. it has a learning curve, but if you spend a lot of time with text files, you might feel its worth it. It also has syntax highlighting (*and a ton of other countless whistles*).

---

### Post by leandromartinez98 on 2009-11-28
xemacs, gvim, nedit?

---

### Post by qalimas on 2009-11-28
Depends on your DE.

KDE's KATE is a great text editor included in the KDE suite.

---

### Post by s0c0 on 2009-11-28
gEdit did not provide syntax highlight (at least not that I could tell).  There was a simple editor I used to program in years back and I believe it was kde specific back when I was on debian+kde.  I am downloading kate now, hopefully thats what I am thinking of.  If that doesn't do it for me I'll look into jedit, thanks.

---

### Post by falconindy on 2009-11-28
I just recently got rid of Gedit and Geany. I'm 100% Vim. Do a little bit of research. Among other things, Vim will do:

-syntax highlighting
-flawless column select
-search/replace with pattern matching
-macros
-word completion
-multiple documents, tabbed or tiled (they're called buffers)
-built in compiling tools
-text manipulation (e.g. changing case, transposing lines)

Yes, the learning curve is vertical, but its been worth sticking with it. I keep my trusty Vim cheat sheet nearby.

---

### Post by maximinus_uk on 2009-11-29
Your question is a bit like asking a sample of sports fans who the best team is.

However, it can be replied in a simple way: there a great number of text editors, and they differ in only a few simple ways, and probably whatever is on your system - GEdit, Kate or whatever - will do what you want.

If, on the other hand, you are going to use a text editor on a regular basis, then you should learn either VIM or EMACS. You'll probably hate both at first but it's the truth. Try both and see how you get on :p

---

### Post by Barriehie on 2009-11-29
> **maximinus_uk said:**
> ...muted...
If, on the other hand, you are going to use a text editor on a regular basis, then you should learn either VIM or EMACS. You'll probably hate both at first but it's the truth. Try both and see how you get on :p

+1 My emacs cheat sheet grows weekly but I couldn't use any other at this point!

Barrie

---

### Post by hessiess on 2009-11-29
> 
If, on the other hand, you are going to use a text editor on a regular basis, then you should learn either VIM or EMACS. You'll probably hate both at first but it's the truth. Try both and see how you get on 


This, Im a Vim guy personally;)

---

### Post by sgosnell on 2009-11-29
Gedit does do syntax highlighting, for many languages/environments.  You may need to enable some plugins through the menus.

---

### Post by jpkotta on 2009-11-29
> **leandromartinez98 said:**
> xemacs, gvim, nedit?

I like nedit, as a notepad-like application.  It is not too hard to make your own syntax highlighting mode.

I use GNU Emacs.  I used to use XEmacs, but it ended up being too crashy for me.  The only things I miss are the horizontal scroll bars and the superior tab mode (but [ido]("http://www.emacswiki.org/emacs/InteractivelyDoThings") is far better than tabs anyway).  Later I came across this and it sums it up perfectly: [http://steve-yegge.blogspot.com/2008/04/xemacs-is-dead-long-live-xemacs.html](http://steve-yegge.blogspot.com/2008/04/xemacs-is-dead-long-live-xemacs.html).

---

### Post by Cavsfan on 2009-12-07
Was on a website the other day and tried to look at a xxxxx.txt file.
I double clicked on it and it said I needed to download an add-on to read it?

That kind of confused me; any one know what I should do here?
I usually use gedit as it came with Karmic. But, the web page could not use gedit.
Thanks!

---

### Post by jpmelos on 2009-12-07
GEdit does syntax highlighting out of the box. Just open a file with the correct extension or choose the correct language/environment on the lower bar.

But I totally recommend Vim.

As I use to say:

[LIST=1]
[*]Learn Linux and you are free.
[*]Learn Vim and you are free of distribution. Whatever UNIX system will suffice.
[*]Learn LaTeX and you are free of office platforms. No more Microsoft Office, OpenOffice or whatever. No more WYSIWYG. No more losing pictures, no more things moving around misteriously.
[/LIST]

That is freedom. Any computer you touch will suffice your needs.

---

