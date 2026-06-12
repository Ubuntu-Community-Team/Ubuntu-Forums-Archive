---
title: "indentation vim and ruby"
date: 2006-11-01
forum: Programming Talk
---

### Post by jordilin on 2006-11-01
I've installed ruby-vim but it doesn't autoindent ruby code. Is there a way to autoindent code in vim using ruby?
thanks

---

### Post by jordilin on 2006-11-01
Solved, I have commented out the following in /etc/vim/vimrc
if has("autocmd")
  filetype indent on
endif
thanks anyway

---

### Post by hasimir44 on 2007-05-30
If anyone wants to set the size of the indent..  (I like 2 spaces..)

Add the following to /etc/vim/vimrc 

```
set sw=2 " no of spaces for indenting
set ts=2 " show \t as 2 spaces and treat 2 spaces as \t when deleting, etc..
```

Also uncomment this for highlighting: 

```
syntax on
```

---

