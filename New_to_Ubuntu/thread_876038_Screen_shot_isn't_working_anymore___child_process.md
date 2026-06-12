---
title: "Screen shot isn't working anymore _ child process?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by arnicainthemembrane on 2008-07-31
"There was an error running "gnome-screenshot": failed to execute child process "gnome-screenshot". (No such file or directory) - 

This problem came up abruptly, I've never had this issue before. How can I get the computer to execute a child process?

---

### Post by tuxxy on 2008-07-31
What happens if you do Alt + Print Screen?

It may have something to do with **gnome-utils** package

---

### Post by billgoldberg on 2008-07-31
Install scrot and use this command to take a screenshot:

```
scrot -e 'mv $f ~/Desktop'
```

Or use the gimp (file -> acquire -> screenshot).

You could try reinstalling  gnome-screenshot

```
sudo apt-get autoremove gnome-screenshot --purge
```

And then

```
sudo apt-get install gnome-screenshot
```

---

### Post by arnicainthemembrane on 2008-07-31
whatever that did, it worked. thanks.

---

