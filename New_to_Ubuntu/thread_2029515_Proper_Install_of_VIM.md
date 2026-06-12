---
title: "Proper Install of VIM?"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by lemmingrebel on 2012-07-19
I want to begin programming some C in the Ubuntu environment ... I started here:

[http://ubuntuforums.org/showpost.php?p=2045086](http://ubuntuforums.org/showpost.php?p=2045086)

But I am unsure what exactly to do about installing VIM.  Everywhere I look there seems to be a different set of install commands for the terminal.  

Can someone point me in the right direction?


PS - Sorry if this is the wrong forum ...

---

### Post by wojox on 2012-07-19
Open a terminal ( Ctrl + Alt + T ) and run this command:
```
sudo apt-get update; sudo apt-get install vim
```

---

### Post by idoitprone on 2012-07-19
> **lemmingrebel said:**
> I want to begin programming some C in the Ubuntu environment ... I started here:

[http://ubuntuforums.org/showpost.php?p=2045086](http://ubuntuforums.org/showpost.php?p=2045086)

But I am unsure what exactly to do about installing VIM.  Everywhere I look there seems to be a different set of install commands for the terminal.  

Can someone point me in the right direction?


PS - Sorry if this is the wrong forum ...

vim is installed by default

open the terminal

type
```
 vi
```

here a cheat sheet
[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)

you might be interesting in 
vimtutor

```
sudo apt-get install vimtutor
```

to run
```
vimtutor
```

Remember vi is another plain text editor. For basic things, gedit and kate is not that bad

---

### Post by richpri on 2012-07-19
Why use VIM when you can use an editor like gedit with programming aids.
Highlight mode for "C" [in gedit] is extremely useful!

---

### Post by GreatDanton on 2012-07-19
Because if you happen to run servers it's better to be prepared on the situation without any graphic editors.

---

### Post by M!K3_$ on 2012-07-19
> **richpri said:**
> Why use VIM when you can use an editor like gedit with programming aids.
Highlight mode for "C" [in gedit] is extremely useful!

Vim will perform syntax highlighting as well as auto indentation (and probably a whole whack of other stuff which I don't yet know of).

---

### Post by CharlesA on 2012-07-19
> **idoitprone said:**
> vim is installed by default

open the terminal

type
```
 vi
```

vim.tiny is installed by default. If you want the full blown version of vim, you can install it with:

```
sudo apt-get install vim
```

---

### Post by afixane on 2012-07-19
The default vim in ubuntu is the "vim-tiny". If you want to install complete vim, then type
```
sudo apt-get install vim
```
If you want the GUI client of vim
```
sudo apt-get install vim-gtk
```

---

### Post by glennric on 2012-07-19
> **richpri said:**
> Why use VIM when you can use an editor like gedit with programming aids.
Highlight mode for "C" [in gedit] is extremely useful!

Vim has everything that gedit has and much more.  Once you know how to use it it blows any other text editor away.  Well, except maybe Emacs.

---

### Post by M!K3_$ on 2012-07-20
> **glennric said:**
>  Well, except maybe Emacs.

...and it begins

---

