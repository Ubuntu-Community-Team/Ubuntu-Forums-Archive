---
title: "beginner to c help IDE, vim compile"
date: 2008-03-29
forum: Programming Talk
---

### Post by jubej on 2008-03-29
Hello!

I have read a lots of post here about best IDE, editors and c books to read for beginner, after 8 hou of reading in this forum i discover something intressting.

a lot of people says that vim and emacs are like the best out there for linux. and that others IDE like Anjuta and Geany are like not that good.

and about books a lot of people recommend books for complete beginner they recommend books that are kind of advance, you have to have a basic knowledge on c or prograrmming in general to get to understand those books.

Here its my experience, a tried vim and it has a lot of features i mean a lot, its to confusing. Anjuta dosent work at all, an Geany its the only that i wrote the hello program and compile and run it without dificulties.

Anyway i've read that if you want to go professional you need to know vim or emacs.

so the question is:

i want to start writing c program in vim. but how can i USE vim? i started it and its really hard to understand? can aonyone write a tutorial simple to follow on how to even use vim, and how to set up to work for C?

I start v im and i cant write anyting i get this  

VIM vi improved ....type help to enter, type q<enter> to quit etc

i dont know how to navigate in this.

i use gedit before and you just start start typyng and thats it.

other thing its the compiler. everyone suggest to use g++ but i dont find really eny good tutorial about HOW to use it. maybe some answer read the man page or something like that but for someone really new its hard to understand all that.

and for the books recommended are:

The C Programming Language 2nd Ed
Accelerated C++ 2000
Apress.Beginning.C.From.Novice.to.Professional.4th.Edition.Oct.2006

but i have read that the first two are for people that have basic knowledge about prrogramming.




in short.
 if a complete beginner that never even, compile or read or never had any experience what so ever about programming in c and never ever use vim and g++. its there anyone that can help me with how to use vim, how to write in vim and set up. and how to use g++ for compiling and running a program?

I think a lot of people like me will appreciate this help.

thax for all the people that take the time to help other. i hope i to can someday help others with my knowledge.

a thousand miles journey start always with the first step.

---

### Post by LaRoza on 2008-03-29
Vi(m) is good to know (the basics) because it is on every *nix. Emacs is just a weird preference of some people, pay it no mind. (When I say Vim or Vi here, you can usually substitute Emacs, but I must represent my religion here)

For editing, I like Gedit and Vim.

Gedit has a lot of plugins for it that really enhance it.

Vim has a learning curve. 

