---
title: "Automatically put the shebang line in a vim file?"
date: 2006-11-02
forum: Programming Talk
---

### Post by mhueting on 2006-11-02
Hi, I'm just starting to learn python, and I find it quite annoying to put in the "#!/usr/bin/env python" line everytime I try a new example from the tutorial. Is it possible when I start a file that ends in .py, that vim automatically puts that line in? And how would I go about doing that? :biggrin:

I'd love to learn vim and python all the way, and asking questions is part of it I think :)

---

### Post by xtacocorex on 2006-11-02
You could make a file called template.py that has the shebang line and when you want to do another tutorial:
```

cp template.py progname.py
vi progname.py

```
You might have to write a plugin for vi so that you can call it up and it'll print that line at the top of a file. I haven't actually written a plugin on my own though, so I can't be of much help there.

---

### Post by mhueting on 2006-11-02
Well, thanks, but that's not really what I meant ;)

I mean that whenever I start a new file in vim that ends in .py, that vim will automatically put "#!/usr/bin/env python" in the first line.

Thanks anyway :)

---

### Post by rahufnagl on 2006-11-02
Personally, I would write a script using sed, but that is just me.

However, if that way is not practical you could instead create an abbreviation in vi that would allow you to only have to type a smaller amount of characters to get the string you desire.

ex.
:ab py #!/usr/bin/env python

If you were to use this abbreviation whenever you would type py '#!/usr/bin/env python' would be inserted in its place.

These are just some ideas.  There are plenty of other ways to accomplish the task you are wanting, but I'm not sure if you will be able to find a way to add the shebang line automatically.

---

### Post by steev on 2006-11-02
Just add something similar to this to your .vimrc (this is what I have in mine)

```
if has("autocmd")
augroup content
autocmd BufNewFile *.py
   \ 0put = '#!/usr/bin/env python'  |
   \ 1put = '#-*- coding: utf-8 -*-' |
   \ $put = '' |
   \ $put = '' |
   \ $put = '# vim: set sw==3 tw=80 :' |
   \ norm gg19jf]
augroup END
endif
```

(I have a lot more than that, but I am guessing you can figure out based on that example what some of the others would be like :)

---

### Post by po0f on 2006-11-02
steev,

That's pretty freaking useful!  I always felt obligated to write a comment at the beginning of every source file and hated manually putting in include guards for header files in C++, but now it will be so much easier!  Development time has been cut in half!  (not really...)

---

### Post by kampsuniahv on 2007-01-15
I know that this thread is old, but how can i add line with filename. Something like this.

#Filename: <FILENAME>

---

### Post by Ragazzo on 2007-01-16
> **kampsuniahv said:**
> I know that this thread is old, but how can i add line with filename. Something like this.

#Filename: <FILENAME>

```

autocmd BufNewFile *
   \ 0put = '#Filename: ' . expand('<afile>') |
   \ normal G

```

If you want to add the full path, change '<afile>' to '<afile>:p' (:help filename-modifiers). * is the filename pattern so change it to *.py if you want to target only Python files. \ is used to cut the command on many lines to increase readability and | is used to execute multiple commands. "normal G" means the normal-mode command G which moves the cursor to the last line.

---

### Post by fadder on 2007-01-17
I can't get the above types of vimrc stuff to work. For example, if I try:

autocmd BufNewFile *.py
   \ 0put = '#!/usr/bin/env python'  |
   \ normal G

I get:
--- Auto-Commands ---
Error detected while processing /home/fadder/.vimrc:
line    2:
E10: \ should be followed by /, ? or &
line    3:
E10: \ should be followed by /, ? or &


It would be great to get this working, so thanks for any help. I have tried with and without spaces after the \.

---

### Post by Ragazzo on 2007-01-17
You are probably in compatible-mode (:help E10). You can put "set nocompatible" in .vimrc or avoid using \.

```

function BufNewFile_PY()
0put = '#!/usr/bin/env python'
normal G
endfunction

autocmd BufNewFile *.py call BufNewFile_PY()

```

---

### Post by fadder on 2007-01-18
Thanks! Works great now.   :D

---

