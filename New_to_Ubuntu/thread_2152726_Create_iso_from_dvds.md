---
title: "Create iso from dvds"
date: 2013-06-08
forum: New to Ubuntu
---

### Post by opfeld on 2013-06-08
Looking for a program to create iso files from dvds. Was using k9copy but switched to lubuntu and can't seem to install it there. I also tried the dd command but got an error about input output and the resulting file was only 2.5mb. Any suggestions for me about a simple lightweight program for lubuntu to get this done?

---

### Post by benzarti on 2013-06-08
To create iso from dvd, you can use 
```

dd if=/dev/dvdrom of=disc.iso

```
If there is error message, then the disc is bad.

---

### Post by opfeld on 2013-06-08
Thanks I  tried to delete this post but couldn't figure out how, I hadn't enabled the restricted dvd playback yet. After doing so that code works great

---

### Post by claracc on 2013-06-09
> **opfeld said:**
> Thanks I  tried to delete this post but couldn't figure out how, I hadn't enabled the restricted dvd playback yet. After doing so that code works great

You cannot delete the post, you have to ask for it to a moderator ( I think).

Anycase, you can mark the thread as solved: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads) in order other people can get quicker solutions to their problems.

---

