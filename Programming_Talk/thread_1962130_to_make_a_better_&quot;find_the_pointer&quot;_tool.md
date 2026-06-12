---
title: "to make a better &quot;find the pointer&quot; tool, what language should I learn?"
date: 2012-04-20
forum: Programming Talk
---

### Post by Dreamer Fithp Apprentice on 2012-04-20
I want to make a better "find the mouse pointer" program.  So it will need to be aware of the pointer position and be able to lay a graphic on top of a window in response to a selectable hot key.

My experience is limited to batch files under MS-DOS, 4DOS, Windows, and 4NT, enough bash under Ubuntu to write a few small things I find useful, a couple of scripts in csh, a half dozen or so LSL (Linden Scripting Language, used in Second Life) scripts, and long ago, the language the TI-59 was programmed in, which I have been told is similar in its primitive simplicity to machine code. I've never learned a high level language.  I doubt if anything I've written has been over 300 lines, maybe not even a hundred, with the longer ones being 4DOS batches.

If I have to put weeks of study into it before I can make it do anything useful I'll probably get discouraged.  So I'm looking for recommendations as to what language I should study.  Thanks for reading.

---

### Post by sudodus on 2012-04-20
1. Have you tried ```
xeyes
``` that 'looks at' the mouse pointer? That is an old unix program ported to linux. There is also a panel applet based on or inspired by xeyes.

2. If you are not prepared to spend at least a couple of weeks, you cannot expect to learn something powerful. But you can start reading tutorials about scripting languages and some more advanced language, for example C, C++, and compare the general feeling of it. After that you can dive deeper into some language or programming tool.

---

### Post by hakermania on 2012-04-20
After a lot of searching I resulted that this is one of the best codes available around: [http://ubuntuforums.org/showthread.php?t=1248711](http://ubuntuforums.org/showthread.php?t=1248711) (at post #4) and it works fine for me. It's C, so the thought is grabbing cursor position (it is very easy to do so with Qt (C++)) and drawing something around it so as to see where the pointer is.

For calling this program using a hotkey (like Ctrl in Windows) you can see Ubuntu's 'System Settings' program source code on how it does it. See the source code of it:
```

apt-get source gnome-control-center

```The code that should be interesting for you is panels/keyboard/keyboard-shortcuts.c

Hope I helped a little bit.

---

### Post by Dreamer Fithp Apprentice on 2012-04-21
Thanks, guys! That is really above and beyond. I had given up on finding anything already made or even half way toward what I want.  I'm not expecting to turn into richard stahlman in a couple of weeeks. It's more that I can sustain my focus better if I can bite off  projects small enough to actually complete and put more tools in the toolkit as I go along so to speak. I'll study both of these.

---

### Post by hakermania on 2012-04-22
Keep us informed for any news :)

---

