---
title: "vim help"
date: 2005-10-13
forum: Programming Talk
---

### Post by ArthurHeng on 2005-10-13
If I copied some text from outside of vim using ctrl+v, is there a way to paste it in vim using 'p'?

Also, if I copied some text in vim using 'yy', is there a way to paste it outside of vim using ctrl+v?

You know, it'll be faster to try out codes found on the net instead of retyping all of em...

Thanks in advance.

---

### Post by heimo on 2005-10-13
At least if you have vim running in gnome-terminal, you can use ctrl+shift+v to paste. Personally I use paint-and-middle-click-to-paste method both ways.

---

### Post by ArthurHeng on 2005-10-13
Thanks, but Im using Konsole, (yes in Ubuntu, i know its weird) is there a way to do it in konsole?

---

### Post by jerome bettis on 2005-10-13
click the left and right mouse button at the same time to copy, do it again to paste. also you can press shift+insert in vim to paste when you're in insert mode. ctrl+insert might copy but i've never really tried it.

yy, dd, p etc etc are internal vim commands and the text in that buffer can't be seen or modified from oustide vim. i might be wrong on this though but i think that's the way it is. 

try using gvim instead, the menus are nice in case you don't know all 1000000 keystrokes. and when you resort to using a menu get in the habit of looking at the short cut, and try to remember it.

also if you're using the real console (x isn't running) you can use gpm to have the mouse so you can use left+right click to copy/paste. unfortunately the scroll wheel doesn't let you scroll up in the ouput. i would love to find a way to make that work.

---

### Post by ltmon on 2005-10-13
If you are using a graphical vim (gvim, kvim or xvim) it can interact with the outside clipboard (i.e. Xwindows) in this way.  Otherwise you are stuck with whatever the Konsole can do.

L.

---

### Post by GozzoMan on 2005-12-28
Hi all,
   I'm a bit confused by now.

I'm using gvim in Gnome/Ubuntu, and what I like to obtain is to use cntrl+c/cntrl+v to copy/paste from and to other applications just like gvim itself allow in its windows version.

I've been able to use the both left and right mouse button, but it seems a distinct clipboard from the cntrl+c/v one (I mean a different buffer). Also I've been able to use shift+insert to paste from the "cntrl+c/v buffer" in gvim, but cntrl+ insert to copy from doesn't seem to work.

In gvim's own menus the shortcut are given as:

Cut: "+x
Copy: "+y
Paste: "+gP

What does it means? I.e. what key does " stand for?

Thank you very much,

---

### Post by Refrozen on 2005-12-28
You know, the [vim documentation](http://manlib.com/man/230) is really good... read it.

---

### Post by oxEz on 2005-12-28
" means that the action can be performed. For example, if there is no text in the clipboard, there will be no " next to 'Paste'.

---

### Post by GozzoMan on 2005-12-29
[QUOTE=Refrozen]You know, the [vim documentation](http://manlib.com/man/230) is really good... read it.[/QUOTE]

Oh well, good point.
Anyway the online documentantion (:help) proved to be more fitting to the problem than the man page you referenced. Please find my results below.


[QUOTE=oxEz]" means that the action can be performed. For example, if there is no text in the clipboard, there will be no " next to 'Paste'.[/QUOTE]

First of all, thanks for the answer oxEz.

Pardon me, I'm probably misunderstanding something, but it doesn't seem this way. (Hope to not sound unpolite, maybe you meant something different.)
The " seems to be present even if there's nothing in the clipboard, and most important if I _literallly_ press "+gp in _command mode_, voila' the content is pasted.

The point here, according to documentation, seems to be that " is used to reference registers, of which + is the gui-wide clipboard (:reg to see registers).

The tricky part for me was that in the windows version of gvim the paste action has to be done in _insert mode_, hence my confusion and the fail of my previous attempts.

Now, I imagine that to have cntrl+v working in command mode, I simply need to remap the key combination (I've gone for :map <C-V> "+gP), but any idea if there's a way to have it work in insert mode and command line, just like windows version? (If I go for :map! <C-V> "+gP, it pastes '"+gP' not the content of the clipboard.)

Again, thank you all,

---

### Post by GozzoMan on 2005-12-29
[QUOTE=GozzoMan], but any idea if there's a way to have it work in insert mode and command line, just like windows version? (If I go for :map! <C-V> "+gP, it pastes '"+gP' not the content of the clipboard.)[/QUOTE]

Sorry to reply myself (last post, I promise <:p): the cntrl+shift+v that heimo suggested works both in insert mode and in the command line (I mean after a : in command mode).
Anyway to just use cntrl+v (in both) you can use :map! <C-v> <C-R>+ (note the !)

So my .vimrc is now:

:map <C-v> "+gP
:map <C-c> "+y
:map <C-x> "+x
:map! <C-v> <C-R>+

I still lack a way to copy while in insert/command line mode (cntrl+shift+c is no use), but it seems to me less useful.

Cheers,

---

### Post by ow50 on 2005-12-29
I have Vim configured to use the X clipboard with the standard keyboard shortcuts. Here's what it took:
```
function! Paste(mode)
  if a:mode == "v"
    normal gv
    normal "+P
    normal l
  elseif a:mode == "i"
    set virtualedit=all
    normal `^"+gP
    let &virtualedit = ""
  endif
endfunction

vnoremap <C-X> "+d
vnoremap <C-C> "+y
nnoremap <C-V> "+gPl
vnoremap <C-V> :<C-U>call Paste("v")<CR>
inoremap <C-V> <C-O>:call Paste("i")<CR>
```
Hope it helps.

---

### Post by GozzoMan on 2005-12-29
Thank you very much, ow50 :D

I suppose this could be material for a (brief but useful and time-saving) how to/wiki page ;)

---

### Post by xtacocorex on 2005-12-30
[QUOTE=ArthurHeng]Thanks, but Im using Konsole, (yes in Ubuntu, i know its weird) is there a way to do it in konsole?[/QUOTE]

I know that you can paste into vi using the default konsole paste (shift+insert).

I'm definately going to try ow50's addition to the .vimrc file because I was messing with that out the other day (for fun) and couldn't get it working.

---

