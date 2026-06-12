---
title: "Editing C++ using vim in Ubuntu"
date: 2010-11-10
forum: Programming Talk
---

### Post by audit on 2010-11-10
I have been writing C++ programs in vim for about a month. And I now getting use to vim, but one small problem I do not know how to solve.

I set my tabs to 4 which I prefer to 8. When I start a block of code after a
"{" vim auto indents to 8--How do I change this to auto indent in 4?

Also if anyone has any vim C++ tips worth noting--Please do.

---

### Post by Simian Man on 2010-11-10
Put this in a file called "~/.exrc":
```

set ts=4
setsw=4

```

I'd also recommend using "set expandtab" which will insert spaces when you hit the tab key instead of actual tab characters.  Anyone else reading your code will thank you :).

Also "set cindent" would be a nice one to have.  This sets up auto-indentation for C-like languages.

---

### Post by shawnhcorey on 2010-11-10
To get help of the options, type:
```
:help options^M
```
where ^M means press the RETURN key.

Some options related to tabs are:
[LIST]
[*]autoindent
[*]cindent
[*]expandtab
[*]shifhtwidth
[*]shiftround
[*]smartindent
[*]softtabstop
[*]tabstop
[/LIST]

Other command you may be interested in are:
:help ^D
:help ^T
:help >>
:help <<
where  ^X means control-X

These command shift the start of the line in or out one tab stop, depending whether you are in insert mode or command mode.

---

