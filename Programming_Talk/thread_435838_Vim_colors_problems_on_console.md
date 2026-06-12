---
title: "Vim colors: problems on console"
date: 2007-05-07
forum: Programming Talk
---

### Post by alanfranz on 2007-05-07
Hello,
I'm using the latest feisty.

I'm an happy vim user, but I've got some problems with syntax highlighting. If I use gvim on X, everything is fine. All file types I load, with every possibile colorscheme, look fine and are readable.

But using it on console with syntax highlighting turned on, that's impossible. Almost every color scheme seems to use a kind of 'dark gray' (on black background!) for keywords, in any language I try!

But this strange behaviour seems to happen when using 'original' linux ttys only, not by using gterm or any other terminal emulator.

What could the matter be?

---

### Post by lloyd_b on 2007-05-07
When logged in via the console, what are the environment settings for "TERM" and "COLORTERM"?
```
env | grep TERM
```
should display both of them.

I'm guessing that the issue is with one or both of them.

Lloyd B.

---

### Post by alanfranz on 2007-05-07
on the tty, it's just TERM=linux .
no COLORTERM is set (while gterm does set it, of course).

---

### Post by lloyd_b on 2007-05-08
Okay, your TERM setting is normal (at least it's the same as on my system).  And COLORTERM  isn't set in console sessions on my system either.

You mentioned having tried the different color schemes - I'm assuming you used the ":colorscheme ..." command within vim.  Did you also try setting the "background" value?
```
:set background=dark
```
in vim.

A related question: does "ls", when used in a console session, give you colored output?  I'm curious to see if this is a vim-only issue.

Lloyd B.

---

### Post by alanfranz on 2007-05-08
> 
You mentioned having tried the different color schemes - I'm assuming you used the ":colorscheme ..." command within vim.  Did you also try setting the "background" value?
```
:set background=dark
```
in vim.


Yes, indeed, I just forgot to mention. I tried that on various colorschemes, and got no useful result. I even tried using the opposite :set background=light in order to check whether anything was switched, but no result.

> 
A related question: does "ls", when used in a console session, give you colored output?  I'm curious to see if this is a vim-only issue.


Yes, ls does give colored (and readable) output. But vim does show colors as well, e.g. my strings have one colors, function definitions have another, classes have another... the problem is that, on console, the *keywords* of a language (e.g. if... for.. assert in python, for.. do.. if in bash-scripting, most macros in tex, ecc) have a dark-gray colour when the background is black, making them almost unreadable. All other kind of text can be read perfectly.

I suspect it might be an Ubuntu bug... but I can't believe I'm the only one who uses vim with syntax highlighting on the console.

This is a list of vim-related packages I've got installed on my system:
vim
vim-common
vim-doc
vim-full
vim-gnome
vim-gtk
vim-gui-common
vim-python
vim-ruby
vim-runtime
vim-scripts
vim-tiny


I'm now trying to purge some of them in order to check if any change is introduced by an external package.

---

### Post by alanfranz on 2007-05-08
ok, I did some testing. I purged all vim and vim-related packages, I made sure there was no /etc/vim directory, and i deleted my .vimrc and .gvimrc files in my home directory.

Then I reinstalled packages from the official, main ubuntu repo:

vim
vim-common
vim-runtime
vim-tiny

which are the absolutely bare minimum for Vim with syntax highlighting on an ubuntu console.

And I still get the very same behaviour. The only thing I must say, i'm using bash instead of dash as /bin/sh.

But... are you using feisty? I'd like to have tested console-based vim on edgy or dapper, while I didn't; hence I could have spotted what the change was.

---

### Post by lloyd_b on 2007-05-08
> ok, I did some testing. I purged all vim and vim-related packages, I made sure there was no /etc/vim directory, and i deleted my .vimrc and .gvimrc files in my home directory.

Then I reinstalled packages from the official, main ubuntu repo:

vim
vim-common
vim-runtime
vim-tiny

which are the absolutely bare minimum for Vim with syntax highlighting on an ubuntu console.

And I still get the very same behaviour. The only thing I must say, i'm using bash instead of dash as /bin/sh.

But... are you using feisty? I'd like to have tested console-based vim on edgy or dapper, while I didn't; hence I could have spotted what the change was.

First, I'm running with bash.  I haven't tested anything with dash, but I would be very suprised if that makes a difference.

I am, however, running under Edgy (Feisty isn't entirely stable on this machine, so I reverted back to Edgy).  So comparing your system to mine is something of an apples-to-oranges situation.

Have you taken a look at the files in "/usr/share/vim/vim70/colors" to see what color a given scheme specifies for "Statement". 

Then take a look at the file "/usr/share/vim/vim70/syntax/syncolor.vim" and see what it specifies at a default value for "Statement".

And finally, just for the heck of it - in a console session:
```
export TERM=xterm
export COLORTERM=Terminal
```
and see what happens.

Also: in a gterm (or any xterm session)
```
export TERM=linux.
```
and see if this duplicates what you're seeing in a console session.

Lloyd B.

---

### Post by alanfranz on 2007-05-08
dear Lloyd_b,
I wish to thank you for your help, but it seems my problem is not strictly vim-related; I found out my console is not able to properly display some colours.

In fact i tried rebooting in 'safe mode', and everything worked properly! I had all the right colors! I suppose there's some strange misconfiguration happening in my system whenever X starts (or some init.d daemon is executed). Now, i've tried fiddling with console-setup and console-tools, but I haven't got permanent results (yet). I'll post a question on another forum if I need help on that, btw.

Thank you!

---

### Post by yomex on 2007-05-21
To enable vim display color by default, this thread too might be helpful: [click here]("http://ubuntuforums.org/showthread.php?t=413696")

---

### Post by alanfranz on 2007-05-21
thank you yomex, but no, I perfectly know how to enable syntax highlighting. It was a framebuffer/console issue.

---

### Post by nuky on 2007-06-27
alanfranz, I am having the same problem with my vim console colours. I was just curious to see if you fixed this or had a vague idea of how I could go about fixing it? I have also tried all the things you have mentioned earlier in your post and had no luck.
Many thanks!

---

### Post by tr333 on 2007-06-27
try setting the "TERM" variable to "xterm-color"

```
$ export TERM='xterm-color'
```

---

### Post by nuky on 2007-06-27
Hi tr333, I have already tried this too. The various TERM values I have tried include xterm, xterm-color, gnome-terminal, linux-terminal and a few others but to no avail. The best results are with xterm-color. However, even then the backgrounds do not change to match the colorscheme files at all. It just varies between black and white. 

Just to make sure, I am trying these TERM values by invoking vim using (for example):
```
 vim -T xterm-color 
```
Is this correct? Maybe this is where I am going wrong. I love vim and would really like to sort this out but not sure what else to try! :cry:

---

### Post by alanfranz on 2007-06-27
it was a kernel issue. I recompiled from a stock 2.6.20 kernel and solved everything.

Or you could try loading some framebuffer modules along with fbcon. something like

modprobe vga16fb
modprobe fbcon

you could try "vesafb" instead of vga16fb

---

