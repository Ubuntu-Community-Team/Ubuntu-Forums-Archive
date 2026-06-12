---
title: "inotify confusion"
date: 2006-04-02
forum: Programming Talk
---

### Post by cmatheson on 2006-04-02
I need to know when a file is added to a list of directories. inotify seems like the perfect solution for this sort of thing... unfortunately, I am not having a whole lot of luck in getting it to work for me right now.  I have been following a [tutorial]("http://www.linuxjournal.com/article/8478") in Linux Journal.  My problem is that I cannot link the program that I have built... here are the errors:

undefined reference to `inotify_init'
undefined reference to `inotify_add_watch'

So I wasn't even sure where the functions were supposed to be defined, but after googling around for a bit it looks like inotify calls were added to glibc in version 2.4 (Dapper is currently at version 2.3.5).  I know that their are programs utilising inotify in ubuntu, so my question is: how?

TIA

---

