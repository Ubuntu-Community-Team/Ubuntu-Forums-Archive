---
title: "vim"
date: 2007-08-06
forum: Programming Talk
---

### Post by LaRoza on 2007-08-06
When I use vim in Ubuntu, there is no syntax highlighting. When I used vim in Arch, it had syntax highlighting and auto indenting. If there is another package or addon, what is it? And if it is a setting, how to I alter them? 

I would like to be able to control spaces/tabs, auto indenting, and syntax highlighting.

Thanks.

---

### Post by nichipet on 2007-08-06
I'm not on Ubuntu (or any other *nix system) to test this, but I believe you want to do this:

```
vim ~/.vimrc
```

then add in the file:

```
syntax on
set ai
```

I think that will turn on syntax highlighting and autoindent. I haven't found control spaces/tabs yet.

---

### Post by LaRoza on 2007-08-06
Thanks!

Vim is a very good editor so far, I really like being able to edit, compile, run, execute system commands with out taking my hands off the keyboard.

---

