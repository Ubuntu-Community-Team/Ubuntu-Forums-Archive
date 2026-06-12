---
title: "What's your vim setup?"
date: 2008-08-26
forum: Programming Talk
---

### Post by memories on 2008-08-26
I have been using vim to code C for years, and while I know a lot (but not enough), it simply isn't cutting it for web development.

I want a full screen vim (or gvim) with a file explorer on the left, tabs (in a buffer, not GUI tabs), and a small "preview" or status buffer on the bottom, where I can map a key to run tests and have the output appear in the bottom buffer. I'd also like taglist open beneath the explorer.

I know this is do-able, and I've done it, but it's not usable. The main problem is when I open something in the explorer, it opens a new buffer instead of opening a new tab. If I switch tabs after this, then the tab buffer gets duplicated. 

It's all weird problems like this. Is there a certain order I need to source/enable the plugins in?

Anyway, does anyone have any tips?

Plugins:
 bufexplorer
 taglist
 minibufexp
 rails.vim
 Project (though I've never used this) 
 snippetsEmu

I need help setting all of these up! How do you do it?

---

### Post by monkeyking on 2008-08-26
I've been using vim for years,
but I never got the indent to work properly.

So if I need to edit huge amounts of code,
I use emacs.
If I just need to change small things I use vim.

Did you ever get the indent to work?

---

### Post by samjh on 2008-08-26
> **monkeyking said:**
> I've been using vim for years,
but I never got the indent to work properly.

So if I need to edit huge amounts of code,
I use emacs.
If I just need to change small things I use vim.

Did you ever get the indent to work?

To indent a single line, use ">>" to indent and "<<" to un-indent.

To indent a block of code:
1. Hit "V" for visual mode.
2. Use your arrow keys to select the block of code to indent.
3. Hit ">>" to indent, and "<<" to un-indent.
4. Hit "Esc" to return to command mode.

For me, I use nautilus-open-terminal plugin to open a vim session in any directory I want, and nautilus itself to browse files.  In Gnome-terminal, I have two tabs: one for vim and one for the command-line in the source directory.  To switch between tabs, use Shift-PgUp/PgDn.

My vim config:
```
:set nu
:set ts=4
:set sw=4
:syntax on
:filetype plugin indent on
```Simple and useful.

I know this doesn't answer the OP, but hopefully it may be helpful to other users.

---

### Post by memories on 2008-08-26
Thanks for the replies. 

If by indent you mean auto indent (i.e., type "if" and press enter), yes I've gotten that to work. I don't remember how, I've been using the same vimrc for years.. I just append to it from time to time. 

> " Enable 256bit color for console vim. Default is 8 bits.. most themes require a lot more.. 16-256.
set t_Co=256
set background=dark
colors desert

" Automatically detect filetypes
filetype plugin indent on  

set guifont=Anonymous\ 14

set ruler               " Ruler on
set nu                  " Line numbers on
set nocompatible        " no vi compatibility (more features)
set nowrap " Disable line wrap. Will set on per-file basis
set clipboard+=unnamed  " Yanks go to clipboard.
set history=256         " Number of things to remember in history. 
set timeoutlen=220      " recommended. Otherwise there's a delay when you press escape

set expandtab
set tabstop=2   
set bs=2  
set shiftwidth=2 
set autoindent
set smarttab

" Switch to the directory of open file 
autocmd BufEnter * lcd %:p:h

" These two remove annoying blinking and noise
set novisualbell
set noerrorbells 

" Always show the status line
set laststatus=2


" This next line isn't for everyone. It adds a $ to the end of each line, and replaces trailing spaces with ~. This is useful because you will be able to see whitespace, and it won't affect your programming. So in Ruby for instance, here's how hello world would look:

require 'something'~$ 
puts 'hey werld'~~$ 
~$

That shows that I have 1 space after the require line, 2 spaces after the puts line and the last line in the file has 1 space before it ends ($). 
These obviously don't get compiled with the code, they are automatic and just for the programmer.

set lcs=tab:\ \ ,eol:$,trail:~,extends:>,precedes:<


I also have the following for specific languages.. here's one:
" Language::C
autocmd BufNewFile *.c,*.C source ~/.vim/configs/c
autocmd BufNewFile *.c,*.C 0r ~/.vim/skeleton.c

The first line inherits all the settings in "programming" because I use vim for everything, but prefer different settings for programming and doing other work. 
For example, for configs/c I might have:

" These are formatting/indent options for C/C++
set nocp incsearch
set cinoptions=:0,p0,t0
set cinwords=if,else,while,do,for,switch,case
set formatoptions=tcqr
set cindent


The second line sets up a skeleton if I create a new file with the specified extension. 
So for C files (*.c or *.C) it adds #includes and int main() { } - 
For sh I just have #!/bin/sh 
For python it adds def main(): ... if '__name__'==__main__ etc.

I also have some mappings, some for specific languages, some general. i.e., 

" F2 toggles taglist window 
nnoremap <silent> <F2> :TlistToggle<CR>

" F4 and shift-F4 toggle spell check on/off
map <F4> <Esc>:setlocal spell spelllang=en_us<CR>
map <S-F4> <Esc>:setlocal nospell<CR>

... etc. Hope this helps you guys.

---

### Post by samjh on 2008-08-26
Well, auto-indent is just: **:set autoindent**

But this will set indenting according to filetype: **:filetype indent on** and **:filetype plugin indent on** will switch on both fileytype plugins and indenting.

---

### Post by dribeas on 2008-08-26
> **samjh said:**
> To indent a single line, use ">>" to indent and "<<" to un-indent.

To indent a block of code:
1. Hit "V" for visual mode.
2. Use your arrow keys to select the block of code to indent.
3. Hit ">>" to indent, and "<<" to un-indent.
4. Hit "Esc" to return to command mode.


Or instead of manually using '<<' and '>>' press '=' which will indent automatically the block (according to whatever your current indent options are selected, I use cindent)

So my settings:
```

set bg=light
syn on

set cindent ts=4 sw=4

set laststatus=2
set winminheight=0
au VimEnter * set winheight=999 

map gf ^[:sf<cfile>^M

```

I always force a light terminal with syntax on. Default cindent is fine with me (and my company's coding style rules for C++), I prefer a 4 space wide tab indentation and horizontal scroll size.

As I usually horizontally split the window, I want the status line to be always on (two lines). Non selected splits get the least screen size available (0), and the selected window [*] gets as much screen real state as possible.

Finally, whenever I press 'gf' over a file name, I want vi to locate the header file within the directory/subdirectories and default path.

How do I work? screen+vi.

   David


[*] winheight is set to 999 with an autocommand to work around a (officially unrecognized) when opening multiple files from the command line, if winheight was set to 999 in config, only 2 files can be split opened from the command line.

---

### Post by monkeyking on 2008-08-26
by autoindentation I mean emacs style indentation :)

[PHP]
#include <iostream>
int main(){
for (int i=0;i<var;i++)
         if(p!=NULL)
printf("notnull\")
        else
printf("isnull\")
}
[/PHP]

In my emacs, I would simply put the curser on each line,
and press tab, and then it would be aligned according to the scope of the operators.

---

### Post by raul_ on 2008-08-26
Also, selecting a block of text and pressing "=" it will make your code pretty, like magic

---

