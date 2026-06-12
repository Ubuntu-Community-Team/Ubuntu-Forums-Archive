---
title: "curses and ansi color codes"
date: 2006-09-19
forum: Programming Talk
---

### Post by Kvark on 2006-09-19
I'm trying to write a program that gets text containing ansi color codes and displays it to the user using curses. But I just can't figure out how to make curses handle the ansi codes correctly.

Here is an example of my problem. This program prints the text with curses and waits for the user to hit a key. Then exits curses and prints the text normally. The colors doesn't work in curses but do work when printed normally.
```
#!/usr/bin/env python
import curses
def colortest(main_window):
	main_window.addstr(colorsample)
	main_window.getch()
if __name__ == "__main__":
	colorsample = """[32mThis is colored text.[37m

This is normal text.
[32mThis is colored text.[37m

This is normal text.
[32mThis is colored text.[37m

This is normal text.
"""
	curses.wrapper(colortest)
	print colorsample
```

---

### Post by bjarneh on 2008-01-30
you should let curses figure out the color escape sequenses for your terminal, this is an old thread so a short answer..
curses is very poorly documented in Python, in good old Python tradition


try:
  import curses
except: return #to whatever

ansi_foreground = curses.tigetstr('setaf')

if(ansi_foreground):
   ansi_black_fg = curses.tparm(ansi_foreground, 1)
   ansi_blue_fg = cuses.tparm(ansi_foreground, 2)
#
#

print ansi_blue_fg+"i'm blue"

---

