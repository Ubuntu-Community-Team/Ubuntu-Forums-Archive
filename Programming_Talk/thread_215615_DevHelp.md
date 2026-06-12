---
title: "DevHelp"
date: 2006-07-14
forum: Programming Talk
---

### Post by mvaniersel on 2006-07-14
I read this interesting tidbit in the ubuntu newsletter:


> If you are a developer you may often times find yourself scouring the Internet looking for various API references and other technical information you may require while building your software. Sometimes this is the only way to find what you need but for many GNOME applications and libraries you can often find the information your are looking for is readily available via a neat little app called Devhelp. Devhelp consolidates various developer focused documentation into one convenient location so you always know where to find it. To install Devhelp simply install the package named devhelp. Once installed Devhelp is available at Applications -> Programming -> Devhelp. In addition to the documentation available via Devhelp by default you can install more documentation and even register your own apps documentation for use in Devhelp. Give it a try, it is nice to have all of the information you need in one easy to use location whether you are online or off.


Well, I've installed DevHelp just to try it out. But in spite of what the newsletter says, I don't see how I can install new doc libraries. How can I for instance, add glibc documentation? Can I add documentation in chm or pdf format? Is it possible to add javadoc or perldoc?

Ironically, documentation on DevHelp itself seems to be almost entirely missing. I've tried the website [http://developer.imendio.com/wiki/Devhelp]("http://developer.imendio.com/wiki/Devhelp")
or man DevHelp, but that hardly gives any information.

---

### Post by Daverz on 2006-07-14
Most docs can by installed with synaptic (-doc packages).  I know at least the python and pygtk docs will be found by devhelp.

Otherwise, you can install new docs in $HOME/.devhelp/books.

Looking around, it seems that gnome related is found by devhelp, but a lot of other stuff isn't (glibc-doc, postgresql-doc, among others).

---

### Post by mvaniersel on 2006-07-25
I've got docs for allegro in devhelp format, but I can't manage to get them added to the list.

I already tried creating a symlink in ~/.devhelp/books or in /usr/share/gtk-doc/html. For example:

```

/usr/share/gtk-doc/html$ sudo ln -s ~/lib/allegro4.2-4.2.0/docs/devhelp allegro

```

But it doesn't get added to the list in devhelp. Any ideas?

---

### Post by bobrath on 2006-07-25
A little help please...
I'm learning Glade right now. After Glade generates the source code , I go the terminal , navigate to my projects directory and type ./autogen.sh
A series of messages run down on the screen. AT the end it says " Type 'make' to compile."
Then it goes back to the prompt.
When I type make , it says bash:make: command not found...?
What do I do?

---

### Post by Daverz on 2006-07-26
> **mvaniersel said:**
> I've got docs for allegro in devhelp format, but I can't manage to get them added to the list.

I already tried creating a symlink in ~/.devhelp/books or in /usr/share/gtk-doc/html. For example:

```

/usr/share/gtk-doc/html$ sudo ln -s ~/lib/allegro4.2-4.2.0/docs/devhelp allegro

```

But it doesn't get added to the list in devhelp. Any ideas?

There's usually a .devhelp file in the directory.  I'm guessing that you need a layout like

~/.devlhelp/books/foo/foo.devhelp

for it to pick up the docs in the foo directory.

---

