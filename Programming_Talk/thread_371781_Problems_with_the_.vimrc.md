---
title: "Problems with the .vimrc"
date: 2007-02-27
forum: Programming Talk
---

### Post by ewo on 2007-02-27
Dear Users,

I had for quite a long time now problems with my vimrc.

When I use the vimrc_example.vim and rename it I have the following problems:
- syntax isn´t switched on automatically, also when I type :syntax on with a open perl file it isn´t activated I have to typ syn=perl to get the syntax highlight
(when I want to switch between different  languages that is quite uncomfortable)
(btw.: filetype plugin and indent is on)

When I make a short vimrc on my own the syntax highlight is o.k., but I have with both vimrc the problem, that shortcuts doesn´t work.

When I put this in the vimrc
map <F3> :Tlist<CR>
The computer just makes an error sound when I press <F3> also when I press <F1> (normally the vimhelp should displayed) I geht the Gnome Terminal Help, maybe the terminal overwrites the keymappings or doesnt allow it?

Here are my different vimrc´s

vimrc

filetype plugin on
syntax on
set number

" This is for taglist
let Tlist_Inc_Winwidth = 0
map <F3> :Tlist<CR>


vimrc_example.vim

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


Also another probleme is that when I put

" Use perl compiler for all *.pl and *.pm files.
autocmd BufNewFile,BufRead *.p? compiler perl

in my vimrc and type :make to run a perl script it says that it found no targets.

Greetings and thanks for help,
ewo

---

### Post by hellraiser_rob on 2007-02-27
Did you install the full version of vim, or are you using the lite version which some by default

apt-get install vim

---

### Post by ewo on 2007-02-27
> **hellraiser_rob said:**
> Did you install the full version of vim, or are you using the lite version which some by default

apt-get install vim

I have installed the full version of vim and also removed and reinstalled it.

I also tried to test to extract the vim runtime from vim.org but this seems to make no difference.

Is it normal, that when I type apt-get remove vim the files doesn´t seem to go away in the /usr/share/vim the console link to ,vim' is destroyed but I can´t see that the vim files are removed.

ewo

By the way: When I want to answer somethink Firefox redirects me automatically before I can type anthing and I have to push the stop button... mh?

---

### Post by yigal.weinstein on 2007-03-07
first off your vimrc file is scary.  It might be the default but with I don't know how many lines of code I would be running from that configuration.

I think your problem simply lies with defining the extensions as a type of file.  That is you need to tell vim that .pl is a perl file .tex is a tex file.  However, it should recognize it automatically except for certain esoteric extensions.  So here's what I am going to do here is a stripped down vimrc file.  Please use it and tell me what kind of results you have,

filetype plugin on
filetype indent on
syntax enable
set mouse=a
set mousem=popup
set nu!
set lbr!
au BufRead,BufNewFile *.mac set filetype=maxima

It is so small, beautiful, that I am not going to use it as an attachment.  You see the first line, and 3rd line if vim is not using these options this could easily be your problem,

best

---

### Post by shawnhcorey on 2007-03-11
> **ewo said:**
> Dear Users,

I had for quite a long time now problems with my vimrc.

When I use the vimrc_example.vim and rename it I have the following problems:
- syntax isn´t switched on automatically, also when I type :syntax on with a open perl file it isn´t activated I have to typ syn=perl to get the syntax highlight
(when I want to switch between different  languages that is quite uncomfortable)
(btw.: filetype plugin and indent is on)

When I make a short vimrc on my own the syntax highlight is o.k., but I have with both vimrc the problem, that shortcuts doesn´t work.


Try changing the syntax line from 'syntax on' to:

:syntax enable

Other things you can try:

:syntax default

:syntax reset

  -- shc

---

