---
title: "fckeditor"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by tonyn999 on 2008-05-14
I used the Synaptic package manager to install fckeditor.  The installation appeared to go smoothly.  Some files were deposited (e.g., /etc/fckeditor), but these does not appear to be a binary, nor does the program show up under the Gnome Application pull down menu.

Can anyone help?

---

### Post by Het Irv on 2008-05-14
try typing fckeditor in the terminal, if the program was install correctly, it should start.

---

### Post by Oldsoldier2003 on 2008-05-14
> **tonyn999 said:**
> I used the Synaptic package manager to install fckeditor.  The installation appeared to go smoothly.  Some files were deposited (e.g., /etc/fckeditor), but these does not appear to be a binary, nor does the program show up under the Gnome Application pull down menu.

Can anyone help?

try launching it in the terminal
```
fckeditor
```
and see what happens, post any error output you might receive

---

### Post by Paqman on 2008-05-14
From the [homepage](http://docs.fckeditor.net/FCKeditor_2.x/Users_Guide/Overview) it seems like this package is a lightweight text editor designed to be embedded in web pages. I'm figuring the package is designed to be installed on a server.

---

### Post by jordanmthomas on 2008-05-14
fckeditor is a web text editor.  It will not have a binary as it's just javascript.  I might be mistaken but I think you're supposed to use it with Drupal or something similar.

---

### Post by tonyn999 on 2008-05-14
Sorry I should have mentioned, the command (with or without sudo) fckeditor yields a "command not found" message.

---

### Post by jordanmthomas on 2008-05-14
That's because it is not a standalone editor.  It's just a bit of javascript intended to be put in webpages.

---

