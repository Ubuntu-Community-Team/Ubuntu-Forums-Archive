---
title: "Desktop shortcut : A Window didn't pop up"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by Andavane on 2012-03-22
I followed the instructions here:

[http://www.upubuntu.com/2011/10/how-to-create-desktop-shortcut-on.html]("http://www.upubuntu.com/2011/10/how-to-create-desktop-shortcut-on.html")

to the letter. Terminal went through a lot of script, but after that no window giving me the path as in the article.

I am stuck.

---

### Post by Gleichsnerd on 2012-03-22
Make sure that you double check that you're typing the command in correctly into the terminal.

Also check for any system updates and if you're using an outdated version of gnome or whatnot.

---

### Post by EzioAuditore on 2012-03-22
> **Andavane said:**
> I followed the instructions here:

[http://www.upubuntu.com/2011/10/how-to-create-desktop-shortcut-on.html]("http://www.upubuntu.com/2011/10/how-to-create-desktop-shortcut-on.html")

to the letter. Terminal went through a lot of script, but after that no window giving me the path as in the article.

I am stuck.

Did you copy-paste or write it down yourself? If its latter, note that there's a space after 'edit' and 'new'.

---

### Post by Andavane on 2012-03-23
> **Gleichsnerd said:**
> Make sure that you double check that you're typing the command in correctly into the terminal.

Also check for any system updates and if you're using an outdated version of gnome or whatnot.
I don't know how to tell which version of gnome I've got

&

> **EzioAuditore said:**
> Did you copy-paste or write it down yourself? If its latter, note that there's a space after 'edit' and 'new'.

The following was used, viz: > gnome-desktop-item-edit --create-new ~/Desktop
Can't remember but I think it was pasted.

John

---

### Post by Kevin McCready on 2012-03-23
To make desktop shortcuts I use the terminal. Invoke the terminal with ctrl-alt-t

Then I use a symbolic link. I do this by
```
cd ~/Desktop
ln -s ~/[directory where my file is]/[name of file]

```

This make a symbolic link on the desktop to your file. 

Hope this helps.

---

