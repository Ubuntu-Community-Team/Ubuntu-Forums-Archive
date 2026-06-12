---
title: "text editors"
date: 2009-01-18
forum: Programming Talk
---

### Post by octopusfinley on 2009-01-18
Hey there all,
I'm just starting out, trying to learn C++. I'm wondering if anyone can recommend a good text editor. So far I've just been using nano but I feel like this isn't really the place for a program and I also can't find any way to copy my programs. Any suggestions?
Thanks,
finley

---

### Post by cmay on 2009-01-18
all iever use is geany. or codeblocks which i think could be the c++ editor you may want. kdevelop is nice too. but i run light desktop enviroment so i stick with geany. i use nano for editing the files in the system however. like apt sources. but i know it can be madse to syntaxt higlightning. vim or vi for console based programming editors is very popular. i would as said use geany. or gedit on ubuntu.

---

### Post by DocForbin on 2009-01-18
Haven't used it for C++, but I really like Geany as well. It's lightweight/fast, and a nice balance between a juggernaut IDE and a simple editor.

For programming text editors, vi/vim and emacs are popular and powerful, but have a bit of learning curve. There are lots of threads on this topic, and tons of options. Search and try a few out.

For a full-fledged IDE, netbeans and eclipse and both nice, and free :) NetBeans 6.5 is really slick.

---

### Post by jimi_hendrix on 2009-01-18
vim (gvim for the faint-hearted)

---

### Post by octopusfinley on 2009-01-18
Wow thanks everyone, I didn't expect such a good response. I'll definitely check out these suggestions. I really appreciate it.

---

### Post by Joeb454 on 2009-01-18
I use Vim for small text file editing, or for coding on remote computers.

Other than that I have to give my +1 to Geany :D

---

### Post by module0000 on 2009-01-18
VIM is great if you can get the keyboard shortcuts to second nature(and remember to give it ":syntax on" for highlighting).

If I'm not using VIM, I'll use geany in X, and if you have enough resources, Code::Blocks is really incredible(code completion, object browsing, etc).

---

### Post by cardinals_fan on 2009-01-18
Vim is the best editor.  If you need the functions of a full-scale IDE, Geany is very good.

---

### Post by Joeb454 on 2009-01-18
> **module0000 said:**
> VIM is great if you can get the keyboard shortcuts to second nature(and remember to give it ":syntax on" for highlighting).

I thought that's what ~/.vimrc is for? :p

And I've also used NetBeans, it's not that bad really...especially as it works across On Linux, OS X, Windows & Solaris...pretty much guarantee's an identical environment whatever OS you're working on

---

### Post by jimi_hendrix on 2009-01-18
> **module0000 said:**
> VIM is great if you can get the keyboard shortcuts to second nature(and remember to give it ":syntax on" for highlighting).


just:

```
echo :syn on > ~/.vimrc
```

---

### Post by snova on 2009-01-18
> **octopusfinley said:**
> So far I've just been using nano but I feel like this isn't really the place for a program and I also can't find any way to copy my programs.

What do you mean, "copy my program"?

> **jimi_hendrix said:**
> just:

```
echo :syn on > ~/.vimrc
```

Assuming you don't have a .vimrc already... in which case, append:

```
echo :syn on >> ~/.vimrc
```

---

### Post by HotCupOfJava on 2009-01-18
I've used vim a bit myself, but then I decided to code my own text editor for some extra features: automatically placing closing parenthesis, brackets, and quotes. Smaller tab indents (the default takes up too much line space). Line number display (for debugging). JFileChooser so I can "hunt" for my source code when I can't remember which directory I saved it in. 

You get the idea. I could just use NetBeans or something, but my editor is a good bit faster for just straight source typing.

---

### Post by kerry_s on 2009-01-18
what no one likes nedit anymore? :)

---

### Post by Sorivenul on 2009-01-18
My vote is split between Geany and Vim.

---

### Post by module0000 on 2009-01-18
> **Joeb454 said:**
> I thought that's what ~/.vimrc is for? :p

And I've also used NetBeans, it's not that bad really...especially as it works across On Linux, OS X, Windows & Solaris...pretty much guarantee's an identical environment whatever OS you're working on

I wrote that so that the original poster would know how to turn it on to try out VIM, didn't want him to "vi foo.c" and see white on black and think that's all vim was =)

---

### Post by PandaGoat on 2009-01-19
I do not want to start an editor war, but I recommend emacs.  For an editor--IGNORING VIM SINCE I DO NOT LIKE IT FOR PERSONAL REASONS--emacs is superior once you climb the learning curve.

At first glance, it may seem like the keyboard macros are random, but they are not. All macros beginning with C-x have a common trait.  Something beginning with C usually has a complement beginning with M, such as cutting text apposed to just copying.  I would read [http://www.gnu.org/software/emacs/tour/](http://www.gnu.org/software/emacs/tour/) to get a basic understanding of what I even mean by C-x, C, and M and get some ideas of what emacs does.

Of course though, try every editor suggested that you desire until you are bored.  Repeat this process, filtering out what you like to use. Then, pick which won the battle.

---

### Post by hessiess on 2009-01-19
Defanatly Vim;)

---

### Post by NinjaWork on 2009-01-19
I miss Textpad! Can someone please clone it on Linux for me?

---

### Post by jimi_hendrix on 2009-01-19
> **HotCupOfJava said:**
> I've used vim a bit myself, but then I decided to code my own text editor for some extra features: automatically placing closing parenthesis, brackets, and quotes. Smaller tab indents (the default takes up too much line space). 

all doable in vim

---

### Post by mali2297 on 2009-01-19
I use [JED](http://www.jedsoft.org/jed/). It has much of the same features as Emacs but is far lighter.

---

### Post by brunovecchi on 2009-01-19
My vote goes to vim too.

---

### Post by wmcbrine on 2009-01-20
I still use nano. This is partly due to my extreme inertia (pico was my first Unix editor, circa 1993), and partly due to my ruling out anything GUI, which narrows down the choices a lot. (I want to be able to work from the shell.) I do use vim sometimes, but I'm not its master. I've never undertaken the considerable effort required to learn to use emacs even casually, but I admire it from a safe distance. :D

---

