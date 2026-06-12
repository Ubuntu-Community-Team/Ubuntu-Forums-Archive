---
title: "IDE for lisp?"
date: 2008-07-27
forum: Programming Talk
---

### Post by emobrad on 2008-07-27
Is there an IDE for lisp? I've been looking and everything tells me to use Emacs, so I figured that the forums would be the best place to ask.

Thanks

---

### Post by squaregoldfish on 2008-07-27
There may well be an add-on for the Eclipse IDE for Lisp programming.

Steve.

---

### Post by skeeterbug on 2008-07-27
Lisp in a box works pretty well.
[http://common-lisp.net/project/lispbox/](http://common-lisp.net/project/lispbox/)

---

### Post by Kadrus on 2008-07-27
You can use Emacs with Lisp,VIM with Lisp,and I think Eclipse has a plugin for Lisp as well.
I ran across this the other day: [ABLE]("http://phil.nullable.eu/")(A Basic Lisp Editor)
[Eclipse-LispCusp]("http://www.ibm.com/developerworks/library/os-eclipse-lispcusp/index.html")
And this will help you more.
[Lisp Development tools]("http://www.cliki.net/development")

---

### Post by emobrad on 2008-07-27
Thanks guys, I'll definatly try some of those out.

---

### Post by Kadrus on 2008-07-27
> Thanks guys, I'll definatly try some of those out.
No Problem,you can add also Lisp Syntax Highlighting to Gedit
you just need to create 2 files saving them as :lisp.lang in **/usr/share/gtksourceview-2.0/language-specs/**
and in :** /usr/share/gtksourceview-1.0/langauge-specs/**
and another one saving it as x-lisp.xml in :**/usr/share/mime/text/**
In the lisp.lang files you just need to add all the keywords that you want to be highlighted.
```
gksudo gedit /usr/share/gtksourceview-2.0/language-specs/scheme.lang
```
```
gksudo gedit /usr/share/gtksourceview-1.0/language-specs/scheme.lang
```
```
gksudo gedit /usr/share/mime/text/x-scheme.xml
```
Look at those three files and do similar with the Lisp ones.

---

### Post by emobrad on 2008-07-27
Thanks man. It helps a lot.

Edit: Is there any way to get Geany to run Lisp? I've been quite used to that with C++ and I'd like to keep using it for Lisp. It does the highlighting, just never ran the programs. Is there any way to do that?

---

### Post by Kadrus on 2008-07-27
Don't mention it.
I have never used Geany,but i think there is a terminal inside of it..no?
So let's say you've written a program in Lisp,and you have maybe clisp installed or cmucl,or gcl doesnt' matter.
In that terminal I think you can try:
clisp 
and compiling your programs from there.
```
(compile-file "/pathtofile.lisp")
```
```
(load "/pathtofile.lisp")
```

---

### Post by Alasdair on 2008-07-27
The best lisp development environment is Emacs + [SLIME]("http://common-lisp.net/project/slime/"), nothing else really compares. It's got a bit of a learning curve but it's definitely worth learning if you are serious about lisp. If you really don't want to use emacs, make sure you use an editor that can automatically indent lisp code correctly. You will drown in the sea of parenthesis if your editor doesn't do that.:KS

---

### Post by Kadrus on 2008-07-27
I've never used an IDE for lisp and never had any problem with the code.I only added syntax highlighting to Gedit and ran everything from Terminal.And most of my work with Common Lisp is web development.

---

### Post by Alasdair on 2008-07-27
Lisp isn't really supposed to be used from a terminal, afaik CLISP is the only open-source lisp implementation that has decent readline support, and even then it's not exactly nice. SLIME will give you a much nicer repl and it will also provide a much nicer interface for using the debugger. However the real reason you want to use emacs for lisp over any other editor is that rather than treating your code as purely words and characters, only allowing you to move up and down lines, forward and backwards across words, emacs understands the tree-like structure of your code and provides commands to edit it as such - you can kill s-expressions, move down into nested expressions and cycle through their arguments (for example). This allows emacs to indent your code to the correct level whenever you press tab, so you don't have to indent it manually, it just makes the editing experience so much smoother, improving your productivity.

Cusp gives you most of these features for Eclipse if you want to use IDE rather than an editor - but there are editors and then there are ***editors***, gedit being in the former category and emacs in the latter. Plus you can put your lisp knowledge to good use considering emacs is largely implemented in elisp.

---

### Post by jase21 on 2009-08-12
Eclipse + Cusp plugin

---

### Post by sujoy on 2009-08-13
emacs+slime

even if you wont touch emacs for anything else, if you are doing Lisp, atleast try it out for once. nothing comes even close to a comparison

---

### Post by frodon on 2009-08-13
Unnecessary necromancing

Thread closed

---

