---
title: "What's Ubuntu 14.04 Window Manager?"
date: 2014-05-08
forum: New to Ubuntu
---

### Post by joe_cool2 on 2014-05-08
I would like to install some new themes but I don't know which window manager Ubuntu 14.04 uses on Unity. Anyone knows it?

Oh, and which version of GTK+ does it use?

---

### Post by Kingsrookie on 2014-05-08
you can use the Environment Variable $XDG_CURRENT_DESKTOP to find the windows manager you are currently using. The GTK+ may be a little more ticky because of the version you may have but
dpkg -s libgtk-3-0|grep '^Version'

will tell you which version of GTK+3 you are using

Substitute libgtk-3-0 with
libgtk2.0-0
if you are using GTK+2. Hopefully this answers your question!

---

### Post by deadflowr on 2014-05-08
Ubuntu's window manager is compiz.

---

### Post by Drowz0r on 2014-05-08
Not sure if this is related, but if you're into theming this is something I found rather handy/delicious:

[http://www.omgubuntu.co.uk/2014/04/change-folder-icon-color-ubuntu-linux-easily](http://www.omgubuntu.co.uk/2014/04/change-folder-icon-color-ubuntu-linux-easily)

---

### Post by joe_cool2 on 2014-05-08
> **Kingsrookie said:**
> you can use the Environment Variable $XDG_CURRENT_DESKTOP to find the windows manager you are currently using. The GTK+ may be a little more ticky because of the version you may have but
dpkg -s libgtk-3-0|grep '^Version'

will tell you which version of GTK+3 you are using

Substitute libgtk-3-0 with
libgtk2.0-0
if you are using GTK+2. Hopefully this answers your question!

Your post didn't help me.

```
$ $XDG_CURRENT_DESKTOP No command 'Unity' found, did you mean:
 Command 'unity' from package 'unity' (main)
Unity: command not found
```

And if I know which version of GTK+ I'm using, I wouldn't have posted this thread in the first place.

---

### Post by joe_cool2 on 2014-05-08
> **deadflowr said:**
> Ubuntu's window manager is compiz.

Thanks. Which GTK+ in use, do you know?

---

### Post by deadflowr on 2014-05-08
> **joe_cool2 said:**
> Thanks. Which GTK+ in use, do you know?

It's a mixture.
Here's what I have on 14.04
```
dpkg -l gtk* | grep ii
ii  gtk2-engines-murrine:amd64                            0.98.2-0ubuntu2                                     amd64        cairo-based gtk+-2.0 theme engine
ii  gtk2-engines-pixbuf:amd64                             2.24.23-0ubuntu1                                    amd64        pixbuf-based theme for GTK+ 2.x
ii  gtk3-engines-unico:amd64                              1.0.3+14.04.20140109-0ubuntu1                       amd64        Unico Gtk+ 3 theme engine

```

---

### Post by joe_cool3 on 2014-05-19
Ok, thanks!

---

### Post by Luke M on 2014-05-19
wmctrl -m

---

