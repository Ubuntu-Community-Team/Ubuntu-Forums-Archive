---
title: "Samba server - lock file?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by Jim_in_Germany on 2008-07-07
Hi there,

Following some helpful advice from the forum, I have managed to set up a samba server at work for the purposes of making backups.
[http://ubuntuforums.org/showthread.php?t=842373]("http://ubuntuforums.org/showthread.php?t=842373")

I have set up the server so that the three Windows clients, who have their files backed up there on a regular basis, also have a shared folder where they can swap documents.

The problem is that they now want to store documents on the server and work on them there (so that everyone always has the most up to date version).
My question is, how do I configure the samba server so that a document is locked for everyone else if one user has it open and is working on it?

I basically want to avoid that two people work on the same document at the same time and in the end only one version is saved and the other is lost.

As ever, grateful for all help received.

---

### Post by superprash2003 on 2008-07-07
i think if one client opens a .doc file for example.. then if another client tries to open the same file, it would open as read-only.. i think this is how it works

---

### Post by Jim_in_Germany on 2008-07-07
Cheers Superprash,

I guess the easiest thing to do is to set up a samba server at home and check this out.
What you say makes sense, and would make my life easy, so I hope it is indeed the case.
I'll post back here with the results when I have tried it out.

---

### Post by Jim_in_Germany on 2008-07-10
So, it kind of works.
I am testing this at home with one Linux PC running Samba and two windows xp clients.
When I access a file stored on the server from one of the windows clients, I can alter it and change it as I wish.

Whilst this file is open on xp client one, I can open it on xp client two, but as read only.

This is very good.

However, when I close the file on both xp clients and then re-open it on xp client two it is still showing as read only. Even when I turn off xp client one, the file is still showing as read only for xp client two.

Is there any way to change this, so that the file is only locked for as long as it is open on another computer and then it is released again?

Thanks muchly.
Jim

---

### Post by Jim_in_Germany on 2008-07-10
I solved one problem and created another.
I added "create mask 0765" to my config file and now both clients can access and save files in the shared folder without any problems.

My new problem, they can both do this at once.
If client one opens a file in the shared folder of the samba server so as to modify it, client two can also open it and alter it at the same time.

How can I configure the server that the file would be then locked for client two??

It doesn't happen automatically

Thanks for any help
Jim

---

### Post by Jim_in_Germany on 2008-07-12
Solved my own problem again!
It depends on the program on the Win computers if they have a locking mechanism.
For example, I was trying this with text files. Editor doesn't have a locking mechanism.
When I try it with Word (for example). Everything works like it should.

---

