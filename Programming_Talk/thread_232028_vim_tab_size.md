---
title: "vim tab size"
date: 2006-08-08
forum: Programming Talk
---

### Post by cope on 2006-08-08
hey guys, 

i use jedit when programming or gedit when editing configs, but sometimes its just quicker and easier to do things in vim since the load time is so small..

i'm having a problem setting the option to change the tab size from 8 to 4. 
when i try (even when sudo) it complains about "buftype option is set"

buftype isn't set its ""
am i supposed to be doing something else? I guess the question is how the hell do i edit vim options?

---

### Post by slakkie on 2006-08-08
```

:set tabstop=4  # set tabstop at 4
:set ts=8       # set tabstop at 8

```

Or put in in your ~/.vimrc

---

### Post by wjp.reg on 2006-08-08
> **cope said:**
> hey guys, 

i use jedit when programming or gedit when editing configs, but sometimes its just quicker and easier to do things in vim since the load time is so small..

i'm having a problem setting the option to change the tab size from 8 to 4. 
when i try (even when sudo) it complains about "buftype option is set"

buftype isn't set its ""
am i supposed to be doing something else? I guess the question is how the hell do i edit vim options?

> Tab Settings
(to set the tab-size, type :set ts=2 (or whatever number you want)
(also, for tabbing-size, set shiftwidth (>) by typing :set sw=2Navigation

[http://simpletutorials.com/w3/index.php?pagename=Vim%20Reference]("http://simpletutorials.com/w3/index.php?pagename=Vim%20Reference")

Works on my system. (don't forget the leading ":" colon

cheers

---

### Post by cope on 2006-08-08
thanks guys, i didn't realise vim was so open to customisation..
i've downloaded a few tutorials, and even a couple of plugins! 

very impressed, i can see what all the hype is about.. i might put jedit aside for the moment and see how fast i can get writing in vim..

---

