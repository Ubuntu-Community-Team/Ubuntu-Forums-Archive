---
title: "Vim key mapping acts... strangely"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by linuxtalk on 2012-12-27
********************************************************************************************* [COLOR=Red]UPDATE[/COLOR] ***

I found the solution. When using Vim in gnome-terminal, it seems the angle bracket notation is not used. I.e. <Esc> would not represent the escape key. To represent a special key, first start by pressing Ctrl+v. Then press the key (or key combination) you want to represent. For Escape, you'd type Ctrl+v then press the escape key.

*********************************************************************************************************

I've been reading up on how to map keys in Vim. So, I went ahead and tried to make CTRL+i indent the current line and then move to the end of the next line:

```
map <C-i> 0i<Tab><Esc>j$
```This didn't work so i tried...

```
map q 0i<Tab><Esc>j$
```This sort of worked, but on clicking 'q', Vim moved to the start of the line, entered insert mode, and wrote "<Tab><Esc>j$"

Why is Vim not reading the angle bracketed terms as special keys?

---

### Post by linuxtalk on 2012-12-27
To clarify, Vim reads <Esc>, <Tab> and all of those characters *literally*. Why does it do this? And, how do I fix it?

---

