---
title: "Write-only file store"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by mdsanderson on 2008-05-15
Hi,

I once read an article (which I've lost) describing how to create a folder that is visible to all users, for the purpose of storing documents, photos etc.

The idea was that all users could see and write to this folder but as soon as a file was added it became the property of a different user (an account that nobody used, for example "safestore" or something like that).  Because the file changed ownership, all regular users could move or copy files to this folder and then not be able to delete them as they automatically became read-only.

I know what I want to achieve here but I don't know how to do it.  Please can someone HELP me?

Thanks

---

### Post by PinkFloyd102489 on 2008-05-15
Im way ahead of you, Ive already got it implemented on my computer to store my.... files.

I made a folder and chmodded (changed permissions) to 333. This implies that everyone can write and execute only, no read. Then to access the files, I just sudo or switch to root.

I dont know how to implement a switch to read only easily. You'd have to use some sort of script, but I cant think of how off hand.


EDIT: On second thought, you could make a script that changes permission to read only and add it to cron to run constantly. Rather crude, but it's all I got.

---

