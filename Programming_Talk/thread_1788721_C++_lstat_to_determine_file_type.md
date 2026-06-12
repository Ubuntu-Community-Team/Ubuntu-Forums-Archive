---
title: "C++ lstat to determine file type"
date: 2011-06-23
forum: Programming Talk
---

### Post by zobayer1 on 2011-06-23
I want to determine what is the type of the file. So far, using lstat() / stat(), I can get following types:

[LIST]
[*]regular file
[*]directory
[*]character device
[*]block device
[*]FIFO (named pipe)
[*]symbolic link
[*]socket
[/LIST]
But I still need to know about 3 more types, I don't know how to get them, I googled but found no satisfying answer. I need the three following types

[LIST]
[*]Archive state 1
[*]Archive state 2
[*]Whiteout
[/LIST]
Please someone tell me how to get these. Thanks in advance.

---

### Post by Arndt on 2011-06-23
> **zobayer1 said:**
> I want to determine what is the type of the file. So far, using lstat() / stat(), I can get following types:

[LIST]
[*]regular file
[*]directory
[*]character device
[*]block device
[*]FIFO (named pipe)
[*]symbolic link
[*]socket
[/LIST]
But I still need to know about 3 more types, I don't know how to get them, I googled but found no satisfying answer. I need the three following types

[LIST]
[*]Archive state 1
[*]Archive state 2
[*]Whiteout
[/LIST]
Please someone tell me how to get these. Thanks in advance.

The first list are distinguished by the operating system, but what are the other ones? I have never heard of them.

The program 'file' may be useful - it looks into files and tries to determines what the data inside represents.

---

### Post by zobayer1 on 2011-06-23
I think file program uses mime type, and I think that will not be enough to detect them. Do you know of any other means of detecting them? May be from dirent structure or somewhere else?

---

### Post by dwhitney67 on 2011-06-23
> **zobayer1 said:**
> I think file program uses mime type, and I think that will not be enough to detect them. Do you know of any other means of detecting them? May be from dirent structure or somewhere else?

Can you answer this question, that was posed by Arndt

> 
... but what are the other ones?


He is asking about these file types:
[LIST]
[*]Archive state 1
[*]Archive state 2
[*]Whiteout
[/LIST]

These are not well known file types; where did you get this list?

---

### Post by zobayer1 on 2011-06-23
> **dwhitney67 said:**
> Can you answer this question, that was posed by Arndt



He is asking about these file types:
[LIST]
[*]Archive state 1
[*]Archive state 2
[*]Whiteout
[/LIST]

These are not well known file types; where did you get this list?

Hmm, I got them from my assignment paper. It required me to make the "ls" program myself, well, I have done that as much as I could. For the long format requirement, you know, if it is a directory, then 'd' is shown with permission, for links, 'l' is shown, similarly, I am asked to show A, a, w respectively for the above three, but I have searched the net, only thing I get is whiteout is some sort of mysterious file, but no where found how to get them.

---

### Post by Arndt on 2011-06-23
> **zobayer1 said:**
> Hmm, I got them from my assignment paper. It required me to make the "ls" program myself, well, I have done that as much as I could. For the long format requirement, you know, if it is a directory, then 'd' is shown with permission, for links, 'l' is shown, similarly, I am asked to show A, a, w respectively for the above three, but I have searched the net, only thing I get is whiteout is some sort of mysterious file, but no where found how to get them.

I hadn't heard of them, but when I do a google for "whiteout file type", it returns a lot of relevant-looking hits. This may be the best one: [http://free-it.de/archiv/talks_2005/paper-11254/paper-11254.html](http://free-it.de/archiv/talks_2005/paper-11254/paper-11254.html)

---

### Post by dwhitney67 on 2011-06-23
> **Arndt said:**
> I hadn't heard of them, but when I do a google for "whiteout file type", it returns a lot of relevant-looking hits. This may be the best one: [http://free-it.de/archiv/talks_2005/paper-11254/paper-11254.html](http://free-it.de/archiv/talks_2005/paper-11254/paper-11254.html)

That's an interesting document.  Personally, I have never heard of the 'whiteout' file.

From brief peek I took at the document, it seems that only EXT2 and RamFS file-systems support this file type.  If one is using a default installation of Ubuntu, then I believe only ext3 file-systems are used, thus negating the possibility of finding a whiteout file.

---

### Post by zobayer1 on 2011-06-23
> **Arndt said:**
> I hadn't heard of them, but when I do a google for "whiteout file type", it returns a lot of relevant-looking hits. This may be the best one: [http://free-it.de/archiv/talks_2005/paper-11254/paper-11254.html](http://free-it.de/archiv/talks_2005/paper-11254/paper-11254.html)

Thanks, going through your link, I found this:
```
[FONT=monospace]
[/FONT]#define S_IFWHT  0160000  /* whiteout */
#define S_ISWHT(m)  (((m) & S_IFMT) == S_IFWHT)[FONT=monospace]
[/FONT]
```

I have also found that 
> 
At the time of writing this, the only two file systems with support for whiteouts are the second extended (EXT2) and the RamFS file system.


Whiteout are used in BSD and they are not used for inode structure.

Are these available in EXT4? Or I just ignore these three type?

For compressed states, There is a bitpattern S_IFCMP but I am not sure whether they will do what I need. I think, these 3 are implementation dependent and not a part of posix standard.

---

### Post by psusi on 2011-06-23
Ext3 and 4 are ext2 with a few new features enabled.  Whiteout is a relatively new file type added to Linux to support union filesystems.  It is a marker that indicates that the file has been deleted and so should not be reported as existing.  As such, I do not think it is possible to ever see them from userspace.

The other two types seem to be made up, so I think your professor gave you an impossible assignment.

---

### Post by zobayer1 on 2011-06-23
> **psusi said:**
> The other two types seem to be made up, so I think your professor gave you an impossible assignment.

Who knows, I have been into system programming for the last few months. And, I am starting to believe, probably everything is possible in linux & C.

However, there are options in stat for whiteout, although they say that is defined on BSD system, still, if it is not possible to see then in userspace, why the options are present?

---

### Post by psusi on 2011-06-23
> **zobayer1 said:**
> Who knows, I have been into system programming for the last few months. And, I am starting to believe, probably everything is possible in linux & C.

What language you are using doesn't matter.  If there is no such file type, then it is impossible to list it.

> **zobayer1 said:**
> However, there are options in stat for whiteout, although they say that is defined on BSD system, still, if it is not possible to see then in userspace, why the options are present?

You may be able to see a whiteout if you look at the underlying filesystem after a union mount has created the whiteout there.  The man page lists many bits that are not defined in Linux.  They are in the "Other Systems" section for information purposes only.  The symbols aren't actually defined in the Linux headers.

---

### Post by zobayer1 on 2011-06-23
I think I have found about the rest two, archive state 1 and 2. state 2 is the one without compression.
I think he added those in the assignment intentionally. May be "not possible" is also a correct answer. However, the archive types has nothing to do with stat data. But if you use default ls, it will colorize the archive files with different color... So I think, I need to take a look into the ls source, but I am really afraid of that 3000+ lines of coding... :(

---

### Post by psusi on 2011-06-23
Ohh... ls colorizes files whose name ends in .gz.  It is just a name thing.

---

### Post by zobayer1 on 2011-06-23
> **psusi said:**
> Ohh... ls colorizes files whose name ends in .gz.  It is just a name thing.

oh... I thought it checks something else...

So, I think I would better get those two from "file" program, although not a good way, but I think it will work.

---

