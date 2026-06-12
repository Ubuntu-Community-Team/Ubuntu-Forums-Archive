---
title: "Can't gedit?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by knottshawk on 2008-05-16
I want to edit my ssh_config file... I want to add a ServerAliveInterval line in the file. I can't do it thru mousepad... it won't let me save it.

If I use a terminal and do sudo gedit /etc/ssh/ssh_config it says 'gedit: command not found'.

If I do gksudo gedit /etc/ssh/ssh_config it just goes back to the prompt.

What am I doing wrong?

---

### Post by forestpixie on 2008-05-16
install it first - it's not default afaik

sudo apt-get install gedit

---

### Post by t0p on 2008-05-16
I don't know if this is your problem: but if you want to run a graphical app with superuser privileges, you should use **gksudo** rather than sudo.

Eg. type

```
gksudo gedit /etc/ssh/ssh_config
```

Concerning the advice that you need to install gedit first: I don't know about Hardy, but in all previous versions of Ubuntu, gedit is the default text editor that you get through the menus in the gnome gui.

**EDIT** *Ooops!!!* You've already tried **gksudo**!  Sorry!!

---

### Post by knottshawk on 2008-05-16
gedit wasn't installed... (xubuntu 7.10) Good call! Thanks!

---

### Post by .nedberg on 2008-05-16
I always use nano for those small changes...

---

### Post by Oldsoldier2003 on 2008-05-16
> **knottshawk said:**
> gedit wasn't installed... (xubuntu 7.10) Good call! Thanks!

yep mousepad is the default installed gui editor in xubuntu

---

### Post by forestpixie on 2008-05-16
> I always use nano for those small changes...So do I - although I didn't when I first started last year, got confusedand thought it was vi or whatevr that's called, that I still don't use :)

---

### Post by Paqman on 2008-05-16
The default text editor in Xubuntu is mousepad, not gedit. So whenever you see:
```

sudo gedit filename

```
Just replace with:
```

sudo mousepad filename

```

---

### Post by sunexplodes on 2008-05-16
> **t0p said:**
> I don't know if this is your problem: but if you want to run a graphical app with superuser privileges, you should use **gksudo** rather than sudo.

Eg. type

```
gksudo gedit /etc/ssh/ssh_config
```

Concerning the advice that you need to install gedit first: I don't know about Hardy, but in all previous versions of Ubuntu, gedit is the default text editor that you get through the menus in the gnome gui.

**EDIT** *Ooops!!!* You've already tried **gksudo**!  Sorry!!

Isn't it just 'gksu'?

---

### Post by Oldsoldier2003 on 2008-05-16
> **sunexplodes said:**
> Isn't it just 'gksu'?

gksu and gksudo are the same thing. gksudo is just a link to gksu

---

