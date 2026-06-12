---
title: "[SOLVED] SVN phantom folder?"
date: 2008-06-01
forum: Programming Talk
---

### Post by Stex on 2008-06-01
I'm looking to turn one of my bigger PHP projects into more of a community effort by putting it on Subversion. Problem is I've never used a version control system. I've been reading [Version Control with Subversion](http://svnbook.red-bean.com/) and it's all making pretty good sense (I've just finished chapter 3) but there's still one thing that's unnerving me...

Instead of using a SQL database my project stores it's data in a directory called "storage" which is in the root of the program files. On the SVN server I want that folder to contain the default settings that would be shipped with the program. But in my working directory it needs to have other things that mustn't be on the SVN server (like usernames & passwords).

So is it possible to have a folder that:
- Is downloaded on the first SVN checkout done
- Does not upload the programmer's working version to the SVN server
- Does not download & apply updates from the SVN server

Thanks

---

### Post by geirha on 2008-06-01
The common way to do this is to simply not have any configuration files in version control, only examples/templates. I.e., if you have foo.conf, then keep foo.conf out of the version control, and instead make foo.example or examples/foo.conf  or similar, with default values.

If you want to also want to have version controlled configuration files, use a seperate, private repository.

---

