---
title: "Text Editor+IDE"
date: 2008-02-14
forum: Programming Talk
---

### Post by Vadi on 2008-02-14
This is so not the first topic about this, but my requirements are somewhat specific.

I've been using Kate lately, got happy with it, but several things are forcing me to quit it - it can't indent unindented code (ie, select a bunch of code, press the indent button, and it gets aligned), it treats all open files way too separately - ie, if I need to search for 1 thing in all opened files, I have to switch to each file, type the text in, and search, for every single file, and lastly, doing ctrl+a in the search line selects the whole opened text, not the text in the search box. Major usability issue.

What I need is the following - regex find + backreference support (or regex find + custom macros support), *very* good integration for working with multiple text files - as in, I need to be able to search, find & replace across all files easily, indentation support - so I can completely forget about it, code, press a button, and it'll get indented. And bracket maching + selection between brackets. Also code folding.

Can anyone recommend me something please? I've been through so many linux editors now - really trying to get away from wine +  notepad++.

---

### Post by tosk on 2008-02-14
gedit might suit your needs. Give it a try. I know for sure it support indentation of multiple block of code at once as I use this feature on a regular basis. ;)

---

### Post by aks44 on 2008-02-14
KDevelop does all that. The code formatting part is quite configurable too (it goes way farther than "simple" indentation).

EDIT: not sure about "selection between brackets" but it definitely has bracket matching (highlighting).


Let's wait for vim / emacs supporters now... :p

---

### Post by Zwack on 2008-02-14
I like SciTE but it might not suit you...  It does have a Search Files option to look for multiple files containing a given string.

I'm fairly sure Emacs can do everything you want and more... but it might be too much for what you need...  (It's been about 20 years since I started using Emacs... and about 19 since I stopped).

Sorry that you're having a hard time finding just what you want.

Z.

---

### Post by Vadi on 2008-02-14
> **tosk said:**
> gedit might suit your needs. Give it a try. I know for sure it support indentation of multiple block of code at once as I use this feature on a regular basis. ;)

No regex search support.

> **aks44 said:**
> KDevelop does all that. The code formatting part is quite configurable too (it goes way farther than "simple" indentation).

Been using it for a while, yeah. But, for indentation, I need something where I take unindented text, press a button, it indents. The closest that I found that it indents as you type - which is OK until you need to do some editing and the indentation gets messed up :(

As for vim/emacs, unless someone can point me to an excellent guide on how to get started there, I'll give them a try. Best I got in emacs is to play snake in it..

---

### Post by Vadi on 2008-02-14
> **Zwack said:**
> I like SciTE but it might not suit you...  It does have a Search Files option to look for multiple files containing a given string.

I'm fairly sure Emacs can do everything you want and more... but it might be too much for what you need...  (It's been about 20 years since I started using Emacs... and about 19 since I stopped).

Sorry that you're having a hard time finding just what you want.

Z.

Notepad++ is based on the scite editor - unfortunately, it's just that. The bare scite doesn't have everything I need. :(

---

### Post by aks44 on 2008-02-14
> **Vadi said:**
> I need something where I take unindented text, press a button, it indents. The closest that I found that it indents as you type - which is OK until you need to do some editing and the indentation gets messed up :(

Looks like that plugin is not available for all languages... but for C++ projects there is definitely a menu option to reformat all your code (plus numerous configuration options to set how you *exactly* want it to be reformatted).

---

### Post by Vadi on 2008-02-14
It's a C one, so C++ indenting is fine. I'll look into it.

One more thing, I can't get the hand of kdevelop regex. I need to match this:

if (*word*) {

Where word will need to be a backreference/wildcard/however you call it. What would be the proper pattern for this?

---

### Post by scruff on 2008-02-15
Most editors allow you to select a block of text and hit TAB to increase the indent, including gedit. You use SHIFT+TAB to decrese the indent. 

As for regex search across multiple files, I use Komodo and it supports that stuff. It's not free, but it is a sweet IDE especially for Perl/Python. There is a somewhat slimmed down version of Komodo that **is** free and it may have those features built in... Check it out :)

---

### Post by Vadi on 2008-02-15
No, no, no, no. Not that kind of indenting! That kind is really horrible, poor, and crappy.

I'll check out Komodo though, thanks.

---

### Post by slavik on 2008-02-15
in case geany has not been mentioned, give it a try. :)

---

