---
title: "How to create keyboard shortcut to Text Editor"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by abcuser on 2008-10-31
Hi,
on Ubuntu 8.10 I would like to create keyboard shortcut to Text Editor. How?
Regards,
Abcuser

---

### Post by cyfur01 on 2008-10-31
xbindkeys should do exactly what you've asked.

To install and set up the default configuration:
```

sudo apt-get install xbindkeys xbindkeys-config
xbindkeys --defaults > /home/user/.xbindkeysrc

```

Then, to configure:
```

xbindkeys-config

```
The interface isn't exactly pretty. Create a new binding, give it a remark (description), the key combination, and the command (gedit in your case).

As an alternative, have you heard of [gnome-do]("https://wiki.ubuntu.com/GnomeDo")? It's a quick means of launching all your apps. Plus, there's numerous plugins for searching through Pidgin contacts, launching terminal apps, etc...
```

sudo apt-get install gnome-do

```
Once it's installed and running, by default, press Super+Space (Super=Windows key), then start typing the name of the program you want to launch. It also learns, so after you type "gedit" 10 times (probably less), it will likely associate "g" as a match for gedit. [More on usage.]("https://wiki.ubuntu.com/GnomeDo/Use")

---

### Post by Paddy Landau on 2008-10-31
Another method is to use Compiz.

System -> Preferences -> Advanced Desktop Effects Settings

Choose the *General Options*, *Commands*.

Fill in the Commands section (say, "Command line 0") with *gedit*.

Fill in the corresponding Key bindings section with the keystroke that you require.

---

