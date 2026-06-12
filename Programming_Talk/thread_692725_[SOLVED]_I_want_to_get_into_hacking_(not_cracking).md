---
title: "[SOLVED] I want to get into hacking (not cracking)"
date: 2008-02-10
forum: Programming Talk
---

### Post by barbedsaber on 2008-02-10
[LEFT][LEFT][CENTER][LEFT]Yeah, I mean helping fix code and writing your own, not breaking peoples computers through windows many vunrabilitys.

I took a look around, and decided that I would start with learning python, it seemed like the easiest one to learn.

But I have that little choosing a text editor problem.

PLEASE DON'T MAKE THIS EMACS VS VIM

I would give a set of criteria as to what I was looking for in an editor, but I dont know what I want, so could someone please tell me the DIFFERENCE between some of them. not which is better, not which is faster, bigget smaller more good, and please not a flame war, I want to know the differences. 

thank you , [/LEFT].[/CENTER][/LEFT][/LEFT]

---

### Post by LaRoza on 2008-02-10
Text editor features that are essential:

* Syntax highlighting
* Tabs or the ability to have multiple documents open.

Features that are almost essential:

* Ability to run commands without leaving the editor
* Ability to browse directories and open files without leaving the editor.

Fortunately, Gedit (with its plugins), Kate, Vim and Emacs fulfill these.

Your choice :)

You might want to look at Geany or other IDE's also.

(Moving to programming talk, where I suggest you read the stickies.)

<edit> 
Sorry, just moved. To resume:

It is almost entirely personal preference. If you use Ubuntu, Gedit and its plugins are probably what you want. If you use KDE, Kate will be just as good.

If you don't mind installing other editors, I suggest you try Gedit (with plugins), Kate, Geany, and others to see what you like.

And Vim is better than Emacs.

</edit>

---

### Post by moshy on 2008-02-10
I think the best thing is to start with the very basic, like gedit, until the lack of a certain feature actually becomes painful to work without, and you literally outgrow the editor, then upgrade. I wouldn't start out with too many features until you genuinely need them, otherwise it's too distracting and you won't focus on the code.

---

### Post by barbedsaber on 2008-02-10
Thanks for the tip, I will try that, and its nice to see another South Aussie on the forums.

---

### Post by Majorix on 2008-02-10
> **LaRoza said:**
> It is almost entirely personal preference.
> And Vim is better than Emacs.

Aren't we contradicting ourselves a little here? :p

And I believe Gedit with plugins is perfect as a programmer's editor. Vim and Emacs were nice in their time, but back then there was no GUI ;)

---

### Post by H264 on 2008-02-10
> **Majorix said:**
> Vim and Emacs were nice in their time, but back then there was no GUI ;)

Ah, but now you can get Gvim, VIM with a GUI! Don't know if Emacs has the same thing, but it does not matter anyway because VIM is better.
Check it out

---

### Post by lnostdal on 2008-02-10
GUI? for editing text? my GUI is my keyboard and what i'm intrested in seeing at my screen is the text i'm editing not some stinking GUI .... :)

i've posted this link before, but here it is again: [http://xkcd.com/378/](http://xkcd.com/378/)

---

### Post by seventhc on 2008-02-10
@LaRoza
> 
* Ability to browse directories and open files without leaving the editor.

Fortunately, Gedit (with its plugins), Kate, Vim and Emacs fulfill these.
I wasn't aware vim had this feature, can you explain how that is enabled or a link please?
Thanks.

---

### Post by LaRoza on 2008-02-10
> **seventhc said:**
> @LaRoza

I wasn't aware vim had this feature, can you explain how that is enabled or a link please?
Thanks.

You can execute shell commands with Vim, and use Vim with a GUI. I am not good at Vim (besides what I commonly do), so I am not really up on all its features.

---

### Post by Majorix on 2008-02-10
> **lnostdal said:**
> GUI? for editing text? my GUI is my keyboard and what i'm intrested in seeing at my screen is the text i'm editing not some stinking GUI .... :)

i've posted this link before, but here it is again: [http://xkcd.com/378/](http://xkcd.com/378/)

