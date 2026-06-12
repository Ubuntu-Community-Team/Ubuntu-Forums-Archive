---
title: "vim indent"
date: 2010-10-14
forum: Programming Talk
---

### Post by l3ecl on 2010-10-14
when im in insert mode and make a new line, how do i make vim automatically use the previous lines's indentation?

for example when i type:
```

foo
    foo
        foo
        foo

```

i would have to press the tab key, once for 2nd line, twice for 3rd line, and twice on 4th line.

however, if i was using the previous line's indentation, i would only have to press 1 tab for the 3rd line (b/c already using 2nd line's indentation) and 
0 tabs for the 4th line(b/c its already using 3rd line's indentation)

---

### Post by spjackson on 2010-10-14
> **l3ecl said:**
> when im in insert mode and make a new line, how do i make vim automatically use the previous lines's indentation?

```

:set autoindent

```You don't have to press TAB at all. When you hit return it automatically indents the same as the previous line.

---

### Post by shawnhcorey on 2010-10-14
Also, if the indentation is too much, press CTRL-D to back up one tab stop.

If you not in insert mode, use >> to indent the current line one tab stop, << to outdent one tab stop.

---

### Post by l3ecl on 2010-10-14
```
set autoindent
```

thanks so much for the output but for some reason it's not working 

my ":set" output below, and interestingly i can't find autoindent

> :set
--- Options ---
  cindent             laststatus=2        scroll=17           tabstop=4
  filetype=vim        number              smartindent         ttyfast
  helplang=en         paste               syntax=vim          ttymouse=xterm2
  backspace=indent,eol,start
  fileencoding=utf-8
  fileencodings=ucs-bom,utf-8,default,latin1
  printoptions=paper:letter
  runtimepath=~/.vim,/var/lib/vim/addons,/usr/share/vim/vimfiles,/usr/share/vim/vim72,/usr/share/vim/vimfiles/af
ter,/var/lib/vim/addons/after,~/.vim/after
  suffixes=.bak,~,.swp,.o,.info,.aux,.log,.dvi,.bbl,.blg,.brf,.cb,.ind,.idx,.ilg,.inx,.out,.toc


---

### Post by l3ecl on 2010-10-14
i noticed i manually have to type set autoindent for it to work. howcome it is not automatically included in my .vimrc?

---

### Post by spjackson on 2010-10-15
> **l3ecl said:**
> i noticed i manually have to type set autoindent for it to work. howcome it is not automatically included in my .vimrc?
The only thimgs in my .vimrc is stuff I have put there. If you want to make the command permanent then add it to .vimrc

Where something is optional in vim, it almost always defaults to backwards compatible vi behaviour.

---

