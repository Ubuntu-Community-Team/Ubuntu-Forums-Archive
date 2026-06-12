---
title: "PyCurses - Force terminal size"
date: 2006-11-27
forum: Programming Talk
---

### Post by ironfistchamp on 2006-11-27
Hey all

I have just worked out (the hard way) a major annoyance with using curses. When you try to write to a window and there is not enough room BOOM there goes the program. I thought that maybe one could specify how big you wanted the terminal to be and then count lines to be careful. But then you run into problems with using TTY's (is that what they are called... Ctrl Alt F1 things) and possibly different resolutions (specifying too many cols/rows).

I wrote a very basic function that accepts a window and string and will try to output or erase and then output if that fails. Very primitive and I don't really want to have to keep doing that as it will break up the flow of the program.

Can anyone help me with this problem. 

Also there is a problem with text in Gnome terminal on Edgy. The text comes out grey in curses apps and underline, bold and other text styles don't work. Any ideas?

Thanks

Ironfistchamp

---

