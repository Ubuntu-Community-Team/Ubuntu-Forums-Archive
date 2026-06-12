---
title: "move cursor back to previous search in vi"
date: 2014-06-05
forum: Programming Talk
---

### Post by IAMTubby on 2014-06-05
Hello,
 Today, I learnt this nifty little usage of search and replace in vi.
I am using **:%s/word/123/gc** to replace all occurrences of 'word' with '123' in the entire file along with asking for confirmation

However, say vi asks for confirmation before replacing at line 5, and I say NO, by mistake. The cursor is now at line 6. Is it possible to go back to line 5 and say YES.

Although this would not be very useful if you said, YES by mistake and want to change it to NO since the word at line 5 would've been changed already :)

Thanks.

---

### Post by trent.josephsen on 2014-06-05
Not as such, but you can hit 'q' to stop the search-and-replace and 'u'ndo only the last replacement, then continue with something like one of these:
```
:6,$s/word/123/gc    (replace from line 6 to the end of the file)
:.,$s/word/123/gc    (replace from the current line to the end of the file)
VG:s/word/123/gc     (select from the current line to the end of the file in visual line mode, then replace on the selection)
```
You don't have to type the whole expression multiple times, though, because it's available in the command history (hit :<Up>).

I'm assuming Vim and not one of the other vi flavors.

---

### Post by IAMTubby on 2014-06-05
> **trent.josephsen said:**
> :6,$s/word/123/gc
Thank you so much trent.josephsen, that was very useful.

> You don't have to type the whole expression multiple times, though, because it's available in the command history (hit :<Up>).
Thanks, I didn't know that

> 
I'm assuming Vim and not one of the other vi flavors.
Yes vim.

Trent, I have one more question, I did something (typo) and my vi screen was split in two, with the file on the top half and my command history in the bottom half. How do I get this again?

---

### Post by trent.josephsen on 2014-06-05
That's easy. Way too easy; I'm always doing it by accident. It took a long time for me to figure out exactly what typo it was.

```
q:
```

---

### Post by IAMTubby on 2014-06-10
> **trent.josephsen said:**
> That's easy. Way too easy; I'm always doing it by accident. It took a long time for me to figure out exactly what typo it was.

```
q:
```
haha :D
thanks trent.josephsen

---

