---
title: "vim omnicppcomplete issues"
date: 2010-09-30
forum: Programming Talk
---

### Post by Tamaros on 2010-09-30
I used a tutorial ([http://vim.wikia.com/wiki/VimTip1608]("http://vim.wikia.com/wiki/VimTip1608")) to set up c++ code completion in vim.  

I used the links in the tutorial as the sources for omnicppcomplete and the headers.

Reading through the omnicppcomplete.txt help file an comparing the detail there to the instruction i followed everything seems to be kosher.  Problem is that whenever the complete function is invoked I get a string of errors.:

[PHP]Error detected while processing function omni#cpp#complete#Main..omni#cpp#namespaces#GetContexts:
line    4:
E712: Argument of extend() must be a List or Dictionary
Press ENTER or type command to continue
Error detected while processing function omni#cpp#complete#Main..omni#cpp#namespaces#GetContexts:
line    7:
E745: Using a List as a Number
Press ENTER or type command to continue
Error detected while processing function omni#cpp#complete#Main..omni#cpp#namespaces#GetContexts:
line    7:
E15: Invalid expression: omni#cpp#namespaces#GetUsingNamespaces() + listUsingNamespace
Press ENTER or type command to continue
Error detected while processing function omni#cpp#complete#Main..omni#cpp#namespaces#GetContexts..omni#cpp#namespaces#ResolveAll:
line   16:
E714: List required
Press ENTER or type command to continue

-- Omni completion (^O^N^P) Pattern not found[/PHP]


Current .vimrc is 
```
  1 " turn of vi compatability
  2 set nocompatible
  3 
  4 " enable syntax
  5 syntax enable
  6 filetype plugin indent on
  7 " set mouse=a
  8 
  9 runtime! macros/matchit.vim
 10 
 11 augroup myfiletypes
 12    autocmd!
 13    autocmd FileType ruby,eruby,yaml set ai sw=2 sts=2 et
 14 augroup end
 15 
 16 " highlight the current line
 17 "set cursorline
 18 
 19 " show line numbers
 20 set number
 21 
 22 " incremental search, flexible with case
 23 set incsearch
 24 set ignorecase
 25 set smartcase
 26 
 27 " limit scroll so I can see surrounding lines
 28 set scrolloff=3
 29 
 30 " tab = 3 spaces
 31 set tabstop=3 shiftwidth=3 expandtab
 32 
 33 " turn on the spellchecker
 34 " set spell
 35 
 36 " highlight overly long lines in red
 37 highlight OverLength ctermbg=red ctermfg=white guibg=#592929
 38 match OverLength /\%71v.\+/
 39 
 40 " set tags
 41 set tags+=~/.vim/tags/cpp
 42 
 43 " build custom project tags with cntrl-F12
 44 map <C-F12> :!ctags -R --sort=yes --c++-kinds=+p1 --fields=iaS --extra=+q .<CR>
 45 
 46 " omnicomplete settings
 47 let OmniCpp_NamespaceSearch = 1
 48 let OnmiCpp_GlobalScopeSearch = 1
 49 let OmniCpp_ShowAccess = 1
 50 let OmniCpp_ShowPrototypeInAbbr = 1
 51 let OmniCpp_MayCompleteDot = 1
 52 let OmniCpp_MayCompleteArrow = 1
 53 let OmniCpp_MayCompleteScope = 1
 54 let OmniCpp_DefaultNamespaces = 1
 55 
 56 " automatically open and close the popup menu/preview window
 57 au CursorMovedI,InsertLeave * if pumvisible() == 0|silent! pclose|endif
 58 set completeopt=menuone,menu,longest,preview
```

Considering I can't seem to find this issue anywhere else it seems it must be an issue with my configuration but I can find it.

---

### Post by gmargo on 2010-10-01
Your best bet for vim help, especially with complex topics, is to join the vim mailing list.

[http://www.vim.org/maillist.php#vim](http://www.vim.org/maillist.php#vim)

---

### Post by Tamaros on 2010-10-02
Will look into it.  Thanks for the reply.

---

