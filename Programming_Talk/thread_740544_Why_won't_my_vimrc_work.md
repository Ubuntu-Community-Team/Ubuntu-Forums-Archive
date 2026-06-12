---
title: "Why won't my vimrc work?"
date: 2008-03-30
forum: Programming Talk
---

### Post by days_of_ruin on 2008-03-30
```
" An example for a vimrc file.
"
" Maintainer:	Bram Moolenaar <Bram@vim.org>
" Last change:	2002 Sep 19
"
" To use it, copy it to
"     for Unix and OS/2:  ~/.vimrc
"	      for Amiga:  s:.vimrc
"  for MS-DOS and Win32:  $VIM\_vimrc
"	    for OpenVMS:  sys$login:.vimrc

" When started as "evim", evim.vim will already have done these settings.
if v:progname =~? "evim"
  finish
endif

" Use Vim settings, rather then Vi settings (much better!).
" This must be first, because it changes other options as a side effect.
set nocompatible

" allow backspacing over everything in insert mode
set backspace=indent,eol,start

if has("vms")
  set nobackup		" do not keep a backup file, use versions instead
else
  set backup		" keep a backup file
endif
set history=50		" keep 50 lines of command line history
set ruler		" show the cursor position all the time
set showcmd		" display incomplete commands
set incsearch		" do incremental searching

" For Win32 GUI: remove 't' flag from 'guioptions': no tearoff menu entries
" let &guioptions = substitute(&guioptions, "t", "", "g")

" Don't use Ex mode, use Q for formatting
map Q gq

" This is an alternative that also works in block mode, but the deleted
" text is lost and it only works for putting the current register.
"vnoremap p "_dp

" Switch syntax highlighting on, when the terminal has colors
" Also switch on highlighting the last used search pattern.
if &t_Co > 2 || has("gui_running")
  syntax on
  set hlsearch
endif

" Only do this part when compiled with support for autocommands.
if has("autocmd")

  " Enable file type detection.
  " Use the default filetype settings, so that mail gets 'tw' set to 72,
  " 'cindent' is on in C files, etc.
  " Also load indent files, to automatically do language-dependent indenting.
  filetype plugin indent on

  " Put these in an autocmd group, so that we can delete them easily.
  augroup vimrcEx
  au!

  " For all text files set 'textwidth' to 78 characters.
  autocmd FileType text setlocal textwidth=78

  " When editing a file, always jump to the last known cursor position.
  " Don't do it when the position is invalid or when inside an event handler
  " (happens when dropping a file on gvim).
  autocmd BufReadPost *
    \ if line("'\"") > 0 && line("'\"") <= line("$") |
    \   exe "normal g`\"" |
    \ endif

  augroup END

else

  set autoindent		" always set autoindenting on

endif " has("autocmd")

set hidden
set textwidth=75      
set autoindent        
set tabstop=4        
set expandtab        
set autoindent	
set shiftwidth=4      
filetype indent on

```
I added most of the last few lines to make it python friendly but 
it doesn't work.
If I do and if statement or any of the keywords it correctly indents
but only if the if statement is not indented at all.

---

### Post by days_of_ruin on 2008-03-30
if anyone has one that works for python care to share?

---

### Post by mssever on 2008-03-30
I'm no expert in .vimrc files, but mine works just fine for Python, IMHO. Here it is (some of the settings specifically apply to gvim):
```
version 6.0
if &cp | set nocp | endif
let s:cpo_save=&cpo
set cpo&vim
map! <xHome> <Home>
map! <xEnd> <End>
map! <S-xF4> <S-F4>
map! <S-xF3> <S-F3>
map! <S-xF2> <S-F2>
map! <S-xF1> <S-F1>
map! <xF4> <F4>
map! <xF3> <F3>
map! <xF2> <F2>
map! <xF1> <F1>
map <xHome> <Home>
map <xEnd> <End>
map <S-xF4> <S-F4>
map <S-xF3> <S-F3>
map <S-xF2> <S-F2>
map <S-xF1> <S-F1>
map <xF4> <F4>
map <xF3> <F3>
map <xF2> <F2>
map <xF1> <F1>
let &cpo=s:cpo_save
unlet s:cpo_save
set backspace=indent,eol,start
set fileencodings=ucs-bom,utf-8,latin1
set encoding=utf8
set fileencoding=utf8
set helplang=en
set history=50
set printoptions=paper:letter
set ruler
set runtimepath=~/.vim,/usr/share/vim/addons,/usr/share/vim/vimfiles,/usr/share/vim/vimcurrent,/usr/share/vim/vimfiles/after,/usr/share/vim/addons/after,~/.vim/after
set showcmd
set suffixes=.bak,~,.swp,.o,.info,.aux,.log,.dvi,.bbl,.blg,.brf,.cb,.ind,.idx,.ilg,.inx,.out,.toc
set viminfo='20,\"50
syntax on
set scrolloff=5
set mouse=a
set autoindent
set number
set hlsearch
"set cursorline
"set cursorcolumn
highlight CursorLine term=reverse cterm=reverse guibg=Grey90
set nojoinspaces
set tabstop=4
set shiftwidth=4
set smarttab
set expandtab
set copyindent
```

---

### Post by ssavelan on 2009-03-15
[http://svn.python.org/projects/python/trunk/Misc/Vim/vimrc]("http://svn.python.org/projects/python/trunk/Misc/Vim/vimrc")

and also see [this]("http://www.vim.org/scripts/script.php?script_id=1494")

The only thing that I don't really like about just following these two out of the box is that my <c-C> <c-V> don't really work that good and mess up the indentation when I paste into vim.  I'm working on this issue right now...

---

### Post by geirha on 2009-03-15
Add ```
runtime! debian.vim
``` to the start of vimrc. This, amonst others, sets the correct paths for vim to search for syntax and indenting files.

---

### Post by days_of_ruin on 2009-03-15
Not sure why this was bumped but I don't have any problems with this anymore.

---

