---
title: "python specific mapping in vim"
date: 2010-09-03
forum: Programming Talk
---

### Post by FreeTheBee on 2010-09-03
Hi, I was trying to add a mapping to my .vimrc file that would allow me to do some quick imports in python. I tried the following,

autocmd BufRead,BufNewFile *.py imap ,SNM import scipy as sci<cr>import matplotlib as mpl<cr>import matplotlib.pyplot as plt<cr><cr>

autocmd FileType imap ,SNM import scipy as...

and just the imap... into python.vim in my ftplugin folder.

In all cases the mapping does not work as long as I do not open a python file, as it should. However after opening a python file it becomes available in all other buffers as well. I expected the command to be exclusively available to the buffers that contain a python file. What am I missing here?

---

### Post by DaithiF on 2010-09-03
Hi,
a mapping is global by default except where you make it specific to a buffer.  you do this by adding <buffer> to the map command, e.g.:

```
imap <buffer> ,SNM etc.

```

---

### Post by FreeTheBee on 2010-09-03
That did the trick, thanks.

---

