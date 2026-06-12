---
title: "ssh and vi"
date: 2012-10-29
forum: New to Ubuntu
---

### Post by JavaKid on 2012-10-29
I searched for this but was unable to find anything on it. I hope I'm not just being stupid.
I ssh into my 12.04 from my mac and then was trying to edit a file with vi. When I hit the i key to insert and then use the right arrow to move over one space to start to type in the new characters, the right arrow key inserts a 'C'.  What can I do to resolve this?

Many thanks for your help and apology if this is something stupid i'm doing wrong.

---

### Post by Lars Noodén on 2012-10-29
That happens on other systems, too.  The arrow is not a space.  Though if a space exists there, the arrow can move over it.  So if you want your line to have leading space, you must use the space bar.

---

### Post by JavaKid on 2012-10-29
no, actually i was trying to insert at the end of my .profile file and that's at the end of and if statement, which means the cursor is sitting on a i of the fi. so when i move to that position and hit the i for insert, i then tried to move to the right of it with the right arrow and get a 'C' and a line return.  I got on the actual machine and it turns out it actually does this with the keyboard that I'm using on that machine.  It detected the keyboard when i installed, so i'm not sure why this is happening yet.  I'll keep looking for a fix for this but feel free to slap me around and set me straight.

vim  version 7.3.429

---

### Post by kanikilu on 2012-10-29
I know next to know thing about vim, but there are a couple possibly-related questions on StackOverflow that suggest setting the following options:

```
:set nocompatible
:set term=ansi
```

Sources:

[http://stackoverflow.com/questions/6787038/my-vim-7-3-does-not-behave-the-same-way-as-vim-7-1](http://stackoverflow.com/questions/6787038/my-vim-7-3-does-not-behave-the-same-way-as-vim-7-1)

[http://stackoverflow.com/questions/812973/linux-vi-arrow-keys-broken-in-insert-mode](http://stackoverflow.com/questions/812973/linux-vi-arrow-keys-broken-in-insert-mode)

---

### Post by JavaKid on 2012-10-29
ok, here's what I did.

sudo apt-get install vim

I'm not sure why, but it would open a file with the vi command and when I did a vi -v I got:

           vim  version 7.3.429

So I don't completely understand why I was having this problem, but now everything is in beautiful color and working fine.  Thank you for your suggestions.

Time for more Java !


hmmmm, how do i mark this as SOLVED ?

---

### Post by mahdiolfat on 2012-10-29
To mark as solved, look under "Thread Tools" at the top right hand corner of the thread.

-
Mahdi

---

