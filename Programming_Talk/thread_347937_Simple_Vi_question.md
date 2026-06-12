---
title: "Simple Vi question"
date: 2007-01-28
forum: Programming Talk
---

### Post by cneil on 2007-01-28
Hi,
I'm learning C and I use vi in a Gnome terminal.  Everytime I run vi, I need to type the command "sy on" in order to color code my code.  Is there a way to make it so I don't have to type this command every time.  I am running Unbuntu dapper drake and I can't seem to find the configuration files for vi.
Thanks

---

### Post by Ramses de Norre on 2007-01-28
```
sudo vi /etc/vim/vimrc
    #or
vi ~/.vimrc
```
And uncomment "syntax on".

---

### Post by cneil on 2007-01-28
Thanks!
That was really simple.

---

