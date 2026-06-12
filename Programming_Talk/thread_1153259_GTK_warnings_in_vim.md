---
title: "GTK warnings in vim"
date: 2009-05-08
forum: Programming Talk
---

### Post by cak3 on 2009-05-08
When executing a command that launches something graphical from vim (for example, the pdf viewer from vimlatex) I get any gtk warnings (just the basic terminal output when launching something, in this case it is some gtk warning about icon sizes) dumped into the file I am editing. sort of. They arent actually in the file, if I save it, but they appear in the text and are very irritating. They will disappear if I scroll past them and then back up, but I would prefer if they were not shown in vim at all.

I am just wondering if this is something that is fixable by messing with settings. or if its a bug (and I should report it).

here is my .vimrc:
```

syntax on
set number
set expandtab
set shiftwidth=4
set ts=4
hi LineNr ctermfg=gray
filetype plugin indent on
au BufRead,BufNewFile *.s    set syn=mips autoindent

let g:tex_flavor='latex'

```

I am using vim 7.2.79 (from the jaunty repos).

Edit: The unwanted text also dissappears when resizing the terminal window. I am attaching a screenshot. It happened when i used the vimlatex shortcut to view the generated pdf (it doesn't only happen with vimlatex, thats just the fastest was to reproduce the problem).

---

### Post by ibuclaw on 2009-05-08
That isn't vim causing the issue, that is the gtkrc file you are using.

```
cat -n /usr/share/themes/eGTK/gtk-2.0/gtkrc
```

Regards
Iain

---

### Post by cak3 on 2009-05-09
Thanks. Thats where the warnings come from then, but I was really wondering why the warnings get dumped into the text of whatever document I am working on in vim. The warning text is actually selectable and editable in vim (as if I had entered it normally) except for the fact that it dissappears when I scroll past it and back or resize the terminal window.

Any ideas about that?

Derek.

---

### Post by cak3 on 2009-05-12
Anyone?

---

### Post by hugmenot on 2009-05-13
You have to fix the theme. This is GTK outputting the errors, not vim itself.

---

### Post by haTem on 2009-05-14
> **hugmenot said:**
> You have to fix the theme. This is GTK outputting the errors, not vim itself.

I think he wants to know if it's possible to, in general, suppress any output generated from an external application launched from within vim. Having the output dumped on top of the file you're editing could get annoying :P.

There's probably a better solution, but you could redirect the output to a file so that it is not printed out. e.g. "mycommand > output.txt" or maybe "mycommand > /dev/null" if you don't want to save the output.

---

### Post by dwhitney67 on 2009-05-14
> **cak3 said:**
> Thanks. Thats where the warnings come from then, but I was really wondering why the warnings get dumped into the text of whatever document I am working on in vim. The warning text is actually selectable and editable in vim (as if I had entered it normally) except for the fact that it dissappears when I scroll past it and back or resize the terminal window.

Any ideas about that?

Derek.

You can also use ctrl-l (ell) to refresh the vim screen.

As for redirecting the messages, they are probably going to stderr.  You can redirect those using the 2> shell operator.  Probably best to redirect to /dev/null, unless you want to read them later.

---

### Post by ibuclaw on 2009-05-14
> **dwhitney67 said:**
> You can also use ctrl-l (ell) to refresh the vim screen.

As for redirecting the messages, they are probably going to stderr.  You can redirect those using the 2> shell operator.  Probably best to redirect to /dev/null, unless you want to read them later.

true,

But it will be more hassle working around the problem, when you could just instead make 3 or 4 edits to your gtkrc file be done with the issue entirely.

---

