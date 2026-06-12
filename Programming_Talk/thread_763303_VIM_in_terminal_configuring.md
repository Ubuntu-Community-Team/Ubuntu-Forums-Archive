---
title: "VIM in terminal configuring"
date: 2008-04-22
forum: Programming Talk
---

### Post by jus71n742 on 2008-04-22
I have VIM and GVIM and I use the in terminal VIM but I can not get any syntax highlighting, font color, font, etc etc. how can I configure the settings so that I can use the VIM how I want it to work?

---

### Post by geraldm on 2008-04-22
EITHER
  edit in your configuration file ~/.vimrc : add  a line "syntax on"
OR
  after you begin editing a file in vim, you can type <ESCAPE> : syntax on <RETURN>
END
To turn off : syntax off 

Gerald

---

### Post by dwhitney67 on 2008-04-22
The previous post is correct, however if you do not have the "full" vim installed on your system, it might not work.  To get the full vim distro, run this command:

```
$sudo apt-get install vim-full
```

---

### Post by jus71n742 on 2008-04-22
> **geraldm said:**
> EITHER
  edit in your configuration file ~/.vimrc : add  a line "syntax on"
OR
  after you begin editing a file in vim, you can type <ESCAPE> : syntax on <RETURN>
END
To turn off : syntax off 

Gerald

ok I am being denied permission to run the ~/.vimrc
I also do have full vim

---

### Post by dwhitney67 on 2008-04-22
You shouldn't be trying to "run" the ~/.vimrc file... just edit it (using gedit or something similar) and insert the line:
```
syntax on
```

---

### Post by jus71n742 on 2008-04-22
thanks I got it working 
both of you ...many thanks

---

### Post by mssever on 2008-04-23
> **dwhitney67 said:**
> You shouldn't be trying to "run" the ~/.vimrc file... just edit it (using gedit or something similar)
Something similar, such as vim?

/me starts running. Fast. :)

---

### Post by erginemr on 2008-04-23
For more general information on how to configure vim:
*[http://ubuntuforums.org/showpost.php?p=4576155&postcount=2](http://ubuntuforums.org/showpost.php?p=4576155&postcount=2)*

---

### Post by jus71n742 on 2008-04-23
> **mssever said:**
> Something similar, such as vim?

/me starts running. Fast. :)

no I remember now I felt stupid for making this mistake 
```
 gedit~/.vimrc
```

---

