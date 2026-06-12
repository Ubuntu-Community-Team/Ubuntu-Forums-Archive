---
title: "Vim - use CtrlP with the same directory after opening a file ..."
date: 2013-09-12
forum: Programming Talk
---

### Post by mind_exploit on 2013-09-12
Hello,

I'm learning vim currently, and I when I use the "Ctrl-P" plugin - I'm able to quickly find a file in the project directory.

```
 :CtrlP /path/to/the/project/root      ===>      Enter     ===>     <C-d>    ===>     and start typing the name of the file.
```

So, my question is: after I open the file - in new tab or in split - how can I call CtrlP again, pointing to the same doc root? ... Cause if I just type :CtrlP - it is pointing to the folder where the last opened file is.

And I want CtrlP to point to the doc root again, without typing the whole

```
:CtrlP /path/to/the/project/root    ===>    Enter ...... 
```

Thanks in advance ;) ...

---

### Post by trent.josephsen on 2013-09-12
I'm not familiar with that plugin, but can't you just hit :<Up> and use the last run command?

Barring that, does it default to the current working directory? Because you can use the :cd command to change your working directory. (Or just cd to the project root before you run vim.)

---

### Post by MadCow108 on 2013-09-12
see the help of ctrlp:
g:ctrlp_root_markers for the root modes, most useful is probably the 'r' which will search for the root of a version control
there is also g:ctrlp_root_markers to define own roots

---

### Post by mind_exploit on 2013-09-13
Well, the little trick with entering the root directory of the project, and then run vim - did the job :) ... 

So, when I enter the project root folder, run vim, hit <C-p>, quick-find a file and open it, and after that hit <C-p> again - then CtrlP plugin is automatically set to search in the project root again :) ... 

Thank you :) ;) ...

---

