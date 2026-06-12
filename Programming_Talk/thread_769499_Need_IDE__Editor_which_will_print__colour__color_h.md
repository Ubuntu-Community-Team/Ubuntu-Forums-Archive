---
title: "Need IDE / Editor which will print  colour / color highlights"
date: 2008-04-26
forum: Programming Talk
---

### Post by Le Hibou on 2008-04-26
Well, I'm an old fashioned guy and prefer to work from pieces of paper (I *really* miss the old fanfold!) - so what I am looking for is an IDE or text editor with usual features such as code highlighting, multiple language support (specifically, for now, Python, HTML, CSS), that will also print the pretty colours that I see on the screen. And also the monospace font (10 characters per inch please!), and the faint lines for marking indentation levels, and so on. Notepad++ does it if I remember correctly from the days when I was sleeping with the enemy...:), but it's a windows only program - I've tried Bluefish and Geany, but they both seem to simply shell out to an "lp myfile.xxx" or similar command :(

Any suggestions much appreciated!

---

### Post by Natr0n on 2008-04-26
Vim will do it if you feel like learning it. But, I don't see why bluefish or geany wouldn't be able to print colors. Unfortunately, I don't use either, so I can't really help with getting that to work.

---

### Post by Le Hibou on 2008-04-26
Thanks I'll give Vim a try.

Bluefish actually doesn't come with a print function, but you can add one yourself, as a shell command: "lp -dPrintername %f", and Geany has the good manners to show you what it is doing when you hit print, which is "lp Myfilename" or something like it. In both cases, it is just calling the shell command "lp" to print the original text file, which of course contains no colouring information. (I include this just for info for anyone else who may read this thread).

---

### Post by lemuriaX on 2008-04-26
Wouldn't Gedit be able to do this?

---

### Post by Natr0n on 2008-04-26
You should probably run```
$ vimtutor
```first if you don't have any experience with Vim. It can be challenging to get used to at first. By the way, the command for printing from Vim is```
<ESC>:hardcopy<RET>
```
EDIT: To get highlighting you need to type```
<ESC>:syntax on<RET>
```from within Vim.

---

### Post by Natr0n on 2008-04-26
> **lemuriaX said:**
> Wouldn't Gedit be able to do this?
Yeah, and that would probably be easier than trying to learn Vim. I only suggested Vim because that's what I use.

---

### Post by lemuriaX on 2008-04-26
Vim is awesome - I haven't really learned it much yet. 

I used to use Notepad2 on Windoze (still do sometimes) and have mainly used Gedit in Ubuntu so far to edit code with color highlighting. It looks like it will print with the color. It's pretty simple compared to everything Vim can do but might do the trick for what you want.

---

### Post by Le Hibou on 2008-04-26
Just tried Vim, and it prints the colours fine.

But then so does Gedit! 

Guess my mind is still in the other world, I kind of assumed that Gedit was the Linux equivalent of the long gone and unlamented Notepad.

However, that still leaves the issue of the structural highlighting that Bluefish or Geany give you, e.g. like being able to see invisible characters such as tabs, or have faint vertical lines showing where your indents line up... Autocompletion too is a nice to have... even if it can be irritating at times.

Vim looks like it quite a feature rich thing, perhaps it could be persuaded to do it... and as I still hark back to the days before Unix became an anagram, the cryptic commands of Vim are just like coming home after twenty years absence, to good old vi!

I like the IDEs, but just want one which will print the screen in the same way as it displays it.:?

---

### Post by LaRoza on 2008-04-26
> **Le Hibou said:**
> 
Guess my mind is still in the other world, I kind of assumed that Gedit was the Linux equivalent of the long gone and unlamented Notepad.

However, that still leaves the issue of the structural highlighting that Bluefish or Geany give you, e.g. like being able to see invisible characters such as tabs, or have faint vertical lines showing where your indents line up... Autocompletion too is a nice to have... even if it can be irritating at times.

Vim looks like it quite a feature rich thing, perhaps it could be persuaded to do it... and as I still hark back to the days before Unix became an anagram, the cryptic commands of Vim are just like coming home after twenty years absence, to good old vi!

I like the IDEs, but just want one which will print the screen in the same way as it displays it.:?

All the Linux text editors surpass notepad in every way. 

Vim is worth learning, and is my editor of choice. It has a learning curve, but once you know it...(When I use other editors, my code often has ":wq" at the end.)

I don't know of any editor that will print non printing characters.

---

### Post by coolkid5 on 2008-04-26
> **Le Hibou said:**
> Geany has the good manners to show you what it is doing when you hit print, which is "lp Myfilename" or something like it. In both cases, it is just calling the shell command "lp" to print the original text file, which of course contains no colouring information. (I include this just for info for anyone else who may read this thread).

I'm not sure what you are doing to print in geany, but it prints color for me.  I don't have a printer hooked up to my machine but the pdf's that geany outputs are in color.  I would assume the same is true for normal printing.

---

### Post by murmel on 2008-04-26
This is a nice easy way of getting vim to look and feel the right when programming. (This conf is for c++)

This is the code for ~/.vimrc_cpp
```

syntax enable
set number
filetype on
filetype plugin on
set tabstop=4
set softtabstop=4
set shiftwidth=4
set noexpandtab
set smarttab
set noerrorbells
set nocompatible
set ai
set si
set cindent
set nowrap
set incsearch
set showmatch
set mat=5
set wrap
set hls
set cul
set wrapscan
set sol
syn on
set syn=cpp
```

Now just edit ~/.bashrc and add:
```
alias vim.cpp='vim -u ~/.vimrc_cpp'
```

I think it looks quite nice, tbh. :)

---

### Post by Le Hibou on 2008-04-26
> **murmel said:**
> 

I think it looks quite nice, tbh. :)

Yeah, thats a lot better. Seems to work fine on CSS & HTML too.

---

### Post by Le Hibou on 2008-04-27
Thanks coolkid5, Geany does the job. 

Not sure where I went wrong before, I could *swear* it didn't work when I tried it, maybe I'd screwed something else up along the way, or perhaps the psychotic effects of too much caffeine are catching up with me...

---

