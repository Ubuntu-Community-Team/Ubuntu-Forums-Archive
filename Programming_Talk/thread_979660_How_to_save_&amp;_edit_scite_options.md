---
title: "How to save &amp; edit scite options?"
date: 2008-11-12
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-11-12
Normally, when starting scite, line number display is off, and intend settings use tab.

I want scite to have always line numbers on and using 4 spaces instead of tab, when I start scite.

There are some scite config files but I ain't got an idea how to make line numbers on by default, 
or how to change the default intend settings.

Thanks.

---

### Post by loell on 2008-11-12
I too once wonder back then why "show line number" is not persitent. still haven't find an answer to that, i just thought of it as more of a feature.

---

### Post by samjh on 2008-11-12
> **crazyfuturamanoob said:**
> There are some scite config files but I ain't got an idea how to make line numbers on by default, 
or how to change the default intend settings.Run Scite using gtksu.

```
gksu scite
```

Then look in the menus for an item called global options (or something to that effect).  It will open up the global options configuration file.  You can edit the file to set the options to what you want.

It's been a long time since I used Scite, but that's definitely the way to do it if you want to set the options globally.

---

### Post by crazyfuturamanoob on 2008-11-12
> **samjh said:**
> Run Scite using gtksu.

```
gksu scite
```

Then look in the menus for an item called global options (or something to that effect).  It will open up the global options configuration file.  You can edit the file to set the options to what you want.

It's been a long time since I used Scite, but that's definitely the way to do it if you want to set the options globally.
Thanks! [IMG]http://gmc.yoyogames.com/style_emoticons/default/lmaosmiley.gif[/IMG]

Finally, I don't have to always set the line numbers on and edit intend settings when doing something with scite.

And I use scite every day for everything, and I got usually multiple files open with multiple scite windows.

---

### Post by eha1990 on 2009-04-21
How do you modify the Scite startup options so that "line numbers" are displayed by default when you open the application?

---

### Post by samjh on 2009-04-21
As I posted above, run Scite using gksu:
```
gksu scite
```

In the menu bar, select Global Properties (I'm not sure which heading it's under).

Somewhere around the top third of the configuration options, there should be an option like **line.margin.visible**.  I think it's 0 by default, so set it to 1.

---

### Post by rhalaquist on 2009-12-16
Thanks the key was "gksu"

---

