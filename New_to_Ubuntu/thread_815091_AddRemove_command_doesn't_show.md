---
title: "Add/Remove command doesn't show"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by deyka on 2008-06-01
Hi, everyone! I'd like to use the Add/Remove command but it doesn't show in the applications menu. When I try to make the command available from the Main Menu by clicking on the appropriate box, it unchecks itself. How can I solve the problem? :KS

---

### Post by sayakb on 2008-06-01
At a terminal:
```
gksudo gnome-app-install
```

---

### Post by deyka on 2008-06-02
Well, I tried the command [COLOR="SeaGreen"]gksudo gmome-app-install[/COLOR] as [COLOR="Indigo"]LinuxIsInnovation[/COLOR] suggested (thanks for that) but when I entered my password I got this:

[COLOR="Red"]Failed to run gnome-app-install as user root.

The underlying authorisation mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/COLOR]

My Ubuntu version is 7.10 and it doesn't have a root account so I wonder if that's the reason why the above method doesn't work. What else can I try?:-s

---

### Post by WRDN on 2008-06-02
Unless you deleted the root account, you'll have it.
Instead of using the sudo command, try typing "su" then the root password.

---

### Post by deyka on 2008-06-03
I did as you suggested but it didn't change anything. Apparently I'm still not a superuser.

---

### Post by deyka on 2008-06-04
I tried this:

[COLOR="Green"]/usr/bin/gnome-app-install[/COLOR]


and the GUI issued a message saying that the applications database was out-of-date and asked me if I wanted to update it after what it prompted me to enter a password and when I did so I got the message I show as a screen shot in the attachment. And concerning the terminal, the output I got is as follows:

administrador@jose-desktop:~$ /usr/bin/gnome-app-install

[COLOR="Sienna"]** (gnome-app-install:5490): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.5/site-packages/AppInstall/AppInstall.py:1261: GtkWarning: gtk_tree_model_sort_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
  item.applications.set_default_sort_func(None)
administrador@jose-desktop:~$ 
[/COLOR]

Can anyone give me some advice?:(

---

