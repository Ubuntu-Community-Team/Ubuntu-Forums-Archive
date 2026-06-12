---
title: "Where does Kindle Cloud Reader App store the downloaded books?"
date: 2018-08-12
forum: New to Ubuntu
---

### Post by WurmD on 2018-08-12
Hi guys, 

It's been four years since [https://ubuntuforums.org/showthread.php?t=2220004](https://ubuntuforums.org/showthread.php?t=2220004), and thus things have changed.

I'm searching with Nautilus and failing to find where in my computer is Amazon Kindle Cloud Reader app ([http://read.amazon.com](http://read.amazon.com)) storing my downloaded books.

Would you kindly help investigate?

---

### Post by TheFu on 2018-08-12
I won't use amazon for reading books - they track too much.
But if I wanted to find where things are stored, I'd perform a backup, download a new book to read, perform another backup, then ask the backup tool to show differences between the 2 versions. Simple. Should take just a few minutes. This assumes the backup tool you use isn't brain dead.

Or you can use 'find' to locate changed files over the last day.
```
$ find ~/ -mtime -1 -print
```
That will show much more than you want, unless you can avoid using the computer for a day.

Or you can create a new userid, login to it, only install the amazon stuff, see where new files are placed using **find**.

I would guess that amazon uses HTML5 local objects in the browser, but that is just a guess.

I can come up with a few other ideas using LVM too.

---

### Post by WurmD on 2018-08-12
Pretty good suggestions :) Thanks

In the meanwhile I found [https://askubuntu.com/questions/1011989/where-are-amazon-kindle-ebooks-on-my-linux-pc-after-i-download-them-for-offline](https://askubuntu.com/questions/1011989/where-are-amazon-kindle-ebooks-on-my-linux-pc-after-i-download-them-for-offline) , and kinda lost heart to carry on
(XD)

---

