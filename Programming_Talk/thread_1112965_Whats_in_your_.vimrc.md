---
title: "Whats in your .vimrc?"
date: 2009-04-01
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-04-01
well post them! and give a simple explanation if you want

---

### Post by hessiess on 2009-04-01
```

colorscheme desert
set guioptions-=T

set showtabline=0

set spell

set shiftwidth=4
set softtabstop=4

map <C-J> <C-W>j<15C-W>_
map <C-K> <C-W>k<15C-W>_

set wmh=0

if bufwinnr(1)
	map = <C-W>+
	map - <C-W>-
endif

map ; :

" disable arrow keys
map <up> <nop>
map <down> <nop>
map <left> <nop>
map <right> <nop>
imap <up> <nop>
imap <down> <nop>
imap <left> <nop>
imap <right> <nop>

```

---

### Post by Garratt on 2009-04-01
I'm new to vi so mostly nub settings based on C++

P.S. it's not very organised

```
" ---- .VIMRC :- Written By G.CAMPTON. ----

" ---- set commands and options ----

syntax on               "  syntax highlighting
set sw=4                "  shift width
set sts=4               "  soft tab stop
set wrap                "  wrap lines
set nu                  "  number lines
set nuw=4               "  number width
set spell               "  spell check
set spl=en_us,en_au     "  languages
set title               "  title on status bar
set eb                  "  error bells
set ul=100              "  undo level
set et                  " -

"  ---- indenting ----
set ai                  "  auto indent
set si                  "  smart indent
set ci                  "  C/C++ indents
set cin                 " -

"  ---- C style indent keywords ----
set cink=0{,0},:,0#,!,o,O,e
set cinw=if,else,for,do,while,switch
set cinoptions=:.5s,>1s,p0,t0,(0,g2

"  ---- more commands ----     
set hi=100              "  history
set sh=bash             "  shell 
set warn                "  warnings
set debug=msg           "  debug type
set showmode            "  show mode in status
set expandtab           "  tabs are spaces

"  ---- file types ----
set ff=unix             "  file format
set enc=utf-8           "  encoding type

"  ---- more commands ----
set autowrite           "  saves if switching buffers
set incsearch           "  emacs style increment searching
set ignorecase          "  ignores case when searching
set smartcase           " -

"  ---- Backup ----
set backup              " -
set writebackup         " -

"  ---- more commands ----

set showmatch           "  show matching braces
set showcmd             "  show command in status
set textwidth=68        "  screen width
                                                                        

```

---

### Post by akvino on 2009-04-01
> **jimi_hendrix said:**
> well post them! and give a simple explanation if you want

Please do!

cat /etc/vimrc
if v:lang =~ "utf8$" || v:lang =~ "UTF-8$"
   set fileencodings=utf-8,latin1
endif

set nocompatible	" Use Vim defaults (much better!)
set bs=2		" allow backspacing over everything in insert mode
"set ai			" always set autoindenting on
"set backup		" keep a backup file
set viminfo='20,\"50	" read/write a .viminfo file, don't store more
			" than 50 lines of registers
set history=50		" keep 50 lines of command line history
set ruler		" show the cursor position all the time

" Only do this part when compiled with support for autocommands
if has("autocmd")
  " In text files, always limit the width of text to 78 characters
  autocmd BufRead *.txt set tw=78
  " When editing a file, always jump to the last cursor position
  autocmd BufReadPost *
  \ if line("'\"") > 0 && line ("'\"") <= line("$") |
  \   exe "normal! g'\"" |
  \ endif
endif

if has("cscope")
   set csprg=/usr/bin/cscope
   set csto=0
   set cst
   set nocsverb
   " add any database in current directory
   if filereadable("cscope.out")
      cs add cscope.out
   " else add database pointed to by environment
   elseif $CSCOPE_DB != ""
      cs add $CSCOPE_DB
   endif
   set csverb
endif

" Switch syntax highlighting on, when the terminal has colors
" Also switch on highlighting the last used search pattern.
if &t_Co > 2 || has("gui_running")
  syntax on
  set hlsearch
endif

