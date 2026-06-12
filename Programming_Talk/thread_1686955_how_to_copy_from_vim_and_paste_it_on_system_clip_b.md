---
title: "how to copy from vim and paste it on system clip board"
date: 2011-02-13
forum: Programming Talk
---

### Post by tapas_mishra on 2011-02-13
Hi
i want to select some text from vim using "yank" command and then access the same on shell prompt
using ^v or shift ^Insert.How can that be done.

---

### Post by gmargo on 2011-02-13
If you yank into the **"+** register, it will go into the x11 selection, which can be pasted using shift-insert.

So, to yank a whole line in normal mode:
```

"+yy

```

To yank a whole line in command mode:
```

:yank +

```
More info available in the vim help (:help clipboard)

---

### Post by tapas_mishra on 2011-02-13
I read the help page and also tried what you said but any of the things did not worked.
Here is my file 
temp.txt
> 
some arbit
something
non 
ppr
Now I open the above file in vim and scroll down to third line.
Press > :"+yyand then open gedit a blank file opens there
press > Shift+Insert nothing gets pasted there.
I also tried right click of mouse but it sill does not work.
I have tried various other permutations also but things didn't happened as I wanted.

---

### Post by xtremethegreat1 on 2011-02-13
The paste "command" in gedit is Ctrl+V and not Shift+Insert. The rest of what you did is just the same.

---

### Post by trent.josephsen on 2011-02-13
Using * instead of + will put it into the middle-click buffer.  It's still amazing to me how many people don't know this feature exists.

---

### Post by tapas_mishra on 2011-02-16
It works until the clip board buffer does not get over written.
What I mean to say if I have pasted the lines of vi like this on shell or gedit (what ever)
now I copy some thing from Firefox (a URL) 
and repeat the steps from where I started the thread
this time the same steps do not work on both case (shell or gedit)
so the "+ register or "* is not being shared with x11 or some thing prevents writing to clip board buffer.
When you over write the clip board buffer from previous "+ command by a new paste from some different x11 application.

---

### Post by x33a on 2011-05-01
> **trent.josephsen said:**
> Using * instead of + will put it into the middle-click buffer.  It's still amazing to me how many people don't know this feature exists.

 Thanks, i logged in after a few months, specially to thank you. This issue was driving me nuts.  Using * instead of + did the trick for me.

---

### Post by TeoBigusGeekus on 2011-05-01
If you're using the simple plain vim, it doesn't have support for the system clipboard:
```
vim --version | grep xterm
```
Will give 
```
-xterm_clipboard
```

You have two options:
1)Compile vim yourself, with the xterm_clipboard flag on
2)Uninstall vim, install gvim and use it as vim, ie. don't use the ui, but call vim from terminal, the same way you did when you had vim. If you give:
```
vim --version | grep xterm
```
you will get a line with
```
+xterm_clipboard
```
and both the + and * buffers will be enabled.

---

### Post by gmargo on 2011-05-01
By default, Ubuntu installs the **vim-tiny** package, which is a ultra-light version of the console "vim" only.

Most people should simply install the **vim-gtk** (or **vim-gnome**) package.  This package will provide both the graphical "gvim" and the console "vim", but in a "huge" configuration that includes support for the clipboard.  It is not necessary to uninstall **vim-tiny** first.

If you really don't want any gui support (i.e. you have no X libraries installed), then you should install the **vim** package, which is the full "huge" configuration for the console "vim".

---

### Post by ajaysabat on 2011-08-06
Thanks a lot guys. I was looking for this feature for sometime. I could resolve this by following the suggestions mentioned here. This is what I did.
 
I had vim 7.2 on my system with no xterm-clipboard support. I tried the tricks of using * or + register. Storing any text in these registers inside vim was not getting available outside vim.
$ vim --version | grep xterm
**-xterm_clipboard** 
 
Then I removed vim and installed vim-gnone
$ sudo apt-get purge vim
$ sudo apt-get autoremove (removes other unwanted packages from system, in this case related to vim)
$ sudo apt-get install vim-gnome
$ vim --version | grep xterm
-mouse_jsbterm +mouse_netterm -mouse_sysmouse +mouse_xterm +multi_byte 
+X11 -xfontset +xim +xsmp_interact **+xterm_clipboard** -xterm_save
 
Now, when I copy some text in the + register inside the vim editor (e.g. "+yy), it also gets copied to the system clipboard which I can retrieve from some other application outside vim (e.g. terminal bash prompt or gedit editor, by using ^v or Shift+Insert command).
Not sure about the * register, though. It does not work for me.

---

