---
title: "Vim handling of spaces"
date: 2005-12-15
forum: Programming Talk
---

### Post by rosslaird on 2005-12-15
On my ubuntu box, vim handles spaces between words in a particular way: if I type a sentence, then insert the cursor between two words, then type a new word, then hit the space key, the cursor jumps to the first letter of the next word. If I start typing another new word, it will be placed right after the first letter of the word that the cursor landed on. If I type a phrase, the word that I started ahead of slowly gets letters chopped off of it and added to the beginning of the new words I'm typing. The effect of this is that inserting words into a sentence requires that I use a specific strategy to get a single space between words:

word, spacebar, backspace

This can get annoying, as I am often inserting words into existing sentences. However, when I login to my website (on Dreamhost) and use vim on the server, it handles spaces differently. I can insert spaces as in a regular word processor. Text ahead of the cursor gets moved along nicely. I did read in the vim documentation that the cursor has to be on an actual character and not a space, which is why it jumps forward, but clearly vim doesn't have to work that way.

Any ideas on how I might get the spaces to work like on my server?

Thanks.
Ross

---

### Post by darth_vector on 2005-12-15
you may want to log onto your server and look at the .vimrc file in your home directory. if you copy that over to your home machine then you should get identical behaviour.

---

### Post by rosslaird on 2005-12-15
[QUOTE=darth_vector]you may want to log onto your server and look at the .vimrc file in your home directory. if you copy that over to your home machine then you should get identical behaviour.[/QUOTE]

That's a good idea.
However, there is no .vimrc file in my home directory on the server.
There is a .viminfo file, but it seems to just show history.
The space settings must be system wide.

---

### Post by darth_vector on 2005-12-15
the config file for vim in ubuntu can be found in /etc/vim/vimrc. have a look to see if that file exists on the server. are you running ubuntu on the server? it may be in a different place if you are using redhat/fedora or some other distro.

EDIT: failing that i will post my (default) /etc/vim/vimrc and ~/.vimrc

---

### Post by rosslaird on 2005-12-15
OK, found it on the debian server (in /etc/vim):

```
" Configuration file for vim
set runtimepath=~/.vim,/etc/vim,/usr/share/vim/vimfiles,/usr/share/vim/addons,/usr/share/vim/vim63,/usr/share/vim/vimfiles,/usr/share/vim/addons/after,~/.vim/after

" Normally we use vim-extensions. If you want true vi-compatibility
" remove change the following statements
set nocompatible        " Use Vim defaults instead of 100% vi compatibility
set backspace=indent,eol,start  " more powerful backspacing

" Now we set some defaults for the editor
set autoindent          " always set autoindenting on
" set linebreak         " Don't wrap words by default
set textwidth=0         " Don't wrap lines by default
set backupcopy=yes      " Keep a backup file
set viminfo='20,\"50    " read/write a .viminfo file, don't store more than
                        " 50 lines of registers
set history=50          " keep 50 lines of command line history
set ruler               " show the cursor position all the time

" Suffixes that get lower priority when doing tab completion for filenames.
" These are files we are not likely to want to edit or read.
set suffixes=.bak,~,.swp,.o,.info,.aux,.log,.dvi,.bbl,.blg,.brf,.cb,.ind,.idx,.ilg,.inx,.out,.toc

" We know xterm-debian is a color terminal
if &term =~ "xterm-debian" || &term =~ "xterm-xfree86"
  set t_Co=16
  set t_Sf=^[[3%dm
  set t_Sb=^[[4%dm
endif

" Make p in Visual mode replace the selected text with the "" register.
vnoremap p <Esc>:let current_reg = @"<CR>gvdi<C-R>=current_reg<CR><Esc>

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
" syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
" set background=dark

if has("autocmd")
 " Enabled file type detection  " Use the default filetype settings. If you also want to load indent files
 " to automatically do language-dependent indenting add 'indent' as well.
 filetype plugin on

endif " has ("autocmd")

" Some Debian-specific things
augroup filetype
  au BufRead reportbug.*                set ft=mail
  au BufRead reportbug-*                set ft=mail
augroup END

" Set paper size from /etc/papersize if available (Debian-specific)
try
  if filereadable('/etc/papersize')
    let s:papersize = matchstr(system('/bin/cat /etc/papersize'), '\p*')
    if strlen(s:papersize)
      let &printoptions = "paper:" . s:papersize
    endif
    unlet! s:papersize
  endif
catch /E145/
endtry

" The following are commented out as they cause vim to behave a lot
" different from regular vi. They are highly recommended though.
"set showcmd            " Show (partial) command in status line.
"set showmatch          " Show matching brackets.
"set ignorecase         " Do case insensitive matching
"set incsearch          " Incremental search
"set autowrite          " Automatically save before commands like :next and :make

" Source a global configuration file if available
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif
```

Nothing looks obviously related to spaces in the above. But I'm no expert...
Ideas?

And, just to make things more complicated, here's my ubuntu .vimrc:

