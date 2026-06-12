---
title: "Customizing vim"
date: 2006-12-02
forum: Programming Talk
---

### Post by yojimbosteel on 2006-12-02
I am currently using vim to edit and create fortran source files, and am happy with it for the most part.

There are two things I would like it two do however.
1. Auto indent do statements
2. Auto indent for less spaces

I am using filetype indent on to auto indent.
Here is my vimrc file, any advice
```
runtime! debian.vim

syntax on

set background=dark

if has("autocmd")
  filetype indent on
endif

set showcmd		" Show (partial) command in status line.
set showmatch		" Show matching brackets.
set ignorecase		" Do case insensitive matching
set smartcase		" Do smart case matching
set incsearch		" Incremental search
set hidden             " Hide buffers when they are abandoned
set mouse=a		" Enable mouse usage (all modes) in terminals

if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

au BufNew *.for let b:fortran_fixed_source=0    " set the correct value
```

---

### Post by Keffin on 2006-12-02
In answer to 1, if this is not automatically done then the (presumably fortran) syntax file is not fully complete. I could be wrong here, I don't know much about syntax files.

In answer to 2, by default the indent will be 1 (or more) tab. You can make a tab appear as e.g. 3 spaces using "set tabstop=3 shiftwidth=3".

Also you gave me a nice hint with "set mouse=a", cheers :).

---

### Post by yojimbosteel on 2006-12-02
Thanks for the help on my second question, works beautifully.

Does anyone know how to edit a syntax file or where I could get a better/updated fortran syntax?

---

### Post by po0f on 2006-12-02
yojimbosteel,

Try the [website](http://www.vim.org/)?

---

### Post by xtacocorex on 2006-12-02
Here is my complete .vimrc that we were given in my Aerospace Numerical Methods class where we programmed in FORTRAN.

I added the code for paste, but everything else is what I was given.
```

".vimrc file by Ash for aero361 2/6/03
" save this file in your $HOME dir as .vimrc
" Comment lines should precede by " (double quotes)
" Basic options frol user friendly vi setting have been set below
" Please modify as you get comfortable.a
" It is subject to revisions and improvements
" SWAP FILE ALERT !!
"       when this happens, it usually means that your editor crashed 
"       to recover the file type
"       vi -r filename

"set nocompatible

set backup                      " keep a backup file
set viminfo='20,\"50            " read/write a .viminfo file, don't store more
                                                  " than 50 lines of registers
set history=50                  " keep 50 lines of command line history
set ruler                       " show the cursor position all the time
set nu
set bs=2                        " always backspace
set fo=cqrt                     " smart formatting of comments
set hlsearch                    " Highlihting the last used search pattern

"set shiftwidth=4
set tabstop=8
set smarttab
set smartindent                 " Indent in smart fashion
set autoindent
set sm                          " automatic matching braces

set mouse=a                     " Use the mouse in all modes
set mousemodel=popup            " Turn on the popup menu
set mousefocus                  " Use the mouse to focus windows
set mousehide                   " Hide the mouse cursor when the user types
set selectmode=mouse,key,cmd  " Use both mouse and shift keys to select

set pastetoggle=<F10>
set ai bg=dark bs=2 ls=2 lz mls=1 ru sw=8 shm=at so=2 nosol

if has("syntax")
  syntax on                      " Syntax highlighting off
endif

set smartindent                 " Indent in smart fashion
set sm                          " automatic matching braces
                                " set sm        ---> switch on brace matching
                                " set nosm      ---> switch off brace matching
set wildmenu                    " Wild menu option is on
set showmode
set showcmd
set wrapmargin=10

set cmdheight=3                 "command height change

"set dir=~/vi_swap              " swap directory

:let fortran_have_tabs=1
:let fortran_free_source=1
:let fortran_fixed_source=1

function! Paste(mode)
  if a:mode == "v"
    normal gv
    normal "+P
    normal l
  elseif a:mode == "i"
    set virtualedit=all
    normal `^"+gP
    let &virtualedit = ""
  endif
endfunction

vnoremap <C-X> "+d
vnoremap <C-C> "+y
nnoremap <C-V> "+gPl
vnoremap <C-V> :<C-U>call Paste("v")<CR>
inoremap <C-V> <C-O>:call Paste("i")<CR>

```

---

### Post by yojimbosteel on 2006-12-03
Okay, so I found this great website for fortran syntax and indent files:

[http://www.unb.ca/fredericton/science/chem/ajit/syntax/fort60.htm](http://www.unb.ca/fredericton/science/chem/ajit/syntax/fort60.htm)
(It has links to the indentation information at the bottom.)

The only problem is that I can't get do loop indents on.

---

