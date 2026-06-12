---
title: "HOWTO: Edit text files in Ubuntu"
date: 2004-11-09
forum: Outdated Tutorials &amp; Tips
---

### Post by HungSquirrel on 2004-11-09
[size=3]**Graphical**[/size]

When Ubuntu is booted into the graphical environment (X), you can use gedit as your text editor.  Gedit is a small, lightweight text editor similar to Windows' WordPad.  It has a very easy to use graphical interface.  To access it, navigate to Applications -> Accessories -> Text Editor.



[size=3]**Console**[/size]

For those who would prefer (or for situations when you can't get X to start!), there are many text editors you can use from within the console.


**nano**

Nano is a very easy-to-use free pico clone that comes installed by default in Ubuntu.  This is definitely a great console text editor for those who are unfamiliar with more advanced ones such as vim.

To use nano to edit a file, do the following in a terminal, where 'filename' is the name of the file you want create or modify:

```
nano filename
```

The important command shortcuts are displayed at the bottom of nano's screen, denoted by a **^** and a shortcut character.  The **^** stands for the **Ctrl** character on your keyboard.  For example, the exit shortcut on nano is **^X**, so to exit nano you would hold down **Ctrl** and press **x**.

For more information on this editor, please see the [documentation](http://www.nano-editor.org/docs.html).


**ee and aee**

ee (Easy-Edit) and aee (Advanced Easy Editor) are two similar very easy to use console text editors.  Like nano, keyboard shortcuts are performed by holding **Ctrl** and pressing the correct shortcut keys.  Common shortcuts are listed at the top of the screen.  There is also a handy menu system that can be accessed by pressing **Esc**.

Of the two, I prefer aee simply because the main menu loads slightly faster.  Apart from that, their keyboard shortcut sequences are slightly different, but all the shortcuts are listed at the top of the screen.  ee is the default text editor of [FreeBSD](http://www.freebsd.org/).

To install these editors, you will need to [enable the Universe repository](http://www.ubuntuforums.org/showthread.php?t=179).

After doing so, open a terminal and do the following to install ee:

```
sudo apt-get install ee
```

Or, for aee:

```
sudo apt-get install aee
```

To create or modify a file with these editors, do the following in a terminal, where 'filename' is the name of the file you want to edit or create:

```
ee filename
```

Or, for aee:

```
aee filename
```


**vim**

This powerful vi clone is installed by default on nearly all Linux systems, including Ubuntu.  It has many advanced features such as syntax highlighting (a feature that color codes key words in programming languages and configuration files).  If you prefer a more feature-packed text editor than nano and the rest, this is a good one.

To use vim to edit a file, do the following in a terminal, where 'filename' is the name of the file you want to create or modify:

```
vi filename
```

or

```
vim filename
```

To get syntax highlighting to work, do the following in a terminal:

```
cp /usr/share/vim/vim63/vimrc_example.vim ~/.vimrc
```

For more information on how to use vim, please see [The Vim Documentation](http://www.vim.org/docs.php).  Vim is a very powerful *and complicated* tool, so be sure to read over the documentation.

---

