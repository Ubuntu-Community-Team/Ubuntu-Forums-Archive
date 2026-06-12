---
title: "Python mode for Gvim"
date: 2006-12-09
forum: Programming Talk
---

### Post by Somenoob on 2006-12-09
I know it's capable of python highlighting and syntax, but where and how? i've made several google searches but didin't find much helpful.

---

### Post by whoismilan on 2006-12-09
Either add "syntax on" to the startup settings (.vimrc), or enable it in the menus ("Syntax" > "on/off for This file" or "Automatic") should do it (I think, I'm new to vim myself...).

---

### Post by asimon on 2006-12-09
As a start look at /etc/vim/vimrc .
Especially at the lines 
```

syntax on
```
and
```

filetype indent on
```. They are commented out by default. You can either uncomment them and thus enable these features for every vim users or put them into your ~/.vimrc file.

Otherwise just type a colon, followed by "help python" to get help on vim's python mode. BTW, there is no need to install any extra packages. Vim already comes with the python mode. But you will have to install at least the 'vim' package, I think by default only the 'vim-tiny' package is installed, which is missing many features.

---

