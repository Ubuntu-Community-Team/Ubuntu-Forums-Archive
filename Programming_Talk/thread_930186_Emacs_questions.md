---
title: "Emacs questions"
date: 2008-09-25
forum: Programming Talk
---

### Post by Peter Frank on 2008-09-25
Ctrl+K kills a line, but I'm wondering whether I can copy a line into the killring without killing it?

Also, is it possible to autocomplete class member names when you type "[class name]. "?

---

### Post by monkeyking on 2008-09-25
Which language do you want autocompletion for?
I remember I used something called jde for emacs,
that was able to do it, but that was for java.

---

### Post by unutbu on 2008-09-25
C-space C-e M-w    will copy the line instead of cutting the line.

---

### Post by ankursethi on 2008-09-26
C-SPACE sets the mark. It's like holding down the Shift key, only you don't have to actually hold anything down. You just hit C-SPACE and move the cursor to whatever position you like. Then you hit M-W, as unutbu said.

Type M-/ for autocomplete. This is a universal feature, and will only look at the list of words you have typed so far in the buffer. I find it enough for myself, though.

You might want to check out : [http://emacswiki.org](http://emacswiki.org)

---