My wiki has two links to tutorials: [http://laroza.pbwiki.com/Specific](http://laroza.pbwiki.com/Specific) Google will find you more.

g++ guides can be found in the sticky. In the shell, the arrow keys cycle through commands, so you don't have to keep typing it. (Follow the guide on compiling hello world, and then press the arrow keys (up) and you will see that you can do anything over again without typing.)

Don't force yourself to use tools you don't want to use. Use what works for you.

Gedit:
[[IMG]http://img265.imageshack.us/img265/3752/pantallazo1vl4.th.png[/IMG]](http://img265.imageshack.us/my.php?image=pantallazo1vl4.png)
Vim:
[[IMG]http://img265.imageshack.us/img265/7310/pantallazo2fo4.th.png[/IMG]](http://img265.imageshack.us/my.php?image=pantallazo2fo4.png)

---

### Post by jubej on 2008-03-29
thanx for you r fast reply LaRoza

you wrote:
g++ guides can be found in the sticky. In the shell, the arrow keys cycle through commands, so you don't have to keep typing it. (Follow the guide on compiling hello world, and then press the arrow keys (up) and you will see that you can do anything over again without typing.)

in witch sticky? in this forum or in your forum?
and i dont find the vim tutorial, i wen to your site, its grerat by the way i think that i can learn a lot from that :)

anyway can you help me on one thing?

whats the basic package for learning c in ubuntu?

is this good?

compiler:    g++
editor vim? if i learn first how to use it or its Geany better for complete begiinerr better?
book: 
witch one of this is better i have all 3 on e-books, but witch one to start with?
The C Programming Language 2nd Ed
Accelerated C++ 2000
Apress.Beginning.C.From.Novice.to.Professional.4th .Edition.Oct.2006


is this a god chise or do you recomend anything other?

---

### Post by LaRoza on 2008-03-29
> **jubej said:**
> 
in witch sticky? in this forum or in your forum?
and i dont find the vim tutorial, i wen to your site, its grerat by the way i think that i can learn a lot from that :)

[http://ubuntuforums.org/showthread.php?t=606009](http://ubuntuforums.org/showthread.php?t=606009)

On the wiki page I linked to, Vim is at the bottom.

> 
compiler:    g++
editor vim? if i learn first how to use it or its Geany better for complete begiinerr better?
book: 
witch one of this is better i have all 3 on e-books, but witch one to start with?
The C Programming Language 2nd Ed
Accelerated C++ 2000
Apress.Beginning.C.From.Novice.to.Professional.4th .Edition.Oct.2006


is this a god chise or do you recomend anything other?

Well, gcc is standard for Linux development. There are other compilers, but gcc is the one you should use. (g++ is part of gcc).

I would recommend an editor you like, it doesn't matter which one. Geany and Gedit are both nice. As you see, I have gedit customized to my liking. (I also have bash customized)

What is your experience in programming? I would recommend K&R, if you are able to follow it. It is the only C book I use, but it isn't a book for beginners to programming.

---

### Post by gnuman on 2008-03-29
I too was really thrown off by Vim first time I tried it.  

Vim, however, comes with a very good tutorial file, although I had trouble finding it originally.  Eventually I got a copy of the tutorial file and stuck it in a folder in my home directory.  Then I would navigate to it in terminal and type:

```

vim tutorial.txt

```

I think that tutorial is the best way to learn Vim.  

Here a past version of it: [vimtutor.txt]("http://www.cs.umu.se/~janl/vimtutor.txt")

---

### Post by CptPicard on 2008-03-29
@LaRoza, your computer speaks Spanish? :)

I have been thinking of making mine speak German. There would be something nicely pedantic about getting my compiler warnings auf Deutsch.. ;) (not to mention that if I ever write a programming language that I feel fixes all the problems with other languages, it will be called **Über**)

@OP, you shouldn't bother with vi... or Emacs by that matter although that is *my* editor-religion. Whenever I am not feeling religious, which is quite often, I use Kate of KDE...

The package for developing in C is "build-essential". As for programming books... you just need to pick one and start reading. There is no way to know in advance which of them will work for you...

---

### Post by rye_ on 2008-03-29
As a previous poster stated, the extensive range of plugins makes gedit an extremely versatile text editor.  class/ file side pane, embedded terminals, (THE ENORMOUSLY USEFUL) code snippets.  I could go on ...

---

### Post by Triggerhapp on 2008-03-29
> **LaRoza said:**
> Vim has a learning curve. 

Does it? I moved from Windows notepad to Vi without a second thought... I dont remember ever bieng incapable of doing what I want in it (unless it is using arrow keys while in insert mode...) 

> (When I say Vim or Vi here, you can usually substitute Emacs, but I must represent my religion here)Indeed you must.

---

### Post by LaRoza on 2008-03-29
> **CptPicard said:**
> @LaRoza, your computer speaks Spanish? :)


Si.

> **Triggerhapp said:**
> Does it? I moved from Windows notepad to Vi without a second thought... I dont remember ever bieng incapable of doing what I want in it (unless it is using arrow keys while in insert mode...) 

Indeed you must.

If you were able to transfer knowledge of notepad to Vi, then you have amnesia or some Über skills.

Everyone knows that Vi(m) is better, but Emacs is the child of RMS, and I respect him.

---

### Post by Triggerhapp on 2008-03-29
> **LaRoza said:**
> 
If you were able to transfer knowledge of notepad to Vi, then you have amnesia or some Über skills.
Or Google :D

---

