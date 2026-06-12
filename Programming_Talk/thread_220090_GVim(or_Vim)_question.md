---
title: "GVim(or Vim) question"
date: 2006-07-20
forum: Programming Talk
---

### Post by Cyraxzz on 2006-07-20
does it have syntax highlighting for programming languages?

---

### Post by theconley on 2006-07-21
Do :syntax on

In vim you can write a .vimrc file in your home directory.

This is a simple one I use.

```
set tabstop=4
set shiftwidth=4
set smarttab
set autoindent
syntax on
```

I'd like to suggest that the vim package come with a default .vimrc file.  Vim is not much better than a vanilla text editor without syntax highlighting.

As you can probably tell by the number of posts, I'm new to Ubuntu.  Where do I go to suggest this?

---

### Post by Wallakoala on 2006-07-22
I have a really cool .vimrc, complete with line numbers.

Here it is if you want to use it:

```

" ****************************************************************************
" General settings
" ****************************************************************************
set comments=b:#,:%,fb:-,n:>,n:)
set formatoptions=tcro
set ruler
set incsearch
set showmode
set visualbell
set wrapmargin=1
set showmatch
set ignorecase
set showcmd
set hlsearch
set tw=78
set backspace=indent,eol,start
set laststatus=2
set softtabstop=8
set autoindent
set nu!
"color murphy

" For spell checking
noremap <F8> :so "~/.vim/tools/vimspell.sh %"<CR><CR>
noremap <F7> :syntax clear SpellErrors<CR>

nmap <silent> <Leader>sh :exe ":source ~/.vim/tools/vimsh.vim"<cr>
let g:vimsh_show_workaround_msgs=0
let g:vimsh_sh="/bin/tcsh"

" ****************************************************************************
" abbreviations
" ****************************************************************************
ab #d #define
ab #i #include <

" Some extensions to ignore
set wildignore=*.o,*.bak,*.aux,*.class
set wildmenu

" ****************************************************************************
" skeleton commands
" ****************************************************************************
autocmd BufNewFile *.c 0r ~/src/templates/skeleton.c
autocmd BufNewFile *.h 0r ~/src/templates/skeleton.h
autocmd BufNewFile *.pl 0r ~/src/templates/skeleton.pl
autocmd BufNewFile *.cpp 0r ~/src/templates/skeleton.cpp
autocmd BufNewFile *.java 0r ~/src/templates/skeleton.java
autocmd BufRead *.py set smartindent cinwords=if,elif,else,for,while,try,except,finally,def,class
autocmd BufWritePre *.py normal m`:%s/\s\+$//e ``

" Set file types for uncommon extensions
au BufRead,BufNewFile *.sc setfiletype scheme
au BufRead,BufNewFile *.thtml setfiletype html
au BufRead,BufNewFile *.babe setfiletype babe
au BufRead,BufNewFile *.ihtml setfiletype html

" ****************************************************************************
" filetype specific stuff
" ****************************************************************************
au FileType c set cindent tw=79

au FileType matlab set ai et sw=2 sts=2 noexpandtab tw=78
au FileType java set ai et sw=2 sts=2 noexpandtab cindent tw=78
au FileType python set ai et sw=2 sts=2 noexpandtab tw=78
au FileType perl set ai et sw=4 sts=4 noexpandtab tw=78 cindent
au FileType awk set ai et sw=4 sts=4 noexpandtab tw=78
au FileType tex set ai et sw=2 sts=2 noexpandtab tw=78
au FileType cpp set cindent tw=79
au FileType php set ai et sw=4 sts=4 ts=4 cindent tw=78
au FileType html set ai et sw=2 sts=2 noexpandtab tw=78
au FileType sh set ai et sw=4 sts=4 noexpandtab
au FileType scheme set ai et sw=1 sts=1 noexpandtab tw=78 lisp
au FileType lex set ai et sw=2 sts=2 noexpandtab
au FileType yacc set ai et sw=2 sts=2 noexpandtab
au FileType vim set ai et sw=2 sts=2 noexpandtab
au FileType babe set ai et sw=2 sts=2 noexpandtab
au FileType xml set ai et sw=2 sts=2 noexpandtab
au FileType sgml set ai et sw=2 sts=2 noexpandtab

syntax on

" ****************************************************************************
" Key Mappings
" ****************************************************************************

" quick way to source vimrc
nmap ,s :source /home/wsmith/.vimrc<cr>

" Map <c-x> to erase in insert mode
imap <c-x> <c-o>x

" Move around in insert mode
imap <c-j> <c-o>j
imap <c-k> <c-o>k
imap <c-l> <c-o>l
" imap <c-h> <c-o>h

" Map <c-s> to search in insert mode
imap <c-s> <c-o>/

" Map <c-e> to move to the end of a line in insert mode
imap <c-e> <c-o>$

" Map <c-a> to move to the beginning of a line in insert mode
imap <c-a> <c-o>^

" Map <c-f> to move forward a word in insert mode
imap <c-f> <c-o>w

" Map <c-b> to move backward a word in insert mode
imap <c-b> <c-o>b

" Quick quit
map <F2> :q<cr>

" Map <c-s> to write current buffer
map <c-s> :w<cr>
imap <c-s> <c-o><c-s>
imap <c-s> <esc><c-s>

" Undo in insert mode
imap <c-u> <c-o>u

" Navigate screens in insert mode
imap <c-w>k <c-o><c-w>k
imap <c-w>j <c-o><c-w>j
imap <c-w>l <c-o><c-w>l
imap <c-w>h <c-o><c-w>h

" Turn paste on/off
set pastetoggle=<F3>

" ****************************************************************************
" neat hacks
" ****************************************************************************
" show whitespace at the end of lines
highlight WhitespaceEOL ctermbg=blue guibg=blue
match WhitespaceEOL /\s\+$/

" swap current word with the next word
nmap <silent> gw "_yiw:s/\(\%#\w\+\)\(\_W\+\)\(\w\+\)/\3\2\1/<cr><c-o><c-l>

" ****************************************************************************
" misc
" ****************************************************************************
hi! Comment ctermfg=cyan ctermbg=black guifg=blue guibg=black
au Syntax mail source /usr/share/vim/vim62/syntax/mail.vim
runtime ftplugin/man.vim

```

I found it on some site awhile ago...

---

