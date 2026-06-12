---
title: "Theme parsing errors while running gedit from Terminal in 14.04"
date: 2016-04-04
forum: New to Ubuntu
---

### Post by Grace_Palazzolo on 2016-04-04
When I run gedit from Terminal in 14.04, I always get these errors:

  ```
~$ gedit

(gedit:11137): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:994:1: '/*' in comment block

(gedit:11137): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:2055:42: 'from' is not a valid property name

```  While these are not fatal, I would as soon be rid of them. (I am  running Unity desktop, if that makes any difference.) What is the best  way to deal with this?

---

### Post by vasa1 on 2016-04-04
What happens with *gedit 2>/dev/null*?

Of course, you could always edit the files mentioned and see if you can fix whatever needs fixing.

---

### Post by Grace_Palazzolo on 2016-04-04
I gather that command you suggest will just write the output to /dev/null rather than stdout, but that doesn't solve the problem, just makes it invisible, right?  Yes, it does look like I need to edit those files, but I hesitate to do so without a little guidance.

---

### Post by vasa1 on 2016-04-04
You can do so by trial-and-error. Make a back-up of the originals.

You wrote: > but that doesn't solve the problem, just makes it invisible, right?But it isn't a problem, as pointed out to you over at Ask Ubuntu, the messages are directed at developers of the concerned themes or applications and not at end-users such as you or me.

BTW, GNOME is somewhat famous for deprecating code, something that developers have to struggle with ;)

---

