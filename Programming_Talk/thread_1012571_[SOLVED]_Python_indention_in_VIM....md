---
title: "[SOLVED] Python indention in VIM..."
date: 2008-12-16
forum: Programming Talk
---

### Post by helstreak on 2008-12-16
first off, here's my startup
syntax on
set smartindent
set autoindent
set nobackup
set nowritebackup
set noswapfile
set columns=90
set lines=40
set tabstop=4
set shiftwidth=4
set smarttab
colorscheme murphy

how do i get VIM to do the right indentions after the colon?  it won't indent after something like "def foo():"  thanks for the help :)

---

### Post by jimi_hendrix on 2008-12-16
i dont remember the exact command but its very simple...

something like

:indent on

but i dont think that is right

---

### Post by Greyed on 2008-12-16
Better to put those in augroups.

```

let python_highlight_all = 1
augroup Python
  au!
  "au BufNewFile *.py read ~/util/templates/Python.py
  " see also :help smartindent , cinwords
  au FileType python set autoindent smartindent et sts=4 sw=4 tw=80 fo=croq
  " turn off the C preprocessor indenting
  " (allow comments in Python to be indented properly)
  "au FileType python inoremap # X^H#
  "au FileType python set foldenable foldmethod=indent
augroup END

```

---

### Post by mssever on 2008-12-16
It's been a while since I've messed with vim's settings, so I no longer remember what most of this does. However, here's a portion of my .vimrc. The setting should be somewhere in there: ```
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
" Uncomment the following to have Vim jump to the last position when
" reopening a file
if has("autocmd")
  au BufReadPost * if line("'\"") > 0 && line("'\"") <= line("$")
    \| exe "normal g'\"" | endif
endif

" Uncomment the following to have Vim load indentation rules according to the
" detected filetype. Per default Debian Vim only load filetype specific
" plugins.
if has("autocmd")
  filetype indent on
endif
" If using a dark background within the editing area and syntax highlighting
" turn on this option as well
"set background=dark
```If I had to guess, my guess would be [FONT=Courier New][COLOR=SeaGreen]filetype indent on[/COLOR][/FONT].

---

### Post by jimi_hendrix on 2008-12-16
filetype indent on

is it...theres something about plugin that i cant remember but iwll post later that gives even better support but...this should work

---

### Post by Greyed on 2008-12-16
```

filetype on
filetype plugin on
filetype indent on

```

?

---

### Post by helstreak on 2008-12-16
"filetype indent on" did the job

thanks for the help everyone

---

