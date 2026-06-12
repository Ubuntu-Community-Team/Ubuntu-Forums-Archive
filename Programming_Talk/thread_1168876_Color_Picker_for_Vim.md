---
title: "Color Picker for Vim"
date: 2009-05-24
forum: Programming Talk
---

### Post by mvalviar on 2009-05-24
Can anyone suggest a color picker plugin for vim? Gedit has a cool color picker plugin. I'm wondering if there is something similar for vim.

---

### Post by imploder on 2009-08-04
I've found and installed this: [colorsel.vim]("http://www.vim.org/scripts/script.php?script_id=927")
It works, but it has two major downsides: 
- no mouse support, using the arrows is slow and awkward
- it does not load the color from the place of the cursor in the file, nor does it directly change the color code (I have to copy/past it)
When running in X, it has in fact no advantege over external color pickers.
I wonder too if there is a better solution, something that could show and edit colors directly from (g)vim (it doesn't matter if it would be an external window). As far as I've looked, there's no such thing.
It would be helpful a lot for coding HTML/CSS.
 :confused:

---

### Post by stroyan on 2009-08-04
If you are picking colors to look for a nice color scheme, then
[http://code.google.com/p/vimcolorschemetest/](http://code.google.com/p/vimcolorschemetest/)
provides a nice way to just scan for an attractive scheme.

---

### Post by JordyD on 2009-08-04
> **stroyan said:**
> If you are picking colors to look for a nice color scheme, then
[http://code.google.com/p/vimcolorschemetest/](http://code.google.com/p/vimcolorschemetest/)
provides a nice way to just scan for an attractive scheme.

I believe their looking for a plug-in that gives the hexadecimal values of colors so that they can paste it into their code.

---

### Post by FLOZz on 2010-09-18
There is a Python/GTK color picker for vim:

[IMG]http://static.flogisoft.com/vim/vim_color_picker_0.1.png[/IMG]

[http://www.vim.org/scripts/script.php?script_id=3224](http://www.vim.org/scripts/script.php?script_id=3224)

---

