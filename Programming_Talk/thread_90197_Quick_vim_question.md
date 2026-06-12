---
title: "Quick vim question"
date: 2005-11-14
forum: Programming Talk
---

### Post by closet geek on 2005-11-14
How do I stop vim from highlighting the last character of the word I've typed when I enter command mode, this causes me to start typing behind this character when I enter insert mode again!

Cheers,

cg

---

### Post by Sheco on 2005-11-14
That's normal behaviour, since vim has to have the cursor on a valid character, and the behaviour would change on the end of line (the cursor on the command mode can be on after the last char)

You should use 'a' to add text after the cursor, instead of i, to insert text at the cursor.

---

### Post by closet geek on 2005-11-14
[QUOTE=Sheco]That's normal behaviour, since vim has to have the cursor on a valid character, and the behaviour would change on the end of line (the cursor on the command mode can be on after the last char)

You should use 'a' to add text after the cursor, instead of i, to insert text at the cursor.[/QUOTE]

Thanks, while I get used to it all is there no way to force the behaviour I would fine preferable?

cg

---

### Post by salva on 2005-11-14
[QUOTE=closet geek]Thanks, while I get used to it all is there no way to force the behaviour I would fine preferable?

cg[/QUOTE]

you can always define new shortcuts in your home directories .vimrc
There is extensive information on all things vim related on their homepage
[www.vim.org]("www.vim.org")
But basically for common things as i and a i wouldnt suggest changing much.
It may end up making getting used to things the vim way more complex.
Of course you may end up making a set of excelent shortcuts, in which case all would be dandy ;)

---

### Post by David Marrs on 2005-11-14
I'd try to stick with Vim's way for a while before you start making changes to its behaviour. It really will make sense once you start using command mode in earnest. Another useful tip is that 'I' & 'A' (that is, shift+i & shift+a) enter insert mode at the beginning and end of the line respectively.

---

### Post by closet geek on 2005-11-14
Yeah to be honest I think just ignoring 'i' and always using 'a' will be fine for me.

cg

---

### Post by salva on 2005-11-14
thats what i do 90% of the time :D

---

