---
title: "Custom VIM syntax highlighting - which are normal, constants, etc. ?"
date: 2009-11-20
forum: Programming Talk
---

### Post by Slimbo on 2009-11-20
```
highlight Normal guibg=grey90
highlight Constant gui=NONE guibg=grey95
```As an example, the code below - how do I know which part of the code is what ? I mean, **int** and **using** ( C++ ) are now light yellow, which means, they are almost invisible if my terminal background is set to white.
Any tips or advices on how to configure syntax highlighting for a light background ( from your own experience and preferences ) ?

---

### Post by stylishpants on 2009-11-20
Did you already try 

```
:set background=light
```

I think this is usually the default, but maybe you unknowingly have a vimrc that sets it to dark.

---

### Post by Slimbo on 2009-11-20
> **stylishpants said:**
> Did you already try 

```
:set background=light
```I think this is usually the default, but maybe you unknowingly have a vimrc that sets it to dark.

I think you missed the point. Background is white :) The problem is that some of the code elements are in yellow or light green, which makes them hard to read.
The question is more like a theory - what VIM understands with the keyword Normal, Constant, etc.!

Configuration A ( default ):
```
[COLOR=Yellow]using[/COLOR] [COLOR=Lime]namespace[/COLOR] std;
```Configuration B ( I need this but I don't know how to achieve it ):
```
[COLOR=Blue]using[/COLOR] [COLOR=DarkGreen]namespace[/COLOR] std;
```

So .. how can I tell VIM to change the color for **using** *keyword *?

---

### Post by stylishpants on 2009-11-20
I guess you are assuming that the command I gave you sets the background to be light.  

Actually, it tells vim that the terminal background is light, since this is information that vim cannot get for itself.

The reason to set this is that vim then adjusts the syntax highlighting to a set of colors that is readable on a light background.

This is much easier than setting all the individual highlighting elements yourself.

Did you try the command?

---

### Post by Slimbo on 2009-11-20
> **stylishpants said:**
> I guess you are assuming that the command I gave you sets the background to be light.  

Actually, it tells vim that the terminal background is light, since this is information that vim cannot get for itself.

The reason to set this is that vim then adjusts the syntax highlighting to a set of colors that is readable on a light background.

This is much easier than setting all the individual highlighting elements yourself.

Did you try the command?

I tried it and nothing changed - that's why I assumed it sets the background to white or whatever light could be and changes are invisible because I already have a white background.

---

### Post by stylishpants on 2009-11-20
The next thing to try is colorschemes.

Enter```
 :colorscheme 
```
with a space after it, then hit tab to see a list of available colorschemes.  If you find one that works for you, add that command to your .vimrc.

This is still easier than tracking down all the highlight groups that you can't see and setting them individually.


To set them individually, learn about the highlight command.

To see a list of all currently defined highlight groups, enter the :hi command and hit enter.
To redefine one of them, use a command like the following:
```
:hi CppOperator term=standout ctermfg=15 ctermbg=1 guifg=#ffffff guibg=#800000
```

The "CppOperator" part is the name of the highlight group.  I don't know what highlight group 'using' is in, you'll have to figure that out.

You can copy the remainder of the command from one of the other highlight groups, it's fairly self explanatory.

Use :help highlight for more information.

---

### Post by Slimbo on 2009-11-20
Thank you - [COLOR=DarkGreen]colorscheme[/COLOR] seems to be the easiest way out. Everything seems to be fine now :)

---