```

" Set font
"   if has("gui_running")
"       if has("gui_gtk2")
"           set guifont=Bitstream\ Vera\ Sans\ Mono\ 12
"       elseif has("gui_kde")
"           set guifont=Bitstream\ Vera\ Sans\ Mono/12
"       elseif has("gui_x11")
"           set guifont=-*-lucidatypewriter-medium-r-normal-*-*-180-*-*-m-*-*
"       else
"           set guifont=Lucida_Console:x10:cDEFAULT
"       endif
"   endif 
"
set backup
set backupext=~ " extension for backup files
set undolevels=1000
set updatecount=200 " write swap file every 200 chars.
set updatetime=6000 " write swap file after 5 inactive secs.
set writebackup
set path=/home/ross/docs/office/writing/*
set guifont=Bitstream\ Vera\ Sans\ Mono\ 12
set lbr
set nocompatible
set incsearch " incremental search
set backspace=eol,start,indent
set ignorecase " ignore case in search
set encoding=utf-8 " unicode
set termencoding=utf-8
syntax on "syntax highlighting
set background=dark
set mouse=a
set mousemodel=extend
set digraph 
set scrolloff=10
set display=lastline
:colorscheme zenburn
" SpellCheck options
"highlight SpellErrors ctermfg=Red guifg=Red
"highlight SpellErrors guibg=Red guifg=Black
"   \ cterm=underline gui=underline term=reverse
" Cursor navigation keys
noremap <Up> gk
noremap! <Up> <C-O>gk
noremap <Down> gj
noremap! <Down> <C-O>gj
" The following are optional, to move by file lines using Alt-arrows
noremap! <M-Up> <Up>
noremap! <M-Down> <Down>
noremap <M-Up> k
noremap <M-Down> j
noremap <Space> <PageDown>
" Save keys
nmap <f2> :update<cr>
vmap <f2> <esc><f2>gv
imap <f2> <c-o><f2>
set visualbell
" Use kprinter
" set printexpr=system('kprinter'\ .\ '\ '\ .\ v:fname_in)\ .\ delete(v:" fname_in)\ +\ v:shell_error
" Use CTRL-F for saving the file
nmap <C-F> :update<CR>
vnoremap <C-F> <C-C>:update<CR>
inoremap <C-F> <C-O>:update<CR> 
" Typograpics
imap <leader>m -<BS>M
imap <leader>s '<BS>9
imap <leader>o "<BS>6
imap <leader>c "<BS>9
"moby-thesarus shortcut
nmap <F9> :!dict -d moby-thesaurus <cword><CR> 
" Cream multi-file replacement plugin
imap <C-F3> <C-o>:call Cream_replacemulti()<CR>
vmap <C-F3> :<C-u>call Cream_replacemulti()<CR>
nmap <C-F3> :call Cream_replacemulti()<CR>
"Maps Ctrl-tab & Ctrl-Shift-tab for buffer switching
nnoremap <C-Tab> :bnext<CR>
nnoremap <S-C-Tab> :bprevious<CR>
" Puts cursor at last position before closing.
au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$") |
                         \ exe "normal g'\"" | endif
" Cream line numbering plugin
vmap <silent> <F12> :<C-u>call Cream_number_lines("v")
"Gvim window geometry (Maximize upon open)
"winpos 0 25
":set lines=47
":set columns=156
"Dictionary (with Ctrl-n Ctrl-n shortcut)
set dict=/usr/share/dict/words
set complete-=k complete+=k
" Shortcuts for editing Movable Type journal using mtsend.py
" (T)emplate- reads in the template file
map #mtt :0r ~/docs/office/writing/mt.html<CR>:set filetype=html<CR>A
" (N)ew- posts new entry
map #mtn :w ~/docs/office/writing/!mtsend.py -N<CR>
" (G)et- retrieves latest post, enables HTML syntax highlighting
map #mtG :%!~/docs/office/writing/mtsend.py -q -G -<CR>:set filetype=html<CR>
" (g)et- retrieves specified post
map #mtg :%!~/docs/office/writing/mtsend.py -q -G 
" (E)dit- uploads new revision to latest post
map #mte :w !~/docs/office/writing/mtsend.py -E -<CR>
" (R)ebuild- rebuild specified entry
map #mtr :!~/docs/office/writing/mtsend.py -R 
" mpc control
imap <leader>n <C-O>:!mpc next<CR><CR>
" lookup word: dictionary or thesaurus
imap <leader>d <C-O>:!dict <cword>
imap <leader>t <C-O>:!dict -d moby-thesaurus <cword>
" Start spell highlighting
imap <leader>h <C-O>:highlight SpellErrors guibg=Red guifg=Black

```

---

### Post by darth_vector on 2005-12-15
[QUOTE=rosslaird]OK, found it on the debian server (in /etc/vim):Nothing looks obviously related to spaces in the above. But I'm no expert...
Ideas?[/QUOTE]

lol, neither am i. i think you will have to wait for a vi guru to pick this up...

---

### Post by David Marrs on 2005-12-16
can't really see anything in there that's not reasonable. Here's my vimrc:

