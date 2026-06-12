---
title: "A question on IDEs."
date: 2008-12-03
forum: Programming Talk
---

### Post by davidbilla on 2008-12-03
I've been wanting to start using an IDE apart from vim. I need support for C/C++, java and python. Less importantly, I'd also like support for perl, javascript, html, and php, but not necessarily. Any ideas?

Also, I've downloaded and installed Eclipse CDT from the website. Now, how do I go about installing eclipse ide for java and python? Do I have to open separate programs (like CDT, JDT, Python IDE etc.,) for development in different languages or can I just open one 'eclipse' and start developing in whatever language I want once I install support for the other languages? It's a little confusing. Do I have to download and install eclipse ide for each programming language separately?

---

### Post by hessiess on 2008-12-03
Just stick with Vim;)

---

### Post by davidbilla on 2008-12-03
Vim is very good, I agree. I've been using it for more than a year since I started using Linux. I just want to try out different things. To start with, it would be good if I could install some stable IDE that has C/C++, Java and Python support. Got any ideas?

---

### Post by namegame on 2008-12-03
I recommend Geany.

---

### Post by Idefix82 on 2008-12-03
Personally, I really like Gedit. It has syntax highlighting for all the languages you need and lots of useful plugins, like a class browser, bracket matching, it's fully scriptable with python and bash and offers more goodies.

---

### Post by davidbilla on 2008-12-03
Yeah, just now installed it. Will try it out. About eclipse... I've installed CDT. What should I do if I want Java and Python support? There seem to be too many downloads. The Netbeans website seems to be clearer, it has a package called 'All' which supports all three languages I want. But eclipse has three or four versions for Java and I couldn't find Python IDE in a superficial search. There doesn't seem to be any straightforward links. Is it one of the 'projects' in eclipse? Will I have to open a seperate IDE window for each of the languages that I install eclipse IDE for?

gedit is good too, but somehow gvim seems to be a better option than gedit. You can choose one of the in-built themes that go pleasant on the eye and it too provides bracket matching. Any particular advantage of gedit over gvim?

---

### Post by Idefix82 on 2008-12-03
> **namegame said:**
> I recommend Geany.

One question about Geany: how easy is it to add custom syntax highlighting, tooltips and code folding rules for a new language?

---

### Post by namegame on 2008-12-03
> **Idefix82 said:**
> One question about Geany: how easy is it to add custom syntax highlighting, tooltips and code folding rules for a new language?

Honestly, I don't know as I've never had to add anything to it. Every language I used is covered. For me, Geany is the complete package.

It offers support for the following languages:

ASM 
C 
C# 
C++ 
CAML 
Conf 
CSS 
D 
Diff 
Docbook 
F77 
Ferite 
Fortran 
FreeBasic 
GLSL 
Haskell 
Haxe 
HTML 
Java 
Javascript 
LaTeX 
Lua 
Make 
None 
O-Matrix 
Pascal 
Perl 
PHP 
Po 
Python 
R 
reStructuredText 
Ruby 
Sh 
SQL 
Tcl 
VHDL 
XML

---

### Post by Idefix82 on 2008-12-03
> **davidbilla said:**
> 
gedit is good too, but somehow gvim seems to be a better option than gedit. You can choose one of the in-built themes that go pleasant on the eye and it too provides bracket matching. Any particular advantage of gedit over gvim?

I haven't worked with gvim so can't compare.
One reason gedit perfectly fits my bill (except that it doesn't have code folding) is that I am working a lot with a number theory/algebra language called magma, which I can't expect to be provided for in any editor. So I created my own syntax highlighting rules, I set up macros using the external tools plugin, which start magma and load my file in it with one short cut key, macros which backup my entire working directory with one short cut key, I defined a theme myself, which perfectly fits my dark Ubuntu theme, so I now have an editor which perfectly caters for a language of which it had never heard before.

I also use Latex a lot and for that gedit has an amazing plugin.

If you are a web developer, then gedit offers many nice features like working via ftp or ssh directly on your web server, lots of useful plugins like browser preview, a tag list in the left side pane and so on. Have a look at this guide on how to turn gedit in a web developer's dream: [http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html]("http://www.micahcarrick.com/09-29-2007/gedit-html-editor.html")

---

### Post by Sydius on 2008-12-03
I use gVim with a carefully-crafted .vimrc that includes a lot of macros for things like compiling if it's a C++ program or running it through lint if it is a PHP one.  Combined with sshfs for working remotely, it does everything I need, and I like the clicky tabs (regular vim has tabs too, but I find it hard to use them without a mouse).  I use code folding, auto-tabbing, bracket matching, etc.

---

### Post by tinny on 2008-12-03
Have a play with Netbeans ([http://www.netbeans.org/](http://www.netbeans.org/)) it supports Java, C/C++, Python, Groovy, PHP and Ruby out of the box.

Eclipse has a plugin for Python called Pydev [http://pydev.sourceforge.net/](http://pydev.sourceforge.net/)

---

### Post by jimi_hendrix on 2008-12-03
gvim + terminal = your friend

---

### Post by indecisive on 2008-12-13
Use Kate.  It has EVERYTHING.

---

### Post by mssever on 2008-12-14
> **Sydius said:**
>  I like the clicky tabs (regular vim has tabs too, but I find it hard to use them without a mouse).
Who says you can't use a mouse in regular vim? ```
:set mouse=a
```and click away.

---

