---
title: "Vim syntax highlighting question"
date: 2007-08-13
forum: Programming Talk
---

### Post by triptoe on 2007-08-13
Hey i have a question... I downloaded a custom colors script for programming in python.

I am supposed to put it in my ~/.vim/syntax directory

however it has no effect.... the default syntax highllighting still gets used. how to i make it use it ?

---

### Post by hugmenot on 2007-08-13
No, the color themes go into ~/.vim/colors.
Then to apply them you use the command :colorscheme XYZ.
If you want to default it enter this line without the colon into your .vimrc or .gvimrc.

---

### Post by hugmenot on 2007-08-13
If you meant you downloaded a syntax definition then it does go into syntax, but I guess you downloaded a theme with special care taken for python constructs.

---

### Post by triptoe on 2007-08-13
[http://www.vim.org/scripts/script.php?script_id=790](http://www.vim.org/scripts/script.php?script_id=790)

thats what i downloaded. I seem to remember once i had this custom gold coloring that i liked... it was bronze goldish.. it looked better. But oh well. highlighting is on and that is what counts

---

### Post by hugmenot on 2007-08-14
Alright, that&#8217;s a replacement for Python syntax. What you must look for is the color scheme that uses this definition for highlighting with your bronze colors. And that will go into ~/.vim/colors.

---

### Post by pointone on 2007-08-14
Are you sure it's not being used? I use that enhanced version as well, but the differences are very subtle. One way to tell is with strings. With the default, the quotation marks (") will not be coloured, but with the enhanced version, the quotation marks are coloured like the string content.

---

### Post by ajaygautam on 2007-11-17
Also see bug:
[https://bugs.launchpad.net/ubuntu/+source/vim/+bug/63172](https://bugs.launchpad.net/ubuntu/+source/vim/+bug/63172)

This bug requests that syntax / color highlighting be switched on by default.
Till then, the workaround is to uncomment "syntax on" in file /etc/vim/vimrc

- Ajay

---