```

" Configuration file for vim
set runtimepath=~/.vim,/etc/vim,/usr/share/vim/vimfiles,/usr/share/vim/addons,/usr/share/vim/vim63,/usr/share/vim/vimfiles,/usr/share/vim/addons/after,~/.vim/after

" Normally we use vim-extensions. If you want true vi-compatibility
" remove change the following statements
set nocompatible	" Use Vim defaults instead of 100% vi compatibility
set backspace=indent,eol,start	" more powerful backspacing

" Now we set some defaults for the editor 
" set autoindent	" always set autoindenting on
" set linebreak		" Don't wrap words by default
set textwidth=0		" Don't wrap lines by default 
set nobackup		" Don't keep a backup file
set viminfo='20,\"50	" read/write a .viminfo file, don't store more than
			" 50 lines of registers
set history=50		" keep 50 lines of command line history
set ruler		" show the cursor position all the time

" Suffixes that get lower priority when doing tab completion for filenames.
" These are files we are not likely to want to edit or read.
set suffixes=.bak,~,.swp,.o,.info,.aux,.log,.dvi,.bbl,.blg,.brf,.cb,.ind,.idx,.ilg,.inx,.out,.toc

" We know xterm-debian is a color terminal
if &term =~ "xterm-debian" || &term =~ "xterm-xfree86"
  set t_Co=16
  set t_Sf=[3%dm
  set t_Sb=[4%dm
endif

" Make p in Visual mode replace the selected text with the "" register.
vnoremap p <Esc>:let current_reg = @"<CR>gvdi<C-R>=current_reg<CR><Esc>

" Vim5 and later versions support syntax highlighting. Uncommenting the next
" line enables syntax highlighting by default.
" syntax on

" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
" set background=dark

if has("autocmd")
 " Enabled file type detection
 " Use the default filetype settings. If you also want to load indent files
 " to automatically do language-dependent indenting add 'indent' as well.
 filetype plugin on

endif " has ("autocmd")

" Some Debian-specific things
augroup filetype
  au BufRead reportbug.*		set ft=mail
  au BufRead reportbug-*		set ft=mail
augroup END

" Set paper size from /etc/papersize if available (Debian-specific)
try
  if filereadable('/etc/papersize')
    let s:papersize = matchstr(system('/bin/cat /etc/papersize'), '\p*')
    if strlen(s:papersize)
      let &printoptions = "paper:" . s:papersize
    endif
    unlet! s:papersize
  endif
catch /E145/
endtry

" The following are commented out as they cause vim to behave a lot
" different from regular vi. They are highly recommended though.
"set showcmd		" Show (partial) command in status line.
"set showmatch		" Show matching brackets.
"set ignorecase		" Do case insensitive matching
"set incsearch		" Incremental search
"set autowrite		" Automatically save before commands like :next and :make

" Source a global configuration file if available
if filereadable("/etc/vim/vimrc.local")
  source /etc/vim/vimrc.local
endif

```
Hopefully, replacing your current vimrc with that should do the trick. Make sure you don't have any setting set in your personal .vimrc either. Remember there's a separate gvimrc for gvim so, if you're using that, you may be looking at the wrong file.

At any rate, this isn't default behaviour, so you must have accidentally changed something at some point.

---

### Post by rosslaird on 2005-12-16
Progress: I have discovered that vim operates in the desired way if I switch to a different user on my own system. So it's not a global problem. And -- here's the weird part -- the problem seems unrelated to .vimrc or .gvimrc. Because when I remove those files the problem persists, but when I rename my .vim folder, the problem goes away.

So the problem is in the .vim folder for my default user, which has only a few things: various color schemes, scripts, and plugins. It has to be one of those. I suppose now it's a matter of selective removal until I find it...

Well, at least I'm halfway there.

Thanks for the help.

---

### Post by rosslaird on 2005-12-16
vimspell is the culprit.
Of course, it was the last thing I removed becaused it's the plugin I use most.
So any suggestions on a better spell checker?

---

### Post by rosslaird on 2005-12-16
engspchk works without causing any issues:

[http://www.vim.org/scripts/script.php?script_id=195](http://www.vim.org/scripts/script.php?script_id=195)

EDIT:

...except that it crashes vim after a while...

---

### Post by darth_vector on 2005-12-16
im quite a fan of ispell. its a command line tool, so it wont cause any problems to vim or any other editor.

---

### Post by rosslaird on 2005-12-16
I did find a workable spell checker inside vim ("SpellChecker"), and I also tried ispell from the command line. It worked pretty well (though I'll need to look into how I can use a larger dictionary, as I sometimes use arcane and archaic words).

Thanks for hanging in until I got this worked out.

Ross

By the way, here are the dictionaries I currently have installed on my system:

 gcide          The Collaborative International Dictionary of English v.0.48
 wn             WordNet (r) 2.0 (August 2003)
 jargon         Jargon File (4.4.4, 14 Aug 2003)
 vera           V.E.R.A. -- Virtual Entity of Relevant Acronyms (March 2005)
 devil          The Devil's Dictionary (1881-1906)
 elements       The Elements (07Nov00)
 easton         Easton's 1897 Bible Dictionary
 moby-thesaurus Moby Thesaurus II by Grady Ward, 1.0

---

