---
title: "why emacs?"
date: 2010-03-10
forum: Programming Talk
---

### Post by icodemonkey on 2010-03-10
ok well i have been using geany for a while but time and time again i see posts like "use emacs" and "emacs is better then <X>".
My question is why (ie the easiest to understand) is emacs the best IYHO.

now to all the vi usrs out there. pipe down i didnt ask you! :p first mention of it you will be tied to a chair, forced to drink a slab of fosters and then watch every show, movie and concert staring mily cyrus. you have been warned.

breakdown of question:
1. after years of using mouse, keyboard combo i can type at a descent rate with one hand and use the mouse with the other. 
   * can emacs use a mouse to select text, perform drag-drop etc?

2. i use a lot of short-cut keys to do things with
  * can you set custom key combos for things

3. i have a lot of code snippets i use repeatedly
  * does emacs have a snippets system

any other selling points you can think of to convince a programmer to use it.

---

### Post by lykwydchykyn on 2010-03-10
> **icodemonkey said:**
> ok well i have been using geany for a while but time and time again i see posts like "use emacs" and "emacs is better then <X>".
My question is why (ie the easiest to understand) is emacs the best IYHO.

It's not the best, it just works really well for a lot of people.  Including me.

There are things I really don't like about emacs, but I do love the workflow of actually editing text files.  
> 
now to all the vi usrs out there. pipe down i didnt ask you! :p first mention of it you will be tied to a chair, forced to drink a slab of fosters and then watch every show, movie and concert staring mily cyrus. you have been warned.

I hope that threat works! :)
> 
breakdown of question:
1. after years of using mouse, keyboard combo i can type at a descent rate with one hand and use the mouse with the other. 
   * can emacs use a mouse to select text, perform drag-drop etc?

You can, but the mouse doesn't work quite the same as it does in other programs.  For instance, I can't highlight a region and bring up a right-click menu.  Maybe that can be configured, not sure.

Part of the reason I switched to emacs is because I DON'T like bouncing around between the mouse and keyboard.  I wanted an editor/IDE that could be used entirely with the keyboard.

You may not be happy with the mouse support in Emacs.  To be honest it has the feel of a feature that was kludged on, and it behaves a lot differently from how you'd normally expect.

> 
2. i use a lot of short-cut keys to do things with
  * can you set custom key combos for things

You can set custom key shortcuts all day long, though there's probably one already there for whatever you need.  You can also run any command by hitting alt-x and typing the command, which I often find more convenient than remembering the shortcut.

> 
3. i have a lot of code snippets i use repeatedly
  * does emacs have a snippets system

I don't use such a system myself, but I seem to remember seeing something along those lines once.  I'd be surprised if there wasn't an elisp file floating around out there to provide snippets.
> 
any other selling points you can think of to convince a programmer to use it.

I basically switched to Emacs after reading a tutorial on programming (can't remember what it was now) that recommended choosing a good, solid text editor that facilitated mouseless operation and learning how to use it like an expert.  This turned out to be good advice.  

Like I said there are a lot of things I don't like and/or miss using Emacs, but the text editing makes up for it.  The "modes" feature means that depending on what I'm editing, the editor adapts to accomodate it rather than being a generic one-size-fits-all editor.  For example, when in python mode, the "tab" key doesn't insert tab characters, it indents the start of the line (even if I'm not at the start of the line) by increments of four spaces (standard convention for Python), but in a way that's constrained by syntax (i.e., if indenting four more spaces wouldn't be syntactically correct, it doesn't indent).  Basically, while most editors do syntax highlighting, Emacs goes the extra mile by adapting to the idioms of different types of files.

