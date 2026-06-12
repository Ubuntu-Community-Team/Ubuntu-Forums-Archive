---
title: "Crontab Opens in a Different Workspace"
date: 2010-03-16
forum: Programming Talk
---

### Post by navneeth on 2010-03-16
crontab -e opens the crontab two workspaces away. Could someone please tell me why something like this would happen and also what I can do to for it open in the current workspace?

---

### Post by navneeth on 2010-03-16
Okay, this no longer appears to be a problem with Crontab -- it's Vim that is opening in a new workspace when called. My .vimrc contains only basic stuff.

```
$cat .vimrc
colorscheme evening
set number
set autoindent
set tabstop=4
set shiftwidth=4
set smartindent
set lines=999
set columns=999
filetype indent on 
autocmd BufRead *.py set smartindent cinwords=if,elif,else,for,while,with,try,except,finally,def,class

```

---

