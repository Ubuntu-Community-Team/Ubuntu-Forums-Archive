---
title: "text editor with automatic indentation?"
date: 2010-03-28
forum: Programming Talk
---

### Post by superarthur on 2010-03-28
I've been looking for a text editor with automatic indentation.
by that I mean if I click enter after "{", the next line would be indented, and when I type "}", the line would be automatically deindented.
I selected "enable automatic indentation" in gedit, but all it does is to continue indenting my lines after my first indentation. (it doesn't detect the brackets and indent automatically)

When I am on Windows, Crimson Editor does exactly what I want.
When I tried vim on windows, it does what I want as well, but it's not the case when I installed vim on ubuntu.

Are there any text editor that comes with automatic indentation? Or is there a way to make Vim do what I want?

---

### Post by Barriehie on 2010-03-28
I just did this in VIM and it worked like you're describing, I think.  I did this before loading the file, don't know what it does if you load the file first...
```

:set autoindent
:set smartindent
```
then I loaded a .cpp file and it put the braces where they're supposed to go.  I think the default *tab* is 8 and you can change that:
```

set ts=some_number
```

HTH

Edit: You can put those commands in your ~/.vimrc file!

---

### Post by jpkotta on 2010-03-29
In Emacs, you can do this with C-j, or rebind it to <return> with
```
(global-set-key (kbd "<return>") 'newline-and-indent)
```
Emacs computes how much to indent based on the surrounding text (many modes offer extensive customization of this).  You can also tell it to indent with spaces or tabs (indent-tabs-mode) and set how big tabs are (tab-width).  See also [http://www.emacswiki.org/emacs/SmartTabs](http://www.emacswiki.org/emacs/SmartTabs).

---

### Post by superarthur on 2010-03-29
> **Barriehie said:**
> I just did this in VIM and it worked like you're describing, I think.  I did this before loading the file, don't know what it does if you load the file first...
```

:set autoindent
:set smartindent
```then I loaded a .cpp file and it put the braces where they're supposed to go.  I think the default *tab* is 8 and you can change that:
```

set ts=some_number
```HTH

Edit: You can put those commands in your ~/.vimrc file!
Thanks.
It seems that just :set smartindent is alright for me.
Where is the ~/.vimrc file?

---

### Post by kamaji792 on 2010-03-29
**~** === **/home/<user-name>**

So the .vimrc is in:

**/home/<user-name>/.vimrc**

But to edit it:
```
vim ~/.vimrc
```

**vim** is good :D  Mad, but good ;)

---

### Post by geirha on 2010-03-29
If you don't have a ~/.vimrc file yet, then

```

cp /etc/vim/vimrc ~/.vimrc
vim ~/.vimrc

```

---

### Post by Barriehie on 2010-03-29
The **.vimrc** file is where you can customize it's settings and behaviour.  Coming from using emacs for decades I'm finding vim faster and more understandable, it's worth the initial learning curve!  I've been using vim for a few days now and it's great!  I took the leap and removed my emacs files, kept the .emacs though for posterity...

Below is my ~/.vimrc and my plugin files.  The ~/.vimrc file is as posted above and I add/delete from it.  You can find out more about vim at the VimTips Wiki: [http://vim.wikia.com/wiki/Vim_Tips_Wiki](http://vim.wikia.com/wiki/Vim_Tips_Wiki)

What's cool too is you can launch vim in server mode and add a custom app. to your file browser to open a file in the server so you've only got one instance of vim running, accessable from everywhere.  I launch it when I need to edit and then it gets minimized.  

[color="green"]~/.vimrc[/color]
```

if v:progname =~? "evim"
  finish
endif

"
"  My settings here. 
"  Saturday March 27, 2010
"
" Show line numbers.
set number

" Set the backup directory
set backupdir=~/vim/backup

"  Auto SheBang
augroup Shebang
  autocmd BufNewFile *.sh 0put =\"#!/bin/bash\<nl>\##\<nl>\## Script by Barrie Hiern\<nl>##\"|$
    autocmd BufNewFile *.awk 0put =\"#!/usr/bin/gawk\<nl>\##\<nl>\## Script by Barrie Hiern\<nl>##\"|$
augroup END

" Syntax highlighting
syntax on

" Change buffers without saving
set hidden

" Put a line under the cursor
set cursorline

" Set the color scheme
colorscheme darkblue

" Source my plugins...  (some from the net / some from me)
so ~/vim/plugins/myfiletypes.vim
so ~/vim/plugins/sudo.vim

set autoindent
set smartindent
set ts=2							" Set tab width = 2



"
"  End of my customizations
"


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


" Don't use Ex mode, use Q for formatting
map Q gq

" In many terminal emulators the mouse works just fine, thus enable it.
set mouse=a

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
    \   exe "normal! g`\"" |
    \ endif

  augroup END

else

  set autoindent		" always set autoindenting on

endif " has("autocmd")

" Convenient command to see the difference between the current buffer and the
" file it was loaded from, thus the changes you made.
"command DiffOrig vert new | set bt=nofile | r # | 0d_ | diffthis
"	 	\ | wincmd p | diffthis

```

[color="green"]myfiletypes.vim[/color]
```

"
" *************************************************************
" Filename : $HOME/vim/plugins/myfiletypes.vim
" See the document by typing :help autocmd within vim session
" see also the doc at /usr/share/vim/doc/autocmd.txt
" This file will setup the autocommands for new filetypes 
" using the existing syntax-filetypes.
" For example when you open foo.cpp it will use syntax of cpp
" Basically does :set filetype=cpp inside vim
" Add a line in $HOME/.vimrc as below:
" so $HOME/vim/plugins/myfiletypes.vim
"
" *************************************************************
augroup filetype
        au!
        au! BufRead,BufNewFile *.php    set filetype=php
        au! BufRead,BufNewFile *.html   set filetype=html
        au! BufRead,BufNewFile *.cpp    set filetype=cpp
augroup END

```

[color="green"]sudo.vim[/color]
```

"
"
"	sudo.vim:  A vim plugin by Rich Paul (vim@rich-paul.net)
"	
"	This script eases use of vim with sudo by adding the ability to
"	edit one file with root privleges without running the whole 
"	session that way.
"
"
"	Usage:  put it in the plugin directory, and
"			(command line): vim sudo:/etc/passwd
"			(within vim):   :e sudo:/etc/passwd
"
"		sudo will ask for your password if need be.
"	Requires:
"		sudo package installed
"		decent OS (sorry, no windows, unless cygwin has sudo now?)
"	Provides:
"		URL handler, sudo: scheme
"		2 autocommands
"		
"	Commands:
"		SudoRead
"		SudoWrite
"	ToDo:
"		Allow one to sudo to users other than root.
"		Quote the file name better.
"


if exists("s:seen") && !exists("s:debug")
	finish
endif
let s:seen=1
"let s:debug=1
function! SudoRead(url)
	if a:url=="<afile>"
		let file=expand(a:url)
	else
		let file=a:url
	endif
	let prot=matchstr(file,'^\(sudo\)\ze:')
	if '' != prot
		let file=strpart(file,strlen(prot)+1)
	endif
	:0,$d
	call setline(1,"foo")		
	exec '1read !sudo cat "'.file.'" '
	:1d
	set nomod
	:filetype detect
endfunction
function! SudoWrite (url) abort
	if a:url=="<afile>"
		let file=expand(a:url)
	else
		let file=a:url
	endif
	let prot=matchstr(file,'^\(sudo\)\ze:')
	if '' != prot
		let file=strpart(file,strlen(prot)+1)
	endif
	set nomod
	exec '%write !sudo tee >/dev/null "'.file.'"'
endf
command! -nargs=1 SudoRead call SudoRead(<f-args>)
command! -nargs=1 SudoWrite call SudoWrite(<f-args>)
augroup Sudo
	autocmd!
	au BufReadCmd	sudo:*,sudo:*/* SudoRead <afile>
	au FileReadCmd	sudo:*,sudo:*/* SudoRead <afile>
	au BufWriteCmd	sudo:*,sudo:*/* SudoWrite <afile>
	au FileWriteCmd	sudo:*,sudo:*/* SudoWrite <afile>
augroup END

```

---

### Post by Lux Perpetua on 2010-03-29
> **superarthur said:**
> Thanks.
It seems that just :set smartindent is alright for me.I could be wrong, here, but I think what you really want is **:set cindent**. smartindent probably works, too; I don't know exactly what the differences are.

---

### Post by Compyx on 2010-03-29
`cindent' is preferred over `smartindent' since it's stricter and more tailored towards C, hence the 'c' in 'cindent' :)
cindent is enabled by default when entering a buffer with C code, according to the Vim manual.

Some more info can be found [here]("http://vim.wikia.com/wiki/Indenting_source_code#.27smartindent.27_and_.27cindent.27") or by using the commands :help cindent and :help smartindent.

---

### Post by superarthur on 2010-03-29
thank you compyx. that's a useful page.

another problem is that I am too used to save by control-s
it is much slower for me to esc -> : -> w -> enter

---

### Post by Barriehie on 2010-03-29
> **superarthur said:**
> another problem is that I am too used to save by control-s
it is much slower for me to esc -> : -> w -> enter

I'm sure that can be remapped; let me dig!

---

### Post by Barriehie on 2010-03-29
I'm finding out way to much about key mapping!  I've found some examples but their for windows.  I did manage to get it to work using F8 but I hear you on the ESC key, I need an audio triggered one...  I'll keep digging.

---

### Post by Barriehie on 2010-03-29
> **superarthur said:**
> thank you compyx. that's a useful page.

another problem is that I am too used to save by control-s
it is much slower for me to esc -> : -> w -> enter

Okay, I've got save mapped to 'S' while in command mode and then it takes you back to insert mode.  I know there's a way to do it while in -insert- but I've not found it yet.  So, to save you hit ESC and then S and you're back in insert mode.  That's a capital S.

```

:map S :w<cr>i
```

---

### Post by superarthur on 2010-03-30
> **Barriehie said:**
> Okay, I've got save mapped to 'S' while in command mode and then it takes you back to insert mode.  I know there's a way to do it while in -insert- but I've not found it yet.  So, to save you hit ESC and then S and you're back in insert mode.  That's a capital S.

```

:map S :w<cr>i
```
thanks. i am at my uni now. i will try it when i boot in ubuntu at home. :)

---

