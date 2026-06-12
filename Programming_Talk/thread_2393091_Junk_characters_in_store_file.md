---
title: "Junk characters in store file"
date: 2018-05-29
forum: Programming Talk
---

### Post by ab1506 on 2018-05-29
[COLOR=#000000]We have a C++ based application that used to run on RedHat. At some point last year we decided to go ahead with Ubuntu instead of RedHat. Since last year our application has been running smoothly on Ubuntu however, we recently noticed that on Ubuntu, whenever there is a sudden power failure, and if there is a message being written to the store file, it lands up writing junk characters into the store file. When the application starts again it goes into an infinite loop on reading the junk characters. We are able to easily simulate this issue on Ubuntu. However, when we tried to simulate the same on RH we were not able to. We are using Ubuntu 16.04.2 LTS. I'd appreciate any help.[/COLOR]

---

### Post by Skaperen on 2018-05-30
can you try this with your data on an XFS type filesystem?  there are ways to write data that preserves integrity better at the expense of performance (such as journaling).  i have heard that XFS is better at this than EXT[34].  maybe XFS is just better at journaling.

and there are things you application can do, as well.

it sounds like the file was expanding at the time and the actual data was written after the inode or pointer blocks were written.

also try mounting in "sync" mode just for testing. this make everything run slower so you won't want this for production.

also your data format lacks its own data integrity checks.  most programs lack it, assuming the OS provides it.

---

