---
title: "vi color schemes aren't working :("
date: 2008-08-27
forum: New to Ubuntu
---

### Post by lunaz on 2008-08-27
i'm downloading them from [this site](http://www.cs.cmu.edu/~maverick/VimColorSchemeTest/) and making the name.vim files in /home/luna/.vim/colors, then using :colors name or :colorscheme name commands in vim, but  they don't work :( 

sometimes they give me like 3 screens full of errors & other times they just change the colors around a bit but not to dw_green 

would it help to post /home/luna/.vimrc or screenshots?

---

### Post by hubie on 2008-08-28
What happens if you change to one of the simple color schemes that you didn't download, something like [FONT="Courier New"]:colorscheme blue[/FONT] ?

Do you also have the following two lines in your .vimrc:
[FONT="Courier New"]set nocompatible
syntax on[/FONT]

Do you have the problem in vim, or in both vim and gvim?

---

### Post by lunaz on 2008-08-28
i have nocompatible and syntax both on in .vimrc. tried using :colors blue, :colors desert, :colors morning, and they all worked, but the downloaded ones in /home/luna/.vim/colors don't work right, the colors come out wrong. it hapeens when i use vi or vim to open the file. gvim works fine t ho.

> **hubie said:**
> What happens if you change to one of the simple color schemes that you didn't download, something like [FONT="Courier New"]:colorscheme blue[/FONT] ?

Do you also have the following two lines in your .vimrc:
[FONT="Courier New"]set nocompatible
syntax on[/FONT]

Do you have the problem in vim, or in both vim and gvim?

---

### Post by hubie on 2008-08-29
If they aren't too long, could you post your .vimrc and .gvimrc files?

You could also try temporarily copying your .vimrc file to a .gvimrc file, run gvim and see if the colors still work.  Be careful that you don't overwrite your original .gvimrc file though.

---

### Post by lunaz on 2008-08-30
this is my vimrc file. i didn't have a gvimrc, so not sure why the colors worked there but not on vim.

i copied the .vimrc file to a .gvimrc file, then tested both again and gvim still works, vim still doesn't.
```

" The set nocompatible  setting makes vim  behave in a more useful way
set nocompatible

" Turn on line numbering. Turn it off with "set nonu" 
set nu 

" Set syntax on
syntax on

" Indent automatically depending on filetype
filetype indent on
set autoindent

" Case insensitive search
set ic

" Higlhight search
set hls

" Wrap text instead of being on one line
set lbr

" Don't keep backup file
set nobackup

"Incremental search
set incsearch

```

---

### Post by hubie on 2008-08-31
I think you might have an issue with one of your terminal settings.  You can try adding to your .vimrc file:

[FONT="Courier New"]set t_Co=256[/FONT]

This tells the terminal to use 256 colors.  If that looks screwy, try 16.

What kind of errors are you getting when you try loading a color scheme?

---

### Post by lunaz on 2008-09-01
setting the t_Co doesn't make a difference. the default schemes still work but i get strange colors with the ones i downloaded.

the errors i got were from typing the scheme name wrong when using :colors, figured out how to type em right :P

---

### Post by hubie on 2008-09-01
I've been poking around on this, and apparently some color schemes are written only for the term or the gui (or both).  I found [this post]("http://ubuntuforums.org/showpost.php?p=4093978&postcount=5") that explains that the terminal can only handle 8 background and 16 foreground colors, while the gui can handle 16M background and foreground.  

I downloaded the dw_colors which you referred to and opened dw_green and in the header it says that it is only a gui color scheme.  If you open up one of those files you'll see only gui, guibg, and guifg settings.  If you open up, say, morning.vim you'll see in addition to the gui settings, settings for term, ctermbg, and ctermfg.

A good question, if anyone knows the answer, is how do you know before you download them, to what the color scheme applies.  It would be handy if you can select based on that.

---