if &term=="xterm"
     set t_Co=8
     set t_Sb=[4%dm
     set t_Sf=[3%dm
endif

---

### Post by dandaman0061 on 2009-04-01
A tad organized... I mostly program in Python and C++.  I also use multiple windows/buffers *a lot*.  What really helps is the <Ctrl>+[J/K] to switch buffer up/down and the changing the cwd to the current buffer is really convenient. (allows you to type :new <file>) and only have to know the relative path to the file you're currently working on.

```

" Use Vim settings
set nocompatible

fixdel
syntax enable

set ruler           " displays the 'ruler' at the bottom-right of the screen
set number          " precede each line with its line number.
set nowrap          " no line wrapping;
set guioptions+=b   " add a horizontal scrollbar to the bottom

colorscheme zenburn

"--- search options ------------
set incsearch       " show 'best match so far' as you type
set hlsearch        " hilight the items found by the search
set ignorecase      " ignores case of letters on searches
set smartcase       " Override the 'ignorecase' option if the search pattern contains upper case characters
:highlight search guifg=yellow guibg=darkred

"--- indentation ---------------
set expandtab
set smarttab
set smartindent    " smart indent of code - indent after opening '{',

"set autoindent     " Copy indent from current line when starting a new line
set shiftwidth=4   " Number of spaces to use for each step of (auto)indent (used for the >>, << commands)
set tabstop=4      " Number of spaces that a <Tab> in the file counts for.
set softtabstop=4  " Backspace the proper number of spaces
set shiftround     " Round indent to multiple of 'shiftwidth'

" comments are not placed in the first column.  They stay at their current indent level
inoremap # #

"--- Keystrokes ----------------
" h and l wrap between lines, cursor keys wrap in insertion mode
set whichwrap=h,l,~,[,]

" page down with <SPACE>, pageup with - or <BkSpc>
noremap <Space> <PageDown>
noremap <BS> <PageUp>

" allow <BkSpc> to delete line breaks, start of insertion, and indents
set backspace=eol,start,indent

"--- windowing -----------------
" be able to scroll through opened files easily with ctrl+j/k
map <C-J> <C-W>j<C-W>_
map <C-K> <C-W>k<C-W>_
set wmh=0   "set other opened files to just show filename


" have command-line completion <Tab> (for filenames, help topics, option names)
" first list the available options and complete the longest common part, then
" have further <Tab>s cycle through the possibilities:
set wildmode=list:longest,full

"--- python formatting help ---
autocmd BufRead *.py set smartindent cinwords=if,elif,else,for,while,try,except,finally,def,class

"-- always set cwd to current buffer ---
" * helps a lot with multiple windows
function! CHANGE_CURR_DIR()
let _dir = expand("%:p:h")
exec "cd " . _dir
unlet _dir
endfunction

autocmd BufEnter * call CHANGE_CURR_DIR()
"---------------------------------------

```

---

### Post by dwhitney67 on 2009-04-01
I do mostly C and C++ development; the following, along with the Fedora and Ubuntu default settings, suffice for me.  I've been using vi (vim) for almost 22 years!

```

" turn color syntax on
syntax on

" disable auto-comments
au FileType * setlocal comments=

" do not highlight matching parenthesis (that's what shift-% is for!)
let loaded_matchparen = 1

" restore position to the last line visited in the file
set viminfo='10,\"100,:20,%,n~/.viminfo
    au BufReadPost * if line("'\"") > 0|if line("'\"") <= line("$")|exe("norm '\"")|else|exe "norm
$"|endif|endif

```

---

### Post by days_of_ruin on 2009-04-01
narcotics.

EDIT: oops wrong tab

---

### Post by mvalviar on 2009-04-01
From a newbie vim user ```
set nocompatible
set autoindent
syntax on
set smartindent
set tabstop=4
set shiftwidth=4
set showmatch
set incsearch
```

---

### Post by tyfius on 2009-04-02
I am also using several plugins from which I will not list the scripts here. I started out from the VIM configuration of Andrei Zmievski which he uploaded for his [VIM for (PHP) programmers]("http://gravitonic.com/2007/02/vim-for-php-programmers-slides-and-resources") slideshow:

```
"
" MAIN CUSTOMIZATION FILE
"

" Enable loading filetype and indentation plugins
filetype plugin on
filetype indent on

" Turn syntax highlighting on
syntax on

"
" GLOBAL SETTINGS
"

" Write contents of the file, if it has been modified, on buffer exit
set autowrite

" Allow backspacing over everything
set backspace=indent,eol,start

" Insert mode completion options
set completeopt=menu,longest,preview

" Use UTF-8 as the default buffer encoding
set enc=utf-8

" Remember up to 100 'colon' commmands and search patterns
set history=100

" Enable incremental search
set incsearch

" Always show status line, even for one window
set laststatus=2

" Jump to matching bracket for 2/10th of a second (works with showmatch)
set matchtime=2

" Don't highlight results of a search
set nohlsearch

" Enable CTRL-A/CTRL-X to work on octal and hex numbers, as well as characters
set nrformats=octal,hex,alpha

" Use F10 to toggle 'paste' mode
set pastetoggle=<F10>

" Show line, column number, and relative position within a file in the status line
set ruler

" Scroll when cursor gets within 3 characters of top/bottom edge
set scrolloff=3

" Round indent to multiple of 'shiftwidth' for > and < commands
set shiftround

" Use 4 spaces for (auto)indent
set shiftwidth=4

" Show (partial) commands (or size of selection in Visual mode) in the status line
set showcmd

" When a bracket is inserted, briefly jump to a matching one
set showmatch

" Don't request terminal version string (for xterm)
set t_RV=

" Use 4 spaces for <Tab> and :retab
set tabstop=4

" Write swap file to disk after every 50 characters
set updatecount=50

" Remember things between sessions
"
" '20  - remember marks for 20 previous files
" \"50 - save 50 lines for each register
" :20  - remember 20 items in command-line history
" %    - remember the buffer list (if vim started without a file arg)
" n    - set name of viminfo file
set viminfo='20,\"50,:20,%,n~/.viminfo

" Use menu to show command-line completion (in 'full' case)
set wildmenu

" Set command-line completion mode:
"   - on first <Tab>, when more than one match, list all matches and complete
"     the longest common  string
"   - on second <Tab>, complete the next full match and show menu
set wildmode=list:longest,full

" Go back to the position the cursor was on the last time this file was edited
au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")|execute("normal `\"")|endif

" Fix my <Backspace> key (in Mac OS X Terminal)
set t_kb=^?
fixdel

" Avoid loading MatchParen plugin
let loaded_matchparen = 1

" netRW: Open files in a split window
let g:netrw_browse_split = 1

"
" MAPPINGS
"
" save changes
map ,s :w<CR>
" exit vim without saving any changes
map ,q :q!<CR>
" exit vim saving changes
map ,w :x<CR>
" switch to upper/lower window quickly
map <C-J> <C-W>j
map <C-K> <C-W>k
" use CTRL-F for omni completion
imap <C-F> ^X^O
" map CTRL-L to piece-wise copying of the line above the current one
imap <C-L> @@@<ESC>hhkywjl?@@@<CR>P/@@@<CR>3s
" map ,f to display all lines with keyword under cursor and ask which one to
" jump to
nmap ,f [I:let nr = input("Which one: ")<Bar>exe "normal " . nr ."[\t"<CR>
" use <F6> to toggle line numbers
nmap <silent> <F6> :set number!<CR>
" page down with <Space>
nmap <Space> <PageDown>
" Toggle line numbers
nmap <C-D><C-D> :set invnumber<CR>
" open filename under cursor in a new window (use current file's working
" directory)
nmap gf :new %:p:h/<cfile><CR>
" map <Alt-p> and <Alt-P> to paste below/above and reformat
nnoremap <Esc>P  P'[v']=
nnoremap <Esc>p  p'[v']=
" visual shifting (does not exit Visual mode)
vnoremap < <gv
vnoremap > >gv

