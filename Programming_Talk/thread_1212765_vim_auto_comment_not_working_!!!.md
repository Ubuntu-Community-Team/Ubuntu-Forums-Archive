---
title: "vim auto comment not working !!!"
date: 2009-07-14
forum: Programming Talk
---

### Post by abraham.varricatt on 2009-07-14
I've been using vim for months now. Suddenly, it seems that the auto-comment feature is NOT working. I tried googling, but I couldn't find anything.

By auto-comment (in C ) When we type in something like this,

```

#include <sample.h>
/*

```Now if I press "Enter" I expect a "*" character to appear on the next line. This is what I expect (and used to get),

```

#include <sample.h>
/*
*
*
*
*
*

```

But now, all I get is a blank line. Any ideas ? And here is my .vimrc file,

```

set nocompatible  " must be on first line (I'm running vim NOT vi)
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""
" Author        : Abraham Varricatt
""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""""

" BASICS FOR ALL FILE-TYPES
syntax on                       " Turn on syntax highlighting
set cursorline                  " Highlights the current line
"set ruler                      " Always display current line postion

                                " Show stats of line on status bar
set statusline=%<%f\ %m%a%=%([%R%H%Y]%)\ %-19(%3l\ of\ %L,%c%)%P
set laststatus=2                " Status line always visible. =0 to remove
set cindent                     " This and the next one are
set smartindent                 " for indentation purposes
"set paste                      " Pasting without indendation problems
set incsearch                   " Search as you type

" Tab spacing
set tabstop=8
set shiftwidth=8

" CUSTOMIZATION FOR C FILES (AND HEADERS)
"autocmd BufNewFile,BufRead *.h set comments=s:/**,mb:*,ex:*/   " For nicer comments


" PLUGIN SETTINGS

" taglist.vim : Source code browser (supports C/C++, java, perl ... etc)
"**************

                " This will map the F8 key to toggle the list on/off
nnoremap <silent> <F8> :TlistToggle<CR>
                " Move cursor to taglist window when opened
let Tlist_GainFocus_On_ToggleOpen = 1
                " Close the taglist after selecting a tag
let Tlist_Close_On_Select = 1



" The NERD tree : A tree explorer plugin for navigating the filesystem
"****************

                " This will toggle the NERDTree at the current location
nnoremap <silent> <F7> :NERDTreeToggle<CR>
                " To turn OFF this plugin, enable the line below
" let loaded_nerd_tree=1
                " Some syuntax highlighting with the tree
let NERDChristmasTree=1


```Any suggestions ? I've looked everywhere I could think of.

---

### Post by monraaf on 2009-07-14
Try adding this to the end of your .vimrc:

[PHP]
if has("autocmd")
  filetype plugin indent on
endif
[/PHP]

---

### Post by dwhitney67 on 2009-07-14
Wow, this is the first time I have heard of someone actually wanting the auto-comment feature enabled.  Personally I find it annoying, especially when pasting code that has a sprinkle of comments in it; after pasting the code, that every line of code below a comment has been commented-out... including additional comments (if any) themselves.

So when I copy this from one vim session:
```

int i;

// search for all occurrences of...
for (i = 0; i < 5; ++i)
{
   // check if a match
   ...
}

```

to another vim session, this is what appears:
```

int i;

// search for all occurrences of...
//for (i = 0; i < 5; ++i)
//{
//   // check if a match
//   ...
//}

```

---

### Post by abraham.varricatt on 2009-07-15
[monraaf]("http://ubuntuforums.org/member.php?u=536089"),
Thanks a LOT for that!! I must have been searching for about 2 days now and I couldn't figure it out.

[dwhitney67]("http://ubuntuforums.org/member.php?u=322753"),
The auto-comment is needed to distinguish (at a glance) between code and comment. (for me anyway). I've come across the paste problem you mention, especially when using Putty. Before pasting, run,


:set paste


That will avoid inserting the // during the paste operation. When the pasting is over, you can enable things back with,


:set nopaste


Hope it helps.

---

### Post by sujoy on 2009-07-15
```
map <F10> :set paste!<Bar>set paste?<CR>
```

add this to your vimrc, to toggle the paste behaviour.

---

### Post by abraham.varricatt on 2009-07-15
[sujoy]("http://ubuntuforums.org/member.php?u=411789"),

Thanks for the tip. I just tried it out. Looks like to activate/deactivate the short-cut I'll need to be outside the "insert" mode. I think I can manage with this. 

I re-assigned the key to F6.

---

