---
title: "Python and vim syntax highlighting"
date: 2006-09-22
forum: Programming Talk
---

### Post by NoTiG on 2006-09-22
Hey, ive been running edgy and they stripped the vim down to "vim mini" or something... and it doesnt work with syntax highlighiting. so i installed vim-full by synaptic... but there was no .vim/syntax folder so i had to create it... when i insert this file from here : [http://www.vim.org/scripts/script.php?script_id=790](http://www.vim.org/scripts/script.php?script_id=790)

it doesnt seem to be working like it used to be. any suggestoins ?

---

### Post by f0rmula on 2007-02-13
If anyone did figure out how to get syntax highlight working, could you let me know please. 

I'm having exactly the same problem.

Cheers,

James

---

### Post by jblebrun on 2007-02-13
Do you have the line

```

syntax on

```

in your .vimrc file?

---

### Post by colmcd on 2009-02-20
I discovered that in /etc/vim/vimrc I was able to uncomment the line Syntax = on. Sadly I also uncommented the line background = dark which has lead to bright yellow highlighting of key words (eek). 

I have no idea why Syntax = on would be commented. I recommend all users to uncomment it.

---

### Post by alexmurray on 2009-02-21
You should really create your own .vimrc file rather than editing the system wide on in /etc. Simply do the following:

echo 'syntax on' > ~/.vimrc

Then you have a vim configuration file for just your user with syntax highlighting turned on.

---

### Post by ynef on 2009-02-21
alexmurray: you might want to change the destructive output redirection (>) to the appending output redirection (>>) in your post, so nobody accidentally overwrites their .vimrc by following your tip without thinking.

---

### Post by lloyd_b on 2009-02-21
> **colmcd said:**
> I discovered that in /etc/vim/vimrc I was able to uncomment the line Syntax = on. Sadly I also uncommented the line background = dark which has lead to bright yellow highlighting of key words (eek). 

I have no idea why Syntax = on would be commented. I recommend all users to uncomment it.

I believe it's commented by default because the default "vim-tiny" doesn't support syntax highlighting.  It must be presumed that if someone goes through the effort of installing "vim" or "vim-full", then they'll know how to customize their "~/.vimrc" file.

Though it would make more sense if the "vim" and "vim-full" package overrode the "/etc/vim/vimrc" with a version that makes more sense for those packages...

Lloyd B.

---

### Post by drubin on 2009-02-21
> **colmcd said:**
> I discovered that in /etc/vim/vimrc I was able to uncomment the line Syntax = on. Sadly I also uncommented the line background = dark which has lead to bright yellow highlighting of key words (eek). 

I have no idea why Syntax = on would be commented. I recommend all users to uncomment it.

Because syntax support doesn't come with the package "vim" by default. It is provided with another vim-* package I think it might be vim-common but I could be wrong.

If you have that line enabled by default with out having the correct package of vim it will through an error every time you open a file hardly more productive then just for each user to copy their *standard* .vimrc file :)

---

### Post by geirha on 2009-02-21
> **colmcd said:**
> Sadly I also uncommented the line background = dark which has lead to bright yellow highlighting of key words (eek). 


Change it to ```
set background=light
``` if your terminal has a bright background (like the default white of gnome-terminal). I usually set it to dark and change the color of the terminal instead. I find it much better to look at white on black than black on white.

---

### Post by drubin on 2009-02-21
> **geirha said:**
> Change it to ```
set background=light
``` if your terminal has a bright background (like the default white of gnome-terminal). I usually set it to dark and change the color of the terminal instead. I find it much better to look at white on black than black on white.

+1 I always change it to black. Think of it as being in a tty but that can be moved around the screen... :)

---

### Post by dandaman0061 on 2009-02-21
Just to chip in a bit on the conversation, I found that the default python synatx highlighting doesn't recognize a lot of when it should indent and whatnot, but I found this website ([http://www.vex.net/~x/python_and_vim.html]("http://www.vex.net/~x/python_and_vim.html")) which has some very good tips and settings to put in your ~/.vimrc file.

Specifically this part:

```

autocmd BufRead *.py set smartindent cinwords=if,elif,else,for,while,try,except,finally,def,class

```

Which lets you specify the words for which an indent should follow.

---

