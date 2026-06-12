---
title: "vim/gvim teething issues"
date: 2012-08-22
forum: Programming Talk
---

### Post by thaitang on 2012-08-22
I am trying to make the change from long-time gedit user to vim, er gvim and having some teething problems I hope are just that.

two of the great things about gedit I find indispensable is the snippets and ext tools plugins. Discovered UltiSnips plugin for vim and it is ok, far from ideal. I can't seem to enter snippets without preceding them with a space first, even though the previous character is generally a <> bracket. Are there any snippet managers available that work more like gedit's, that allow a snippet to tab forward immediately after a > bracket?

gedit's ext tools is great for entering little bash scripts, but I cannot seem to figure out how to do similar with vim. Do I need to port all of my gedit ext tool scripts into individual bash scripts and run them from my ~/bin dir? Because I have too many to remember and the menu in gedit listing all of the scripts has always seemed rather convenient. Plus, running scripts from within gedits ext tool menu, the script acts on the current file without any need to bother specifying paths. 

Like I said I hope most of my issues are simply teething probs. But I generally edit a lot of text using sed from the terminal and somehow the :%s option in vim seems less than adequate. I can't seem to figure how to invoke the -r option for regex. Is that possible. I would be just as comfortable, actually perhaps more so if I could just open a terminal in the current dir of a file I am editing and run sed/perl scripts that way. In gedit I have always remapped C-t (ctrl+t) to open a terminal in the current directory of the current file. Is there any way to do that using gvim?

Those seem to be my biggest caveats atm. I am enjoying the noticeable performance efficiency of gvim over gedit, however my own editting efficiency is taking a serious nose dive atm; but if I could get a few of these issues resolved I think I might get back on track using gvim.

Oh yeah, one other thing. I got tabs sort of working in gvim...but, for some reason, if I open a new nautilus/thunar session to open a new file then it opens in a new gvim window and does not open in a new tab of the already existing gvim window. Any ideas on that would be great also. I love tabs!

I also forgot to ask about vim's clipboard. I seem to be getting it confused with buffers. Does vim have a clipboard that stores multiple copy/yanks and cuts? I use parcellite precisely because I like to keep a long buffer of copy/cut stuff that I tend to need later on. Everytime I try to find info on any functionality like this in vim I seem to get pointed to buffers, which seem to be alternate simultaneously being managed by vim. 

any help/suggs appreciated.
cheers,
tt

---