GUI is nice, because you want to
- Click here and there with your mouse and continue hacking from that point.
- Have a terminal and other useful plugins mentioned by LaRoza attached.
- Copy&paste text with your mouse. Just imagine how hard it is to copy text using Vim.

Gvim (mentioned in a post before me) is a different story, which adds a gui to vim.

---

### Post by LaRoza on 2008-02-10
> **Majorix said:**
> GUI is nice, because you want to
- Click here and there with your mouse and continue hacking from that point.
- Have a terminal and other useful plugins mentioned by LaRoza attached.
- Copy&paste text with your mouse. Just imagine how hard it is to copy text using Vim.

Gvim (mentioned in a post before me) is a different story, which adds a gui to vim.

[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm) See subproblem 5a, Vim is a lot more efficient, one you know it.

---

### Post by Majorix on 2008-02-10
I don't want to shift off-topic, but I am posting these so not all newbies use Vim or Emacs.

The problem with that article is, why shouldn't I use the mouse? It's the whole fun in programs with GUI!

What if I don't want to delete a whole word, but a few characters, using Vim?

Above all, what if I don't want to remember dozens of keyboard shortcuts just to be able to happily code?

I don't know, but I believe a human in 21st century MUST use GUI, it wasn't invented for nothing. M$ got all those money because they produced Microsoft Mouse and then Windows, click&be done.

---

### Post by seventhc on 2008-02-10
> **Majorix said:**
> I don't want to shift off-topic, but I am posting these so not all newbies use Vim or Emacs.

The problem with that article is, why shouldn't I use the mouse? It's the whole fun in programs with GUI!

What if I don't want to delete a whole word, but a few characters, using Vim?

Above all, what if I don't want to remember dozens of keyboard shortcuts just to be able to happily code?

I don't know, but I believe a human in 21st century MUST use GUI, it wasn't invented for nothing. M$ got all those money because they produced Microsoft Mouse and then Windows, click&be done.You can easily delete any number of character or lines with vim
or replace every instance of a word very easily, much faster and efficient.

---

### Post by Jessehk on 2008-02-10
I always despised emacs, but I was using it in X11 mode. 

When I tried emacs in text-mode (emacs -nw), I was quickly impressed. It's now my favourite terminal editor (my previous favourite was nano).

---

### Post by mssever on 2008-02-10
I use both vim and gedit. Vim is awesome for quick edits or making changes to already-existing code. Commands like cw and d$ (and their friends and relatives) come in handy. However, IMO ~/.vimrc must contain at least the following before vim is usable (these commands do such things as enabling syntax highlighting, clicking, and line numbering, among other things):
```
syntax on
set scrolloff=5
set mouse=a
set number
set hlsearch
```
I mostly use gedit for extended hacking sessions involving many files and where I want autocompletion.

---

### Post by pmasiar on 2008-02-10
> **barbedsaber said:**
>  I would start with learning python, it seemed like the easiest one to learn.

But I have that little choosing a text editor problem.

IDLE is standard IDE for Python. Is very simple, but has all important features you need for Python as defaults. It comes included on Windoes, but has to be installed on Linux.

Other good editors are SciTE (universal text editor with good python mode) and SPE, Stani's Python editor. Both are universal editors optimized for Python.

In any editor, make sure you set tab as 4 spaces, and converting tabs to spaces, as Python standards suggests. If you mix tabs and spaces in source code, strange errors might happen - in Py3.0 mixing spaces and tabs will yield warning.

Another nice features to have is 
- "indent guide" - gray vertical line showing matching block level.
- block collapsing

---

### Post by lnostdal on 2008-02-10
> **Majorix said:**
> GUI is nice, because you want to
- Click here and there with your mouse and continue hacking from that point.

yeah, i can do that without a gui .. usually i do this faster using the keyboard though (the editor "understands" the code structure and allows me to navigate block-by-block or keyword-by-keyword etc.)

> 
- Have a terminal and other useful plugins mentioned by LaRoza attached.

yeah, i have that - but i don't need a gui

> 
- Copy&paste text with your mouse.

yeah, i can do that also without a gui .. usually i do it faster using the keyboard though for the same reason i mentioned above

---

