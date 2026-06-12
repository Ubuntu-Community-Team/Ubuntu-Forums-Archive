---
title: "[SOLVED] Vim not working properly in terminal"
date: 2008-12-18
forum: Programming Talk
---

### Post by helstreak on 2008-12-18
when I prompt vim in the terminal it will start but it won't type...yes I entered insert mode ;) also, it won't even display the text of a file.  all that it gives me is this crap when I try to type:

All                1,2
All                1,3
All                1,4


Anyone else have this problem?  Anyone know a good way to fix it?

here's my vimrc in case it helps:
syntax on
set smartindent
set autoindent
set nobackup
set nowritebackup
set noswapfile
set columns=90
set lines=40
set tabstop=4
set shiftwidth=4
set smarttab
filetype indent on
colorscheme murphy


thanks for the help :)

edit: forgot to mention this is ubuntu 8.04, gnome terminal

edit2:  found the problem...it was with "set columns=90"  it was freaking out because the column width was too wide for the terminal or something since the default is set at 80...just had to change the columns=80 and now it works. :)

---

### Post by kcode on 2008-12-18
Just tried your .vimrc. I dont think so there is any problem with it.

---

### Post by helstreak on 2008-12-18
> **kcode said:**
> Just tried your .vimrc. I dont think so there is any problem with it.

i didn't think there was a problem with it either, just put it up in case.  its odd that vim isn't working correctly :(

---

### Post by digitalvectorz on 2008-12-18
Did vim work prior to implementing that new vimrc?  Or is this the first time that you're testing it out since a reinstall or something?

---

### Post by helstreak on 2008-12-18
> **digitalvectorz said:**
> Did vim work prior to implementing that new vimrc?  Or is this the first time that you're testing it out since a reinstall or something?

if i take away the vimrc it works fine but then when i put back my settings it stops working....erg

---

### Post by digitalvectorz on 2008-12-18
try commenting out line after line in vimrc and rerun vim to find the culprit line?

---

