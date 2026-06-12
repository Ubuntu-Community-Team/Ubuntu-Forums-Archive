---
title: "remap ESC to CAPS LOCK in .vimrc file"
date: 2007-10-22
forum: Programming Talk
---

### Post by frischi on 2007-10-22
I've started using vim only recently and i really like it. But it always such long way to the esc - key. I then found out that many people remap it to caps lock. And I even found a How-To that I was able to do.

It worked like that.

make a file with

```
remove Lock = Caps_Lock
add Lock = Escape
keysym Caps_Lock = Escape
keysym Escape = Caps_Lock
```

in it

and append

```
xmodmap FILENAME
```

to the file .bashrc in home folder

It did work fine but my problem is that i want to use the keys normally when I'm not in vim. So I've been wondering whether you could set this in the .vimrc file??? So it's normal again when you leave vim.

---

### Post by brunovecchi on 2008-01-17
Could you please tell me what Ubuntu version were you using when you remapped this? Because I can't seem to make xmodmap work for me, and I think that I'm dealing with a bug.

EDIT: Nevermind, I got it working. Sorry! :KS

---

### Post by naugiedoggie on 2008-01-17
> **frischi said:**
> I've started using vim only recently and i really like it. But it always such long way to the esc - key. I then found out that many people remap it to caps lock. And I even found a How-To that I was able to do.

It worked like that.

make a file with

```
remove Lock = Caps_Lock
add Lock = Escape
keysym Caps_Lock = Escape
keysym Escape = Caps_Lock
```

in it

and append

```
xmodmap FILENAME
```

to the file .bashrc in home folder

It did work fine but my problem is that i want to use the keys normally when I'm not in vim. So I've been wondering whether you could set this in the .vimrc file??? So it's normal again when you leave vim.

Probably, although there's no vim key identifier for the capslock key, so you would have to do it with a scan code.  I don't know how to do that.  Within vim, you can remap keys like this:

```

:inoremap <C-space> <esc>

```
That remaps the escape key to Control-Space.  Also, note that Control-[ performs the same function as <esc>.  And, easier to type.  So if that is an acceptable keystroke, you could avoid the mapping business altogether.

Thanks.

mp

---

