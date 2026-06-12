---
title: "Make CLASSPATH persistent in Ubuntu"
date: 2011-06-22
forum: Programming Talk
---

### Post by skytreader on 2011-06-22
Hi all. I noticed that turning my computer off removes the CLASSPATH variable I set, i.e., on my next session, running java programs importing from non native APIs throws ClassNotFoundExceptions. I'm following the instructions from JDBC MySQL Connector documentation:

```
export set CLASSPATH=/usr/import/jdbc-mysql-connector.jar:$CLASSPATH

```

How do I make my setting "persistent", i.e., it remains even if I turn my computer off? (Doing this while in su doesn't help as, exiting su, the library is unavailable to non-su users).

Thanks!

---

### Post by m_duck on 2011-06-22
Putting the export line in the **~/.bashrc** of the user who needs this extended classpath should do the trick.

---

### Post by skytreader on 2011-06-22
> **m_duck said:**
> Putting the export line in the **~/.bashrc** of the user who needs this extended classpath should do the trick.

Ummm...sorry but, where is ~/.bashrc?

---

### Post by dwhitney67 on 2011-06-22
> **skytreader said:**
> Ummm...sorry but, where is ~/.bashrc?

:shock:

Look in your home directory; there should be a hidden file with the name of .bashrc (if you are using the bash environment).

---

### Post by m_duck on 2011-06-22
Sorry, it's in your home directory. Say your user is 'skytreader', saying ~/.bashrc for that user is the same as /home/skytreader/.bashrc.

In Nautilus you can press **ctrl + h** to show hidden files and edit it from there, or you can open it from the terminal in you editor (e.g. gedit or vim respectively):```
gedit ~/.bashrc
``````
vim ~/.bashrc
```

---

### Post by cgroza on 2011-06-22
> **m_duck said:**
> Sorry, it's in your home directory. Say your user is 'skytreader', saying ~/.bashrc for that user is the same as /home/skytreader/.bashrc.

In Nautilus you can press **ctrl + h** to show hidden files and edit it from there, or you can open it from the terminal in you editor (e.g. gedit or vim respectively):```
gedit ~/.bashrc
``````
vim ~/.bashrc
```
or:

```
emacs ~/.bashrc
```

---

