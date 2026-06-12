---
title: "[SOLVED] syntax coloring VIM"
date: 2008-09-28
forum: New to Ubuntu
---

### Post by luckydeveloper on 2008-09-28
hi all,
i am thinking of using vim as my default text editor..but when i type in it...the syntax i type are not becoming colored...why is that so.. should i change any setting... and if yes .. how do i do it

---

### Post by tonybaqain on 2008-09-28
it is simple,

when you are in vim, exit the insert mode, and type
```
:syntax on
```

and there you go, have fun :)

---

### Post by jrothwell97 on 2008-09-28
You also need to have saved the file, for example as "source.c" with the relevant extension. That way vim will know what you're coding in and how to highlight it.

---

### Post by luckydeveloper on 2008-09-28
> **tonybaqain said:**
> it is simple,

when you are in vim, exit the insert mode, and type
```
:syntax on
```

and there you go, have fun :)

when i did that... it says...

```
E319:sorry, the command is not available in this version
```

I am using hardy heron(the latest ubuntu)... then why am i not having the option/command to do that

---

### Post by Dr Small on 2008-09-28
Have you installed vim-full?

---

### Post by luckydeveloper on 2008-09-28
i got it.. i just did the install for vim-full and made a command  :suntax on  it worked.. thanks

---