### Post by Majorix on 2008-02-10
I am sure Gedit could have most of the same functionality with a little plugin, with all the fanciness of it. I still prefer Gedit hehe. Maybe you could write the plugin :p

---

### Post by lnostdal on 2008-02-10
> **Majorix said:**
> I don't want to shift off-topic, but I am posting these so not all newbies use Vim or Emacs.

let ppl use what they want to use .. i started with VIM as a total linux newbie, and i'm using Emacs now

> 
The problem with that article is, why shouldn't I use the mouse? It's the whole fun in programs with GUI!

it's slow .. i don't feel like "letting go" of my keyboard .. it interrupts my flow

> 
What if I don't want to delete a whole word, but a few characters, using Vim?

i haven't used vim in years, but i can imagine it handles this very efficiently .. i know emacs does

> 
Above all, what if I don't want to remember dozens of keyboard shortcuts just to be able to happily code?

i believe most editors have support for this

> 
I don't know, but I believe a human in 21st century MUST use GUI,

yeah, my (g)ui is my keyboard .. i don't have to have a button on the top of the screen labeled "Compile (F9)" .. after i've clicked it 10 000 times with my mouse i kinda get that i can press F9 on my keyboard to achieve the same thing .. so i'd rather use the space up there to see more code (context) instead of that silly button -- that i already have physically here on my keyboard (the old worn out F9 button, no?)

> 
 it wasn't invented for nothing. M$ got all those money because they produced Microsoft Mouse and then Windows, click&be done.

ok, this is just to silly for me to comment on

---

### Post by seventhc on 2008-02-10
> **lnostdal said:**
> *yeah, i can do that without a gui* .. usually i do this faster using the keyboard though (the editor "understands" the code structure and allows me to navigate block-by-block or keyword-by-keyword etc.)


yeah, i have that - *but i don't need a gui*

[I]
yeah, i can do that also without a gui[/I] .. usually i do it faster using the keyboard though for the same reason i mentioned above
So let me make sure I've got this straight...
You don't need a gui??? Right???  :D

---

### Post by stroyan on 2008-02-10
> **seventhc said:**
> @LaRoza

I wasn't aware vim had this feature, can you explain how that is enabled or a link please?
Thanks.

Just open a directory name with vim.
You get a list of file and directory names.
You can move around in the list like it was a text file.
Use 'j' and 'k' to move up and down.
Use '/pattern' to search.
Use 'enter' to edit a file.

---

### Post by pmasiar on 2008-02-10
> **Majorix said:**
> Above all, what if I don't want to remember dozens of keyboard shortcuts just to be able to happily code?

I don't know, but I believe a human in 21st century MUST use GUI, it wasn't invented for nothing. M$ got all those money because they produced Microsoft Mouse and then Windows, click&be done.

You don't remember shortcuts - your fingers do. It is like when you ride a bike: you don't remember shift your weight when turning - you just do it.

MSFT made all those money on noobs, while almost completely ignoring needs of experts. problem is, those days experts are so rare they are not interesting market, so (except of FOSS) they can be  ignored without market consequences.

And what is even more sad, said non-experts now don't even consider becoming experts, they feel comfortable enough with half-knowledge they have.

Remember: if $DEITY wanted us to interact with PC using mouse, it would created us with USB port in the wrist instead of 10 fingers. :-)

---

### Post by seventhc on 2008-02-10
> **stroyan said:**
> Just open a directory name with vim.
You get a list of file and directory names.
You can move around in the list like it was a text file.
Use 'j' and 'k' to move up and down.
Use '/pattern' to search.
Use 'enter' to edit a file.
I've been trying that but I must be typing it wrong.
can you post an example.
:)
:command???

I got it :) Actually looks familiar I must have used it in one of the tutorials, but haven't used it actively so I didn't remember.

---

### Post by LaRoza on 2008-02-10
:Explor

---

### Post by seventhc on 2008-02-10
> **LaRoza said:**
> :Explor
Thanks, I was actually do it differently but this way is much better. :)
I was doing it from the terminal
```
vim /home
```Just found that this works too
```
:Ex
```

Did some reading and here you can get split too
```
:Vexp
```
```
:Sexp
```
wow :)
Vim is Great:)

---

