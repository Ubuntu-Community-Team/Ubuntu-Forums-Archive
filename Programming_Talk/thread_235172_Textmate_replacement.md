---
title: "Textmate replacement?"
date: 2006-08-12
forum: Programming Talk
---

### Post by Note360 on 2006-08-12
I have been looking for a Textmate replacement. I have been usign gvim and it is great but I kinda want a GUI editor. I have been using PIDA to manage my Python projects and I occasionally use Scribes which is great.

Scribes has the potential, but it lacks some features I like, such as tabs and themes.

---

### Post by Daverz on 2006-08-13
Well, the g in gvim stands for GUI.

I suppose you could try gedit or kate, or maybe nedit (motif, <shudder>, but that shouldn't matter much).

Here's a [list of editors for Python](http://wiki.python.org/moin/PythonEditors#head-b53ef1475e2d0f89e83733d3c51344235d1144ff) which may be useful.

I'm an XEmacs guy, myself.

---

### Post by skymt on 2006-08-13
If you don't mind Java, [jEdit](http://www.jedit.org/) is pretty nice.

---

### Post by Note360 on 2006-08-13
Sorry, I know gVim is GUI. That was stupid. I meant with common commands (CTRL-V pastes) I have been trying to map but it wont work. Can any one help me map "+gP to CTRL-V or SHIFT-CTRL-V.

---

### Post by Jessehk on 2006-08-14
Try the cream editor, it's in the repositories.

It's name reflects the way it "softens" up vim for the average user; like cream taking the bite away from coffee.

It has all the standard keyboard shortcuts like Ctrl-V, etc.

---

### Post by 3david on 2006-08-15
> **Note360 said:**
> Sorry, I know gVim is GUI. That was stupid. I meant with common commands (CTRL-V pastes) I have been trying to map but it wont work. Can any one help me map "+gP to CTRL-V or SHIFT-CTRL-V.

By default Ctrl-V in vim is used to insert special characters (like escape, try doing Ctrl-V Escape, you'll see "^[").

To paste from the clipboard i usually do this during insert mode:
<c-r>*
or
<c-r>+

(pastes from the * buffer or + buffer which are the two clipboards on linux)

If you wanna map ctrl-v to paste anyway then do this:

map <c-v> "+gP
imap <c-v> <c-r>+

(ctrl-c i never remap because it's even more useful: block selection).

---

### Post by LFT on 2006-08-19
> **Note360 said:**
> I have been looking for a Textmate replacement. I have been usign gvim and it is great but I kinda want a GUI editor.

Cream is a version of gvim that is a visual editor, but with all of the power of vim.  To get back into modal vim, set Cream to "[expert mode]("http://tips.webdesign10.com/jedit-cream-gvim-and-vim-for-ruby-on-rails")" and then use ESC to toggle vim's normal mode.

Other good editors for Ubuntu:
Kate
Quanta
SciTE

---

### Post by chonger on 2006-08-19
What are you looking for in a GUI editor? prettiness? Good color syntax highighting to make coding easier? Support for a particular language?

I prefer Xemcas, emacs makes it easy (umm... I'm not being sarcastic, once you learn lisp) to add your own marcros/functionality to the editor. Xemacs provides great package management. 

For Java coding, I have to use Eclipse. But Xemacs is what I use for other every day tasks, including Python coding.

---

### Post by Note360 on 2006-08-19
I think I will stick with gVim and scribes. I really hope that scribes includes tabs one day.

---

