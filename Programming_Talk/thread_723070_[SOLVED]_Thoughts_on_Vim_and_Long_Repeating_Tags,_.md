---
title: "[SOLVED] Thoughts on Vim and Long Repeating Tags, quick-keys or the like available?"
date: 2008-03-13
forum: Programming Talk
---

### Post by Gen2ly on 2008-03-13
Hey guys.

I'm just starting on vim and am really liking it.  I've been using it to create html pages and some basic scripts.  It's a great program.  I though at times find myself having to type a long line that I haverepeated before, so it's a big of a drag to repeat it again.  In fact, I've discovered in the html work I'm doing some of these tags I'm doing over and over...

```
<img src="http://wiak.com/images/bullet.png" style="border-width:0;" class="com" alt="bullet bullet" />
```

For example.  I could shorten this a bit in my css but for the mostpart it's become a dull to repeat.  I know that Vim has alot of customizable and has some shortcuts, what can I do to help this process?

---

### Post by mssever on 2008-03-13
> **Dirk.R.Gently said:**
> Hey guys.

I'm just starting on vim and am really liking it.  I've been using it to create html pages and some basic scripts.  It's a great program.  I though at times find myself having to type a long line that I haverepeated before, so it's a big of a drag to repeat it again.  In fact, I've discovered in the html work I'm doing some of these tags I'm doing over and over...

```
<img src="http://wiak.com/images/bullet.png" style="border-width:0;" class="com" alt="bullet bullet" />
```For example.  I could shorten this a bit in my css but for the mostpart it's become a dull to repeat.  I know that Vim has alot of customizable and has some shortcuts, what can I do to help this process?

Well, yy will copy a line, and p will paste it. Beyond that, check out vimtutor. Personally, I use vim for most stuff, but when it comes to extended hacking sessions (such as when writing quite a bit of new code), I usually find Gedit more convenient. That might be in part because I only know a small subset of all of vim's features.

---

### Post by ruy_lopez on 2008-03-13
See also CTRL-n which attempts to complete what you type based on what else is in the text.

---

### Post by shawnhcorey on 2008-03-13
There are 26 buffer available aside from the specific purpose ones.  To yank a line into buffer 'a', place the cursor on the line and (note the double-quote):

  "ayy

To place it elsewhere, move to the line above where you want it and (note the double-quote):

  "ap

There are 25 other buffers, from 'b' to 'z'.

Some special purpose buffers:

  /   the last search pattern
  +  the clipboard
  "   the un-named buffer (the place where everything goes when you don't name a buffer).

You can also delete to a buffer.  To delete a word and place it in the clipboard (Edit->Cut):

  "+dw

---

### Post by Gen2ly on 2008-03-13
Actually these buffers may be what I'm looking for. I will have about five long lines that I will need quick access to.  And control-N is nice for really longwords.  I like bluefish enough but I was moving back and forth from keyboard to mouse so often I eventually just found it quicker to remember what I needed to and just type in vim.  Requires a whole lot of concentration though. :-k

---

### Post by stylishpants on 2008-03-13
Ctrl-x Ctrl-l (that's little L not I) will complete an entire line, based on the previous lines.

---

