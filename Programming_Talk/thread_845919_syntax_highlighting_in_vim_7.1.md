---
title: "syntax highlighting in vim 7.1"
date: 2008-07-01
forum: Programming Talk
---

### Post by hey_ram on 2008-07-01
hey all,

i am using ubuntu 8.04 that came with vim 7.1.

i am trying to write some code in C++ but cannot figure out the following:

1. syntax highlighting.
i tried out a lot of commands, such as "syntax on", "syntax enable" in command mode of vi. but every time i try these commands out, i end up with the message 

"E319: Sorry, the command is not available in this version"

2. where can i find my .vimrc
does this file come "pre-loaded" with vim like bashrc or bash_profile do with bash?

3. I also wanted to set number lines. that went off smoothly with the "set nu" command. but how do i make these changes permanent??

please help...

---

### Post by Greyed on 2008-07-01
Taking a stab here but:
```

sudo aptitude install vim

```

If Ubuntu follows Debian in this regard they install vim-tiny by default which is vim in vi compatibility mode and nothing else at all compiled in.

---

### Post by LaRoza on 2008-07-01
> **Greyed said:**
> 

If Ubuntu follows Debian in this regard they install vim-tiny by default which is vim in vi compatibility mode and nothing else at all compiled in.

That is the fix, and that is the reason.

It should have a pretty ok default setting which you can change if you want.

---

### Post by hey_ram on 2008-07-01
thanx!!

that did it..
Greyed..u were correct...the syntax highlighting works perfectly now.

i had been reading up some other discussions where one of the suggestions was to do:
sudo apt-get install vim-full
i tried that and it still did not work...

any idea about the other two questions from the earlier post...

1. where do i find .vimrc, or do i have to create one...
if i have to create one, where do i create the file (which directory)?

2. how do i make the changes (of line numbering, syntax highlighting) permanent?

---

### Post by Greyed on 2008-07-01
> **hey_ram said:**
> 1. where do i find .vimrc, or do i have to create one...
if i have to create one, where do i create the file (which directory)?

You create it in your home directory.  When you open up a console you're in your home directory so just vim .vimrc right there.  

> 2. how do i make the changes (of line numbering, syntax highlighting) permanent?

Place them there in your .vimrc.  Personally I took advantage of vims augroups.  Here's my .vimrc file as an example:
```

set bg=dark
set modelines=5
syntax on
map Q gq
let spell_executable = "aspell"
let spell_language_lsist = 'english'
let spell_insert_mode = 0
filetype on
filetype plugin on
filetype indent on

" this takes effect when the syntax file is loaded
let python_highlight_all = 1
augroup Python
  au!
  "au BufNewFile *.py read ~/util/templates/Python.py
  " see also :help smartindent , cinwords
  au FileType python set autoindent smartindent et sts=4 sw=4 tw=80 fo=croq
  " turn off the C preprocessor indenting
  " (allow comments in Python to be indented properly)
  " au FileType python inoremap # X^H#
  " au FileType python set foldenable foldmethod=indent
augroup END

augroup Mail
  au!
  au Filetype mail set noai tw=78 wrap
augroup END

```

Basically sets up some stuff I generally want on all the time, then sets up what I want for my Python coding and mail writing but only when I am coding Python or writing mail.

---

### Post by ynnhoj on 2008-07-06
there's already a vimrc located at **/etc/vim/vimrc** which you can take a peek at.  changes to that file, of course, would apply to all users.  you can also make a ~/.vimrc to make any personal changes, as has been mentioned.

---

### Post by ewproctor on 2008-10-27
I am slowly coming to love VIM.  I have syntax highlighting and auto-indentation over ssh now...that made my day.

---