### Post by mssever on 2008-03-29
@OP: If you end up learning vim, run the command vimtutor, which is designed to teach you vim. Although, as others have said, there's no reason why you should use vim or emacs if you don't like them. It's good to be familiar with a CLI text editor in case you're ever stuck without X. If I didn't have vim, I'd use joe. (Emacs is heresy :))

But for normal programming, pick the tool you prefer. For a GUI editor, I go back and forth between gedit and scribes.
> **Triggerhapp said:**
> I dont remember ever bieng incapable of doing what I want in it (unless it is using arrow keys while in insert mode...)
I use arrow keys in insert mode (or any other mode) all the time. The key is to use the actual arrow keys. Forget about h, j, k, and l. As far as I'm concerned, those keys could be re-bound to something that's actually useful. (Though I haven't cared enough to learn how to re-bind keys.)

---

### Post by Triggerhapp on 2008-03-29
> **mssever said:**
> I use arrow keys in insert mode (or any other mode) all the time. The key is to use the actual arrow keys. Forget about h, j, k, and l. As far as I'm concerned, those keys could be re-bound to something that's actually useful. (Though I haven't cared enough to learn how to re-bind keys.)

I can on my Desktop, cant on my laptop. Not too fussed to be fair, I can get around by pulling out of insert mode, which is better for me if i knock a key XD

---

### Post by jubej on 2008-03-29
oki thanx for all your answer it really help.
I have learned now the basics of editin deleting and copy save. etc etc. the basic skills off using vim.

now the question is:

can someone please help me to setup VIM for C programming? like highlight syntax, auto dent, autofiling etc etc.

like LaRoze gedit looks nice, the picture you put in, i like :)
but the problem its how can i configure like that?
 thnx

---

### Post by LaRoza on 2008-03-29
> **jubej said:**
> now the question is:

can someone please help me to setup VIM for C programming? like highlight syntax, auto dent, autofiling etc etc.

like LaRoze gedit looks nice, the picture you put in, i like :)
but the problem its how can i configure like that?
 thnx

**Vim**
Run this command:

```

sudo aptitude install vim

```

Put this in .vimrc, or make one if you don't have it in your home directory:

> 
[noparse]
" File: _vimrc             
" Version: 1
" Author: Seth Mason
" Created: 19 Nov 2003 10:20:19
" Last-modified: 17 Mar 2008 03:40:13 PM
" All my Vim commands for the taking
" Works on cygwin but not very well on unix machines...still trying to figure
" it out


" Use Vim settings, rather then Vi settings (much better!).
set nocompatible

" Turn on the verboseness to see everything vim is doing.
"set verbose=9

" allow backspacing over everything in insert mode
set backspace=indent,eol,start

" I like 4 spaces for indenting
set shiftwidth=4

" I like 4 stops
set tabstop=4

" Spaces instead of tabs
set expandtab

" Always  set auto indenting on
" set autoindent

" select when using the mouse
set selectmode=mouse


" do not keep a backup files 
set nobackup
set nowritebackup

if has('gui_running')
    " i like about 80 character width lines
    set textwidth=78
    " Set 52 lines for the display
    set lines=52
    " 2 for the status line.
    set cmdheight=2
    " add columns for the Project plugin
    set columns=110
    " enable use of mouse
    set mouse=a
    " for the TOhtml command
    let html_use_css=1
endif

" keep 50 lines of command line history
set history=50  

" show the cursor position all the time
set ruler       

" show (partial) commands
set showcmd     

" do incremental searches (annoying but handy);
set incsearch 

" Show  tab characters. Visual Whitespace.
set list
set listchars=tab:>.

" Set ignorecase on
set ignorecase

" smart search (override 'ic' when pattern has uppers)
set scs

" Set 'g' substitute flag on
" set gdefault

" Set status line
set statusline=[%02n]\ %f\ %(\[%M%R%H]%)%=\ %4l,%02c%2V\ %P%*

" Always display a status line at the bottom of the window
set laststatus=2

" Set vim to use 'short messages'.
" set shortmess=a

