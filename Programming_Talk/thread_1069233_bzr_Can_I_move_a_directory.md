---
title: "bzr: Can I move a directory?"
date: 2009-02-13
forum: Programming Talk
---

### Post by days_of_ruin on 2009-02-13
I want to move a directory that contains my bzr branch to a new directory called src.If I move all the files an the .bzr folder and the .bzrignore will everything still work? I am assuming bzr uses relative paths for files
so I think it should be fine but I just want to make sure before I ruin anything.

---

### Post by bruce89 on 2009-02-13
Not being versed in Bazaar much, moving the .bzr folder is not going to be a good idea. Perhaps the individual source files should be moved to src?

---

### Post by snova on 2009-02-13
You can, and it will work- mostly. And like bruce89 said, it's not really a good idea.

But, if you copy the .bzr directory somewhere new, nothing worse will happen then bzr assuming you've deleted all your files- which a **bzr revert** will return. (Note that any uncommitted changes will not be copied.)

Example:

```

~/tmp$ mkdir orig ; cd orig
~/tmp/orig$ echo 'hi' > hi
~/tmp/orig$ bzr init
Created a standalone tree (format: pack-0.92)
~/tmp/orig$ bzr add
adding hi
add completed
~/tmp/orig$ bzr commit -m 'foo'
Committing to: ~/tmp/orig/
added orig
Committed revision 1.
~/tmp/orig$ cd ..
~/tmp$ mkdir dest ; cd dest
~/tmp/dest$ cp ../orig/.bzr . -r
~/tmp/dest$ bzr status
removed:
  hi
~/tmp/dest$ bzr revert
 N  hi
~/tmp/dest$ cat hi
hi

```

This is only from a quick test- it's not guaranteed to work.

Now, if this branch were in a repository without trees- then you could. In fact, branches are meant to be equivalent to directories in this setting.

---

### Post by days_of_ruin on 2009-02-18
Yeah I realized that bzr has commands to mv files so its all good.;)

---

