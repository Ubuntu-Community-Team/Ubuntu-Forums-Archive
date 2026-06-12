---
title: "vim iabbrev"
date: 2013-02-13
forum: Programming Talk
---

### Post by linux_noob0 on 2013-02-13
Hi, I've been reading about [vimscript]("http://learnvimscriptthehardway.stevelosh.com/chapters/14.html"), and I can't get this one example to work:
```

iabbrev iff if ()<left>

```
(This code is a simplified version of the one given in this book, this is just to show where the problem is without unnecessary stuff around it).

So in theory, when I type iff in insert mode, I should get if (), with my cursor positioned on the ')' character (**before**, actually).

This doesn't happen however, I get if ( ). If I remove <left> in the above code, I get if (), with my cursor positioned **after** the ')'. 

My question: why does <left> do anything other than movement? :)

By the way, I also tried it with <esc> instead of <left>, and amazingly it printed if (), and moved to the **next line**.

---

### Post by trent.josephsen on 2013-02-13
It's because you're entering the abbreviation by typing "iff<Space>". The space doesn't get eaten, it gets added. With <left>, it gets added between the parentheses. Without, it gets added after the ). With <esc>, you leave insert mode, and space does its normal behavior of moving to the next character -- which will move you to the next line if you're currently at the end of a line.

Try "iff<Enter>" and you'll see that the newline gets inserted between the parentheses as well.

I'm not sure what the best way is to avoid this. I don't think there's a default key that will terminate an abbreviation but won't mess up the next thing you're typing. You could bind something (say Ctrl-L) to Ctrl-O i, which is a no-op but allows Vim to replace the abbreviation. Do

:imap <Ctrl-L> <Ctrl-O>i

and then when you want to say

```
if (i == 0)
```
you'd type "iff<Ctrl-L>i == 0".

---

