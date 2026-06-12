---
title: "Need a C++ editor!"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by Lazzarus on 2008-11-12
I looked at GCC but immediately became confused on how to install.

I'm using Ubuntu 8.10 if that info matters.

I don't care what the compiler is as long as it works. If someone could help me with the install process that'd be great.

---

### Post by markjensen on 2008-11-12
install gcc?

I'm not at my Linux box right now, but you can either do a
**sudo apt-get install gcc**
from a terminal, or open Synaptic and search "gcc" and click and install it from there.

Is that what you are after?   You said "editor", but your post seemed to not care about an editor, but instead a "compiler".

---

### Post by WRDN on 2008-11-12
If you're looking for a compiler only, then install gcc.

If on the other hand, you want an IDE (Integrated Development Environment), I would recommend either [Code Blocks]("http://www.codeblocks.org/") or [NetBeans]("http://www.netbeans.org/").

---

### Post by igknighted on 2008-11-12
The standard text editor (gedit in ubuntu, or kate in Kubuntu) has some terrific syntax highlighting and other features for developing in C/C++ (and many, many more languages).

---

### Post by binbash on 2008-11-12
jedit is cool

---

### Post by hessiess on 2008-11-12
Vim! Vim! Vim! :popcorn:

Compiler, install 'build-essential'

---

### Post by ibuclaw on 2008-11-12
For gcc/build essential tools.
[build-essential]("apt:build-essential")

If you require a library, install the "**-dev**" packages for that library.
ie: I've just written a perl module which interfaces with the libwiiuse library, to compile libwiiuse I required bluetooth headers.
**sudo apt-get install libbluetooth-dev**

A cool IDE for C/C++
[Code::Blocks]("apt:codeblocks")

A brilliant editor for writing code :D
[vim]("apt:vim")

If you don't like the console
[vim GTK]("apt:vim-gtk")

[EDIT]
A bit off topic, but I have the most useful bits of my ~/.vimrc file to show, should be enough to work with. (If you use spaces to indent lines, and not tabs :D)
```

syn on
set background=dark
set dir=/tmp
set nocompatible
"set nu
filetype indent on
set ic
set hls
set lbr
set nobackup
set incsearch
imap <Tab> <C-P>
imap <S-Tab> <C-N>

```

Though, this one here will probably do just as well. [http://lena.franken.de/linux/vim.html](http://lena.franken.de/linux/vim.html)

Regards
Iain

---

### Post by Lazzarus on 2008-11-12
I'm sorry I meant I needed a compiler that has the STL.

---

### Post by Lazzarus on 2008-11-12
OKAY I was able to just go to Add/Remove and search for C++ and found both netbeans and code blocks.

Thanks for the suggestions on programs though.

---

### Post by cmay on 2008-11-12
the gcc compiler is short for gnu compiler collection. there is all the things needed in that one package. so it is just [php]sudo apt-get install build-essentials.[/php]the c++ compiler is g++ and the c compiler is gcc.

---

### Post by cmay on 2008-11-12
> **Lazzarus said:**
> OKAY I was able to just go to Add/Remove and search for C++ and found both netbeans and code blocks.

Thanks for the suggestions on programs though.

i have posted just when you did it seems. ignore the above post by me as for now. as i think codeblocks drags the build-essential package into it. but the most problems i see whit hello world programs that wont compile is since people forget to install that package. 
sorry for being to late posting. i just did not see you had found the things you needed.
good luck

---

