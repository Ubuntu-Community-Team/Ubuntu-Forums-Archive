---
title: "vim keymappings"
date: 2011-04-27
forum: Programming Talk
---

### Post by cybo on 2011-04-27
i'm somewhat new to vim scripting

i'm trying to map my makefile commands but for some reason nothing happens. i would appreciate any help in explaining why. here are the commands

nmap <S-F9>:cd src<CR>:make clean<CR>
nmap <S-F10>:cd src<CR>:make all<CR>
nmap <S-F11>:cd src<CR>:make rebuild<CR>
nmap <S-F12>:cd src<CR>:make final<CR>

any help is appreciated

---

### Post by DaithiF on 2011-04-27
Hi, as it says in vim's help for nmap, the format is:
```
:nmap {lhs} {rhs}
```
you don't seem to have a space between your keymap (<S-F9>) and the command it maps to

---

### Post by cybo on 2011-04-27
yep, that did it. thanks.

---

