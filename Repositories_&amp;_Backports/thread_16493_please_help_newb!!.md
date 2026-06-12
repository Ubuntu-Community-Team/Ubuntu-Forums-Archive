---
title: "please help newb!!"
date: 2005-02-21
forum: Repositories &amp; Backports
---

### Post by rarstar on 2005-02-21
I've downloaded some .deb packages from [http://archive.ubuntu.com/ubuntu/pool](http://archive.ubuntu.com/ubuntu/pool)
but I haven't got a clue how to install them!!

Can anybody help?

The package manager program (synap something) only seems to let you add internet resources as repositories but I don't have a net connection yet.

I'm totally confused!

I already have the .deb files on my desktop, I just don't know what to do with them!

---

### Post by wallijonn on 2005-02-21
Usually you start a Root Terminal (Applications -> System Tools -> Root Terminal), then cd (change directory) over to where the file is and issue a [COLOR=Red]sudo dpkg -i xxxxxxx.deb[/COLOR] command, where xxxxxxx = name of file.

---