What do I not like?  A good code browser (don't like ECB/CEDET), macros for working with QT (like Eric has), and better interoperability with my WM (it has weirdness with Kwin), among other minor things.

There are also some things I just haven't had time to sit down and figure out yet, like project management or svn integration.  That's one things about Emacs; there's a bit of a learning curve to most features.  It's not that doing stuff is hard, just different from most "wordpad-style" editors out there.

EDIT: One last thought.  The killer feature for Emacs is customization; every IDE has a preferences dialog, but other than Emacs I don't know any that have their own scripting language for customization and adding new features.  Major pieces of functionality are written in elisp, so in theory the sky is the limit with Emacs, provided you're willing to code it.

Even if you don't want to or can't code it, chances are someone else did and you can drop their script into your config and go.

---

### Post by nmccrina on 2010-03-11
Why not try V-*smother*

---

### Post by matthew.ball on 2010-03-11
> **icodemonkey said:**
> My question is why (ie the easiest to understand) is emacs the best IYHO.
I wouldn't say Emacs is necessarily easy to understand (well, once you have become familiar with it, it definitely becomes easier to play with, but the initial exposure is quite over-whelming).

> 
1. after years of using mouse, keyboard combo i can type at a descent rate with one hand and use the mouse with the other. 
   * can emacs use a mouse to select text, perform drag-drop etc?
I have a laptop, and I hate the laptop mouse (mice?), the keyboard just works. I've been typing for so long that I no longer have to look at the keyboard (I was never "taught" to touch-type, most people are these days). It just feels natural to use a keyboard. I can keep a steady flow going with minimal pauses, which is difficult (impossible?) with a mouse.

> 
2. i use a lot of short-cut keys to do things with
  * can you set custom key combos for things
Yeah, this is in fact *one* of the key strengths of Emacs - don't like a keybinding? Re-bind it!

> 
3. i have a lot of code snippets i use repeatedly
  * does emacs have a snippets system
There is some code-completion built into Emacs (M+/), but as far as I know, code-snippets are an additional add-on. I don't know of any off the top of my head, but a quick search on google returns quite a few. [This]("http://emacsblog.org/") appears to list at least one, as well as including some other documentation related to Emacs. (I didn't know of this site before, but I will bookmark it now, so cheers for making me look).

> any other selling points you can think of to convince a programmer to use it.
Probably not, I finally realise I can't sell Emacs to programmers (especially not here on UF :(), it's just something you have to try for yourself. If you like it, you like it. If you don't, you don't.

For me personally, I write a lot of papers/articles for university as well as coding. Sure it's possible to use a different text-editor, but Emacs just fits the need so well. I really like constantly learning new things, and Emacs has a plethora of features, each time I learn a new technique, something else crops up. I like that, though I have come to understand most people are quite different to me.

---

### Post by lisati on 2010-03-11
> **icodemonkey said:**
> ok well i have been using geany for a while but time and time again i see posts like "use emacs" and "emacs is better then <X>".
My question is why (ie the easiest to understand) is emacs the best IYHO.

now to all the vi usrs out there. pipe down i didnt ask you! :p first mention of it you will be tied to a chair, forced to drink a slab of fosters and then watch every show, movie and concert staring mily cyrus. you have been warned.


Fosters, huh? I feel your pain!

---

### Post by howlingmadhowie on 2010-03-11
i'd say it took me about a month to become productive in emacs and about 6 months until i really started using features that most other editors don't have. now i've been at it for 2 odd years so using any other editor reduces my productivity greatly. 

in other words: there's a learning curve to climb.

---

### Post by icodemonkey on 2010-03-11
well thanks for all the responces have started to tinker with emacs now. final question is there a way to get emacs to behave in a more GNOME-ish way or is emacs-gtk the gui-est it gets?

---

### Post by matthew.ball on 2010-03-11
I can't speak for anyone else here, but I just run Emacs in a terminal. I have slight OCD, and it was the most consistent way to have it running.

Edit: Maybe [this]("http://ubuntuforums.org/showthread.php?t=101613") will make it "look" more GNOMEish.

---

### Post by myrtle1908 on 2010-03-11
> **lisati said:**
> Fosters, huh? I feel your pain!

Coopers Pale Ale is the greatest Australian Beer!  Stuff is like cocaine in a glass.  I'm sure they put something in it that makes one want more and more.  Now that was OT ... my apologies ... still, good to see an oz/nz contingent here.

---

### Post by CptPicard on 2010-03-11
Not only are "most features implemented in elisp", but the editor itself is implemented in elisp, some string buffer methods excluded. Emacs is kind of a Lisp machine in itself, running an editor-application written in Lisp. That's why it is so infinitely customizable, of course...

---

### Post by Tibuda on 2010-03-11
Vim for the win. :D

just use what works for you...

---

### Post by Bachstelze on 2010-03-11
That's what I was wondering too when I realized the "Development Environments" class ay my university is mostly Emacs-centric... I really don't look forward to that.

---

