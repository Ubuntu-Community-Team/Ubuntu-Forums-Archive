---
title: "How to start GUI editor with root privledge?"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by gregphil on 2008-09-13
Under KDE4

I can't seem to find an easy way to invoke a GUI editor (like kate) with full root privledges.  I can get to a root console (using sudo su) but form there can not start kate, the command line error returned is:

/home/greg # /usr/lib/kde4/bin/kate
No protocol specified
kate: cannot connect to X server :0.0

From a non-privledged console I CAN start kate (but then I can't save edits to system files) 

From a non-privledged console I cannot use kdesu to start kate:

/home/greg $ kdesu kate
sudo: kate: command not found

If I give kdesu the full path to kate, then at least it starts Kate:

/home/greg $ kdesu /usr/lib/kde4/bin/kate
kate(8130): createDoc 

But the originating terminal windows behind it has all sorts of messages, many of which appear to be errors.

So.... I guess my real questions is: How should I create a shortcut icon on the 'panel' that will start a copy of Kate with root privledges?  I want to use this to edit system configurations files.  Currently I am using the console editor "ne" (the Nice Editor) which works well.  However the bugs in the KDE4 konsole scroll-back are so distracting I would like to get away from using the konsole.

Thank You.   :?

---

### Post by akiratheoni on 2008-09-13
Hm.

Try using this command:

```
sudo ln -s /usr/lib/kde4/bin/kate /usr/bin/kate-kde4
```

Then run Kate by hitting Alt+F2 and typing:

```
kdesu kate-kde4
```

Hope it helps.

---

### Post by gregphil on 2008-09-13
Thanks, but what exactly are you doing there?  Creating a link and running the new link from a run-level-3 console?

I think I found an easier (safer?) way.  I used the adept package manager install kedit, it seems to have no problem being started from a regular konsole with kdesu:
/home/greg $ kdesu kedit
kbuildsycoca running...

I can then edit my system files, and kedit is probbaly better for this than kate anyway.  I don't know why it is not considered part of KDE4.1.1

Strangely enough kedit can not be started from a root privledged konsole:
/home/greg # kedit
No protocol specified
kedit: cannot connect to X server :0.0

Do you know the magic I need to perform to allow a root console to run programs that a normal konsole can?

Thank You.

---

### Post by dhtseany on 2008-09-13
```
user@localhost:~$ gedit /fold/file.config
```

---

### Post by Ntweat on 2008-09-13
Why dont you try kwrite instead of kate

---

### Post by bodhi.zazen on 2008-09-13
kde uses kdesu

you do not need then to make any kind of links or any of that fancy stuff.

Open a terminal and enter :

```
kdesu kate
```

---

