---
title: "VI Editor"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by mabathom on 2008-04-22
Hi guys,

I'm new to linux, I'm trying to edit files using VI. I found tutorials but copy and pasting is a real problem for me. 

What commands can I use to copy and paste. I tried the Y commands and they don't  seem to work. 

Preferable where I can use a combination like ctrl+ D, something like that.

Please help me.

---

### Post by Rocket2DMn on 2008-04-22
I don't really know anything about vi, but I have this page bookmarked if you'd like to check it out - [http://www-acs.ucsd.edu/info/vi_tutorial.shtml](http://www-acs.ucsd.edu/info/vi_tutorial.shtml)

If you just need a simple CLI text editor to edit a config file or something, you can use a preinstalled program called nano.

Good luck.

---

### Post by sdennie on 2008-04-22
Things like "yy" will only copy/paste within vim and not the system clipboard.  If you are just starting with vim, you may want to install vim-gnome (sudo apt-get install vim-gnome).  That will give you menu items along with key combinations for common tasks.  You can learn the key combinations by looking at the menus.

Edit:

Actually, it will give you a useful menu if you start vim with the command "gvim" instead of just typing "vi" or "vim".

---

### Post by The Cog on 2008-04-22
I only know a few commands (just enough to get by), but these work:
Copy current line: yy
Copy 5 lines (current and next 4): 5yy
Delete current line: dd
Delete 5 lines: 5dd
Delete current character: x
Delete 5 characters: 5x
Go to insert mode at cursor: i
Go to insert mode after cursor: a
Go to insert mode at end of line: A
Open insert mode in a new line: o 
Leave insert mode: <Esc>
Write file: :w<Enter>
Write and quit: :wq<Enter>
Quit without saving: :q!<Enter>

You might find nano easier to get along with, but I like vi because it is sure to be available on any distro, and even any unix variant.

P.S. The cursor keys don't work in insert mode in the default vi install on Ubuntu. I have read that there are better packages in the repositories, vim-full possibly, that might vix that problem.

---

### Post by joshrobinson on 2008-04-22
have you tried using nano? it might work better for you

just run ```
nano /directory/filename.extension
```
you will have to throw a sudo on there if its a file that needs permissions

---

### Post by mabathom on 2008-04-22
Hi, i did run the apt-get install v....but I still got an error that says this is not an editor command

---

### Post by sdennie on 2008-04-22
If you open up a terminal and type:

```

sudo apt-get install vim-gnome

```

That should install a version of vim that is less difficult to ease into if you use it by typing "gvim" instead of "vi" or "vim" in a terminal.  Specifically, it will allow you to select text and then use the Edit menu to copy/paste from the system clipboard.  It also shows you keystrokes that you could have used to do the same without going to the menu.

---

### Post by grahams on 2008-11-22
It is easy to copy and paste in vi using the mouse keys, rather than ctrl-c/v etc.

Hold the left mouse button (assuming you haven't reversed them), and highlight what you want to copy. Release the left button, move the cursor to where you want to paste and click the middle button (or left+right together on a 2 button mouse.

If your middle button is also a wheel, be careful not to spin it in vi as it will pick up the ctrl chars.

---

### Post by eldragon on 2008-11-22
if you wanna work around commands remember this:

commads are usually split in 3:

main command instruction
a number
a direction

so, y = yank, aka copy

if you do: y2l it will yank 2 chars to the right

l = right, h= left, j = down, k = up (related to keyboard possitions)

if you want to yank lines:
yy = yank current line

y2j = yank 2 lines below current one AND current one

j2k = yank 2 lines abouve current one AND current one.

then, to paste, use the p key

all this is done when not in insert/replace mode


if you want regular copy paste.
select with the mouse, and hit CTRL-SHIFT-C
then enter insert mode (or replace): i (or R)
move cursor where you wish to paste and hit CTRL-SHIFT-V


hope i cleared it up a bit :D

---

### Post by chazn85 on 2008-11-22
the only other suggestion would be vim, it can be installed via the repos

---

### Post by nhasian on 2008-11-22
a great way to learn to use vi(m) is to use the vimtutor.  first install:

```
sudo apt-get install vim-full
```

after its installed, simply run in the terminal *vimtutor*

---