" Abbreviations
ab #i #include
ab #d #define

" Generic highlight changes
highlight Comment cterm=none ctermfg=LightBlue
highlight IncSearch cterm=none ctermfg=Black ctermbg=DarkYellow
highlight Search cterm=none ctermfg=Black ctermbg=DarkYellow
highlight String cterm=none ctermfg=DarkGreen
highlight treeDir cterm=none ctermfg=Cyan
highlight treeUp cterm=none ctermfg=DarkYellow
highlight treeCWD cterm=none ctermfg=DarkYellow
highlight netrwDir cterm=none ctermfg=Cyan

" Set up cscope options
if has("cscope")
    set csprg=/usr/bin/cscope
    set csto=0
    set cst
    set nocsverb
    cs add cscope.out
    set csverb
    map <C-_> :cstag <C-R>=expand("<cword>")<CR><CR>
    map g<C-]> :cs find 3 <C-R>=expand("<cword>")<CR><CR>
    map g<C-\> :cs find 0 <C-R>=expand("<cword>")<CR><CR>
endif


"
" NERDTree configuration
"

" Increase window size to 35 columns
let NERDTreeWinSize=35

" map <F7> to toggle NERDTree window
nmap <silent> <F7> :NERDTreeToggle<CR>

let Tlist_GainFocus_On_ToggleOpen = 1

```

---

### Post by jimi_hendrix on 2009-04-02
ive only just begun modding my .vimrc,

credit to LaRoza for most of the contents in mine

```