" Insert two spaces after a period with every joining of lines.
" I like this as it makes reading texts easier (for me, at least).
set joinspaces

" showmatch: Show the matching bracket for the last ')'?
set showmatch

" allow tilde (~) to act as an operator -- ~w, etc.
set notildeop


" Java specific stuff
let java_highlight_all=1
let java_highlight_debug=1
let java_ignore_javadoc=1
let java_highlight_functions=1
let java_mark_braces_in_parens_as_errors=1

" highlight strings inside C comments
let c_comment_strings=1

" Commands for :Explore
let g:explVertical=1    " open vertical split winow
let g:explSplitRight=1  " Put new window to the right of the explorer
let g:explStartRight=0  " new windows go to right of explorer window


if has("gui")
  " set the gui options to:
  "   g: grey inactive menu items
  "   m: display menu bar
  "   r: display scrollbar on right side of window
  "   b: display scrollbar at bottom of window
  "   t: enable tearoff menus on Win32
  "   T: enable toolbar on Win32
  set go=gmr
  set guifont=Courier
endif

" Switch syntax highlighting on, when the terminal has colors
" Also switch on highlighting the last used search pattern.
if &t_Co > 2 || has("gui_running")
  syntax on
  set hlsearch
endif




" ************************************************************************
" C O M M A N D S
"

"switch to directory of current file
command! CD cd %:p:h

" ************************************************************************
" K E Y   M A P P I N G S
"
map <Leader>e :Explore<cr>
map <Leader>s :Sexplore<cr> 

" pressing < or > will let you indent/unident selected lines
vnoremap < <gv
vnoremap > >gv

" Don't use Ex mode, use Q for formatting
map Q gq

" Make p in Visual mode replace the selected text with the "" register.
vnoremap p <Esc>:let current_reg = @"<CR>gvs<C-R>=current_reg<CR><Esc>

" Make tab in v mode work like I think it should (keep highlighting):
vmap <tab> >gv
vmap <s-tab> <gv

" map ,L mz1G/Last modified:/e<Cr>CYDATETIME<Esc>`z
map ,L    :let @z=TimeStamp()<Cr>"zpa
map ,datetime :let @z=strftime("%d %b %Y %X")<Cr>"zpa
map ,date :let @z=strftime("%d %b %Y")<Cr>"zpa

" Map <c-s> to write current buffer.
map <c-s> :w<cr>
imap <c-s> <c-o><c-s>
imap <c-s> <esc><c-s>

" Buffer naviation
map <M-Left> :bprevious<CR>
map <M-Right> :bnext<CR>


" Select all.
map <c-a> ggVG

" Undo in insert mode.
imap <c-z> <c-o>u

" Load my color scheme 
" colorscheme slack

" ************************************************************************
" B E G I N  A U T O C O M M A N D S
"
if has("autocmd")

  " Enable file type detection.
  " Use the default filetype settings, so that mail gets 'tw' set to 72,
  " 'cindent' is on in C files, etc.
  " Also load indent files, to automatically do language-dependent indenting.
  filetype plugin indent on

  " When editing a file, always jump to the last known cursor position.
  " Don't do it when the position is invalid or when inside an event handler
  " (happens when dropping a file on gvim).
  autocmd BufReadPost *
    \ if line("'\"") > 0 && line("'\"") <= line("$") |
    \   exe "normal g`\"" |
    \ endif

  " Normally don't automatically format 'text' as it is typed, only do this
  " with comments, at 79 characters.
  au BufNewFile,BufEnter *.c,*.h,*.java,*.jsp set formatoptions-=t tw=79

  " add an autocommand to update an existing time stamp when writing the file 
  " It uses the functions above to replace the time stamp and restores cursor 
  " position afterwards (this is from the FAQ) 
  autocmd BufWritePre,FileWritePre *   ks|call UpdateTimeStamp()|'s


endif " has("autocmd")

