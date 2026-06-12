---
title: "How create link to another folder in HOME"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by movrshakr on 2008-04-24
With apologies, I know this must be simple, but I cannot figure it out, nor did 30 min of web hunting lead me to it.

Using the GUI folder views, how do you create a link in your home folder that will open a folder elsewhere on the disk?

---

### Post by taavikko on 2008-04-24
In Gnome, just right click on selected folder "Create/make link"
Then move it to where you like.

or in command line
```
ln -s /folder/to/link /where/to/linkit
```

---

### Post by swoll1980 on 2008-04-24
by holding ctrl+shift you can drag and drop links as well

---

### Post by movrshakr on 2008-04-24
> **swoll1980 said:**
> by holding ctrl+shift you can drag and drop links as well

That's it!  I don't know why my web searching didn't find that.  I searched
ubuntu make link
ubuntu make symbolic
ubuntu create link
ubuntu create symbolic

and never found anything of help.

Thanks much; it worked.

---

### Post by movrshakr on 2008-04-24
> **taavikko said:**
> In Gnome, just right click on selected folder "Create/make link"
Then move it to where you like.

or in command line
```
ln -s /folder/to/link /where/to/linkit
```

The 'make link' was grayed out in the right click, probably because I was using it on /etc.  The ctrl+shift drag did create the link though.

---

### Post by rykel on 2009-10-19
Like what swoll1980 says, you can Ctrl+Shift and drag to create a link.

You can also Middle-Click and drag to get a "Create Link" dialog.

Try it - you will like it!

:guitar:

---

### Post by bmasterflash on 2010-07-04
> **movrshakr said:**
> The 'make link' was grayed out in the right click, probably because I was using it on /etc.  The ctrl+shift drag did create the link though.

If 'make link' is grayed out it is probably because you do not own the folder.  If you change the owner and/or permissions it should be available, but like you said ctrl+shift will work too.

---