:syn on "syntax highlighting
:set number "line numbers
:filetype plugin indent on "autoindent based on filetype
:set completeopt+=longest "for autocomplete with ctrl+p
:set showmatch "cant remember what this does
:set expandtab "makes tabs spaces
:set tabstop=4 "makes tabs 4 spaces
:set shiftwidth=4 "cant remember this (possibly autoindent = 4 spaces?)
:set nocompatible "cant remember
:set spl=en_us "sets spelling

```

---

### Post by asmoore82 on 2009-04-04
```
**asmoore@ubuntu-lenovo:~$** cat .vimrc 

syntax on
filetype on

filetype indent off

set ts=3
set bg=dark

**asmoore@ubuntu-lenovo:~$** cat .gvimrc 

set bg=light

amenu Edit.Remove\ Nul\ Bytes	:%s:<Nul>:\r:g<CR>
amenu Edit.Convert\ from\ Mac\ to\ UNIX  :%s:\r:\r:g<CR>

```

---

### Post by Vicfred on 2009-04-04
```
syntax on
set autoindent
colorscheme ir_black
set number
set guifont=Monaco\ Bold\ 12.5
set tabstop=2
```

---

### Post by Erich.AMA on 2011-06-03
[EMAIL="Erich.AMA@gmail.com"]
[/EMAIL]

---

### Post by schauerlich on 2011-06-03
```
:! emacs %
```

---

### Post by cgroza on 2011-06-03
> **schauerlich said:**
> ```
:! Emacs %
```
+1

---

### Post by shawnhcorey on 2011-06-04
OK, you asked for it.  BTW, it is actually my .gvimrc.
```
"
" Shawn's gvimrc file
"

" Make window as big as possible.
winpos 0 0
" set lines=99
" set columns=999
set lines=58
set columns=180

" Status line
set statusline=%F%m%r%h%w\ \ (%{&ff},%Y)\ \ %l/%L\ (%p%%)\ \ %v\ (%b,0x%02.2B)
set laststatus=2
set guioptions-=T

" miscellaneous
syntax enable
syntax match _all_Tab /	/
highlight _all_Tab gui=undercurl guibg=#dddddd guisp=#0000bb
runtime macros/matchit.vim
filetype plugin on

" functions
function ReformatParagraph(width)
  let save_tw = &tw
  let &tw = a:width
  normal gqap
  let &tw = save_tw
endfunction

" Key maps
map <C-Q>    :confirm q<CR>
map <C-S>    :if expand("%") == ""<Bar>browse confirm w<Bar>else<Bar>confirm w<Bar>endif<CR>
map <C-O>    :browse confirm e<CR>
map <C-P>    :call ReformatParagraph(60)<CR>

map <C-Down>   <C-E>
map <C-Up>     <C-Y>
map <S-C-Down> <Down><C-E>
map <S-C-Up>   <Up><C-Y>

" Ctrl-Alt key maps
" C-M-O
map   :vnew<CR><C-W>L:browse confirm e<CR>
" C-M-Q
map ‘  :confirm qall<CR>
" C-M-P
map   {jmp}kmq:'p,'qj<CR>:s/\([^A-Z][?.!]"\?\)  \?\("\?[A-Z]\)/\1\r\2/g<CR>:let @/ = '\r'<CR>2j
" C-M-J
map Š  {jmp}kmq:'p,'qj<CR>2j
" C-M-T
map ”  /\<TBD\><CR>

filetype on

" Indent options
set   autoindent     " Indent new lines to that of others
set noexpandtab      " Do not replace tabs
set   shiftround     " Round indentation to nearest shiftwidth
set   shiftwidth=4   " Indentation is 4 spaces
set   smartindent    " Auto indent/outdent for { }
set   softtabstop=4  " Indentation is HT characters
set   tabstop=4      " Indentation is HT characters

" Search options
set   hlsearch       " Highlight search matches on screen
set   incsearch      " Jump to searched item as pattern is typed

" Text options
set   encoding=utf-8 " All files are UTF8
set   ignorecase     " Searches ignore case
set   textwidth=0    " Disable textwidth

augroup yamlfiles
  autocmd filetype yaml setlocal   autoindent
  autocmd filetype yaml setlocal   expandtab
  autocmd filetype yaml setlocal noignorecase
  autocmd filetype yaml setlocal   shiftround
  autocmd filetype yaml setlocal   shiftwidth=4
  autocmd filetype yaml setlocal   smartindent
  autocmd filetype yaml setlocal   softtabstop=4
  autocmd filetype yaml setlocal   tabstop=4
  autocmd filetype yaml setlocal   textwidth=0
augroup END