" GUI ONLY type stuff.
if has("gui")
  :menu &MyVim.Current\ File.Convert\ Format.To\ Dos :set fileformat=dos<cr> :w<cr>
  :menu &MyVim.Current\ File.Convert\ Format.To\ Unix :set fileformat=unix<cr> :w<cr>
  :menu &MyVim.Current\ File.Remove\ Trailing\ Spaces\ and\ Tabs :%s/[	]*$//g<cr>
  :menu &MyVim.Current\ File.Remove\ Ctrl-M :%s/^M//g<cr>
  :menu &MyVim.Current\ File.Remove\ All\ Tabs :retab<cr>
  :menu &MyVim.Current\ File.To\ HTML :runtime! syntax/2html.vim<cr>
  " these don't work for some reason
  ":amenu &MyVim.Insert.Date<Tab>,date <Esc><Esc>:,date<Cr>
  ":amenu &MyVim.Insert.Date\ &Time<Tab>,datetime <Esc><Esc>:let @z=YDATETIME<Cr>"zpa
  :amenu &MyVim.Insert.Last\ &Modified<Tab>,L <Esc><Esc>:let @z=TimeStamp()<CR>"zpa
  :amenu &MyVim.-SEP1- <nul>
  :amenu &MyVim.&Global\ Settings.Toggle\ Display\ Unprintables<Tab>:set\ list!	:set list!<CR>
  :amenu &MyVim.-SEP2- <nul>
  :amenu &MyVim.&Project :Project<CR>

  " hide the mouse when characters are typed
  set mousehide
endif

" ************************************************************************
" A B B R E V I A T I O N S 
"
abbr #b /************************************************************************
abbr #e  ************************************************************************/

abbr hosts C:\WINNT\system32\drivers\etc\hosts

" abbreviation to manually enter a timestamp. Just type YTS in insert mode 
iab YTS <C-R>=TimeStamp()<CR>

" Date/Time stamps
" %a - Day of the week
" %b - Month
" %d - Day of the month
" %Y - Year
" %H - Hour
" %M - Minute
" %S - Seconds
" %Z - Time Zone
iab YDATETIME <c-r>=strftime(": %a %b %d, %Y %H:%M:%S %Z")<cr>


" ************************************************************************
"  F U N C T I O N S
"

" first add a function that returns a time stamp in the desired format 
if !exists("*TimeStamp")
    fun TimeStamp()
        return "Last-modified: " . strftime("%d %b %Y %X")
    endfun
endif

" searches the first ten lines for the timestamp and updates using the
" TimeStamp function
if !exists("*UpdateTimeStamp")
function! UpdateTimeStamp() 
   " Do the updation only if the current buffer is modified 
   if &modified == 1 
       " go to the first line
       exec "1" 
      " Search for Last modified: 
      let modified_line_no = search("Last-modified:") 
      if modified_line_no != 0 && modified_line_no < 10 
         " There is a match in first 10 lines 
         " Go to the : in modified: 
         exe "s/Last-modified: .*/" . TimeStamp()
     endif
 endif
 endfunction
endif
[/noparse]


(Most of this stuff I never use, but I got it from some site and I pruned all the stuff that would cause problems in Linux.)

**Gedit**

Search in Synaptic (System->Administration->Synaptic Package Manager) for gedit plugins. (gedit-plugins)

Go to Edit-Preferences and plugins (or something like that, mines in Spanish) and turn on the ones you want. (To be consistant with the .vimrc, set it also to have four space tabs and spaces instead of tabs)

You can have a bunch of plugins, use the ones you like.

---

### Post by jubej on 2008-03-29
wow thnx that really make vim more functionable...LaRoze you are a great help. thnx a lot i appreciate that.

---

### Post by LaRoza on 2008-03-29
> **jubej said:**
> wow thnx that really make vim more functionable...LaRoze you are a great help. thnx a lot i appreciate that.

No problem.

(Don't tell anyone, but I just make it up as I go. For everything else, I just use wikipedia...)

---

### Post by Sinkingships7 on 2008-03-30
> **LaRoza said:**
> No problem.

(Don't tell anyone, but I just make it up as I go. For everything else, I just use wikipedia...)


lulz

---

