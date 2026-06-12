---
title: "How-To: Find a command for a given task"
date: 2006-04-14
forum: Outdated Tutorials &amp; Tips
---

### Post by Third Thoughts on 2006-04-14
I learned a really neat trick with the man command the other day from the local Linux mailing list I subscribe to. Since it seemed new to alot of the people on the list I thought I'd pass it along. 

The man command is great if you know a command but don't know what it does, but what if you want to do something but don't know a command. Well then you can type ```
man -k [keyword]
```. This will display a list of all the commands that have the word convert in their header or name.

If you want to refine your search then just go ```
man -k [keyword] | grep [second keyword]
```

Of course this is in the man manpage, but I hadn't stumbled upon it until someone else told me, so hopefully this will benefit someone like myself.

~Andrew S.

---

