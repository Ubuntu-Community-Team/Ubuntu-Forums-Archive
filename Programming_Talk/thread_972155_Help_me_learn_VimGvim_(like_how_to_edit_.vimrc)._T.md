---
title: "Help me learn Vim/Gvim (like how to edit .vimrc). Thanks!"
date: 2008-11-05
forum: Programming Talk
---

### Post by _Atreides_ on 2008-11-05
Hey guys I am trying to learn Gvim (vim basically) but the problem is I cant find many good guides. I just naturally suck at google-fu. Topics i really would like covered are features of vim that would be helpful to a programmer, especially also what to actually keep in my .vimrc file, because i can find absolutely no guides on how to customize this. Thanks!:popcorn:

---

### Post by jimi_hendrix on 2008-11-05
laroza has a vim guide in her wiki...but nothing with .vimrc

---

### Post by GarudaReiga on 2008-11-05
I think you can google with ".vimrc programming" or ".vimrc c++" if you are using c++, and you will find some information useful for you.

Besides, you can download some plugins such as Tlist, which may be very helpful.

---

### Post by geirha on 2008-11-05
Look at the global vimrc file /etc/vim/vimrc. It explains what alot of the options do. Either edit it as root, to affect all users' vim, or copy it to ~/.vimrc and edit your local copy to your needs.

---

### Post by jimi_hendrix on 2008-11-05
@OP

i really like the quote in your sig...wheres that from (i heard it somewhere and cant remember) </OT>

---

### Post by ad_267 on 2008-11-05
Run in the terminal: vimtutor

That won't help with customising your .vimrc, but it will help you learn how to use vim.

---

### Post by _Atreides_ on 2008-11-05
Its from the book Dune by Frank Herbert. There are also sequels and prequels by his son. My favorite book!

---

### Post by _Atreides_ on 2008-11-05
hmmm well i keep finding a lot of guides on how to actually use vim like keystrokes and stuff like that but no one seems to have a guide to editing .vimrc .... is there something else people use to have their settings or what? Im actually suprised everyone is either emacs or vi but i cant find any guides for vim...

---

### Post by ConMan318 on 2008-11-05
This is my .vimrc:
```

syntax on
set number
set tabstop=4
set shiftwidth=4
set expandtab
set softtabstop=4
colorscheme darkblue
set nocompatible
set showmatch

```


With comments to show what each line does:
```

syntax on  //turns on programming syntax for the language you're writing in
set number  //displays line numbers
set tabstop=4  //tabstop is 4 spaces
set shiftwidth=4  //forget what this does, match the number to the above line though i think
set expandtab  //expand tab to spaces
set softtabstop=4  //i think this allows backspacing of tabs even though they're expanded
colorscheme darkblue  //my favorite color scheme for gvim :)
set nocompatible  //turns off compatibility mode, you should still install the full version and remove vim-tiny
set showmatch  //highlight matching parens

```

I don't know much more than this as far as .vimrc editing goes, but stick whatever is useful to you in yours.  I just add to it whenever I come across something new that I think would be useful.

---

### Post by _Atreides_ on 2008-11-05
Thanks this should definately help get me started!

---

### Post by ad_267 on 2008-11-05
Another option I have is "set cindent" which automatically uses C style indentation.

---

