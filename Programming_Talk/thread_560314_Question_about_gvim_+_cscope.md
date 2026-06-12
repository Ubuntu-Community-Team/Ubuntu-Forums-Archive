---
title: "Question about gvim + cscope"
date: 2007-09-26
forum: Programming Talk
---

### Post by jutirain on 2007-09-26
I've installed cscope on my gvim.

Sometimes it works just fine, but sometimes it will prompt out the error message when I start gvim:

```
Error detected while processing /usr/share/vim/vim70/plugin/cscope_maps.vim:
line   42:
cs_read_prompt EOF: Illegal seek
E609: Cscope error: cscope: cannot read trailer offset from file cscope.out
jutirain@Freedom:~/Research/Semi-automatic Composition/Code/Semi-automatic_Composition$ gvim *.cpp *.h
7 files to edit
Error detected while processing /usr/share/vim/vim70/plugin/cscope_maps.vim:
line   42:
cs_read_prompt EOF: Illegal seek
E609: Cscope error: cscope: cannot read trailer offset from file cscope.out

```

even I use
:cs add cscope.files     or
:cs add cscope.out

It won't work. :(

Any idea?

BTW, after using my 1680 * 1050 resolution new monitor, my cscope output become a little ugly... bottom of each line didn't show up properly, like the following one:

[http://graphics.csie.ntu.edu.tw/~jonathan/temp/cscope.png](http://graphics.csie.ntu.edu.tw/~jonathan/temp/cscope.png)

What's the problem?

---

### Post by sylvarant on 2008-07-23
I've just encountered this topic via google as I'm having the same problem
Did anyone find a solution to this problem or should it be bug reported

---

### Post by sylvarant on 2008-07-23
I've actually found a solution for this,
to not encounter it anymore make sure not to use folders with
spaces in their names,
thats apparantly whats causing this problem :)

---