augroup perlfiles
  autocmd filetype perl setlocal   autoindent
  autocmd filetype perl setlocal   expandtab
  autocmd filetype perl setlocal noignorecase
  autocmd filetype perl setlocal   shiftround
  autocmd filetype perl setlocal   shiftwidth=2
  autocmd filetype perl setlocal   smartindent
  autocmd filetype perl setlocal   softtabstop=2
  autocmd filetype perl setlocal   tabstop=2
  autocmd filetype perl setlocal   textwidth=0
augroup END

augroup msfiles
  autocmd filetype ms setlocal   autoindent
  autocmd filetype ms setlocal noexpandtab
  autocmd filetype ms setlocal   ignorecase
  autocmd filetype ms setlocal   shiftround
  autocmd filetype ms setlocal   shiftwidth=8
  autocmd filetype ms setlocal   smartcase
  autocmd filetype ms setlocal nosmartindent
  autocmd filetype ms setlocal   softtabstop=8
  autocmd filetype ms setlocal   spell
  autocmd filetype ms setlocal   spelllang=en_us
  autocmd filetype ms setlocal   tabstop=8
  autocmd filetype ms setlocal   textwidth=0
augroup END

augroup bbcodefiles
  autocmd filetype bbcode setlocal   autoindent
  autocmd filetype bbcode setlocal   expandtab
  autocmd filetype bbcode setlocal   ignorecase
  autocmd filetype bbcode setlocal   shiftround
  autocmd filetype bbcode setlocal   shiftwidth=4
  autocmd filetype bbcode setlocal   smartcase
  autocmd filetype bbcode setlocal   smartindent
  autocmd filetype bbcode setlocal   softtabstop=4
  autocmd filetype bbcode setlocal   spell
  autocmd filetype bbcode setlocal   spelllang=en_ca
  autocmd filetype bbcode setlocal   tabstop=4
  autocmd filetype bbcode setlocal   textwidth=0
  autocmd filetype bbcode setlocal nowrap
augroup END

augroup textfiles
  autocmd filetype text setlocal noautoindent
  autocmd filetype text setlocal noexpandtab
  autocmd filetype text setlocal   ignorecase
  autocmd filetype text setlocal noshiftround
  autocmd filetype text setlocal   shiftwidth=4
  autocmd filetype text setlocal   smartcase
  autocmd filetype text setlocal nosmartindent
  autocmd filetype text setlocal   softtabstop=4
  autocmd filetype text setlocal   spell
  autocmd filetype text setlocal   spelllang=en_ca
  autocmd filetype text setlocal   tabstop=4
  autocmd filetype text setlocal   textwidth=0
  autocmd filetype text setlocal nowrap
augroup END

augroup podfiles
  autocmd filetype pod setlocal noautoindent
  autocmd filetype pod setlocal   expandtab
  autocmd filetype pod setlocal   ignorecase
  autocmd filetype pod setlocal noshiftround
  autocmd filetype pod setlocal   shiftwidth=4
  autocmd filetype pod setlocal   smartcase
  autocmd filetype pod setlocal nosmartindent
  autocmd filetype pod setlocal   softtabstop=4
  autocmd filetype pod setlocal   spell
  autocmd filetype pod setlocal   spelllang=en_us
  autocmd filetype pod setlocal   tabstop=4
  autocmd filetype pod setlocal   textwidth=0
augroup END

augroup tabfiles
  autocmd filetype tab setlocal noautoindent
  autocmd filetype tab setlocal noexpandtab
  autocmd filetype tab setlocal   ignorecase
  autocmd filetype tab setlocal noshiftround
  autocmd filetype tab setlocal   shiftwidth=8
  autocmd filetype tab setlocal nosmartindent
  autocmd filetype tab setlocal   softtabstop=8
  autocmd filetype tab setlocal   tabstop=8
  autocmd filetype tab setlocal   textwidth=0
  autocmd filetype tab setlocal nowrap
augroup END

" scripts

" Set search buffer to \<TBD\> if present
autocmd filetype perl source $HOME/.vim/after/scripts/perl.vim
autocmd BufNewFile,BufRead * source $HOME/.vim/scripts/tbd.vim


```

---

### Post by lotuseclat79 on 2011-07-18
In my ~ubuntu/.vimrc file (looks like):
:map ^P !}fmt -80
where ^P is a single control character inserted using Ctrl-^-P, i.e. press and hold down the CTRL-key and then press in sequence the '^' character followed by 'P'.

The allows you to reformat long lines into 80 character lines by positioning the cursor to the start of the long line and then pressing Ctrl-P followed by Enter.

-- Tom

---

