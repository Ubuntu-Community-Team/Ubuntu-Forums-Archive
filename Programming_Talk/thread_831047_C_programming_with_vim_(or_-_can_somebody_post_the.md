---
title: "C programming with vim (or - can somebody post their .vimrc?)"
date: 2008-06-16
forum: Programming Talk
---

### Post by oodlesOfmoodles on 2008-06-16
Hey guys,

I just bought a copy of The C Programming Language (Second Edition) and I'm pretty excited to start learning.

I kind of don't want to use a traditional IDE.

Can anyone post or direct me to a site that has a good .vimrc for C programming? I prefer ANSI brackets if thats possible

```
foo bar(foo foobar)
{
   return foobar;
}
```

Thanks a lot guys!

---

### Post by LaRoza on 2008-06-16
Run:

```

sudo aptitude install vim

```

Ubuntu comes with vim-tiny by default.

If it doesn't by default, I would add these to .vimrc. (Try the default settings after installing first to see what you like)
```

set showmatch
set expandtab
set tabstop=4
set shiftwidth=4
set nocompatible

```

---

### Post by aJayRoo on 2008-06-16
The template vimrc file is actually very good, although I also make additions as in the above post. The template file is not available until you install the full vim (again as directed in the above post). Once you have that installed you can copy the template to your home directory as follows:
```
cp /usr/share/vim/vim71/vimrc_example.vim ~/.vimrc
```
This will overwrite your current vimrc file so back it up if necessary. You can then add any extra lines to the end of that file as you please. This is the setup I use for programming in C and other languages.

---

### Post by MONODA on 2008-06-16
I have been thinking of purchasing this book myself, how is it so far?

---

### Post by LaRoza on 2008-06-16
> **MONODA said:**
> I have been thinking of purchasing this book myself, how is it so far?

K&R is the only C book needed. (Best to know a bit of programming already before reading it)

---

### Post by MONODA on 2008-06-16
> K&R is the only C book needed. (Best to know a bit of programming already before reading it)
cool thanks, I will look into it.

---

### Post by dtmilano on 2008-06-16
The best of both worlds: Netbeans + [jvi]("http://jvi.sourceforge.net/") (vim for Netbeans).

---

