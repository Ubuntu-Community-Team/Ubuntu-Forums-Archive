---
title: "open a folder"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by nyabu on 2008-08-21
i have a folder setup on the desktop with the file deluge which am trying to install but cannot install it even from the terminal because i cannot access it. Please if anyone can give a step by step instruction on configuring it to run i will greatly appreciate. thanks.

---

### Post by manishtech on 2008-08-21
You mean to say that you cannot access the files on your desktop?
Can you give us the output of the command

ls -lr ~/Desktop/*

and then just paste the section of the file/folder which you wanted to install?

---

### Post by billgoldberg on 2008-08-21
> **nyabu said:**
> i have a folder setup on the desktop with the file deluge which am trying to install but cannot install it even from the terminal because i cannot access it. Please if anyone can give a step by step instruction on configuring it to run i will greatly appreciate. thanks.

Mmm.

Strange.

Well..

Deluge has .deb packages that just need to be double clicked to be installed.

Download them here:

[http://deluge-torrent.org/downloads.php](http://deluge-torrent.org/downloads.php)

--

The permission thing is strange, are you the admin of the machine?

---

### Post by manishtech on 2008-08-21
If you want to install deluge, use the package manager, or apt

> sudo apt-get install deluge-torrent

---

