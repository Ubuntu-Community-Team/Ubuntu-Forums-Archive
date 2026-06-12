---
title: "Two questions about git."
date: 2009-08-20
forum: Programming Talk
---

### Post by SledgeHammer_999 on 2009-08-20
Today I tried git to keep a local repo for my project, because I was tired to manually gzip my whole source instead of the files that actually changed. I managed to get it working but I have two questions:

I added a file that I misnamed. I renamed it and add it again. Of course git added it as a separate/new file. Is there a way to tell git to delete the MISNAMED file that it has "in it"? I already delete it from my working dir, but I don't want it to take space inside the ".git" folder.

This question is rather theoritical at this point: Let's say I modify a file and commit it. Then how do I revert this commit? Also let's say that I have done 100 commits with various changes:
1.Is there a way to revert all the tracked files to the state they were before the 60th commit?
2.Is there a way to revert a specific file to the state it was before the 60th commit?

ps. I am really happy that I started to use a VCS. :D

---

### Post by wmcbrine on 2009-08-20
> **SledgeHammer_999 said:**
> I added a file that I misnamed. I renamed it and add it again.Next time, do "git mv" instead.

> *Of course git added it as a separate/new file. Is there a way to tell git to delete the MISNAMED file that it has "in it"?*"git rm".

> *Let's say I modify a file and commit it. Then how do I revert this commit?*"git revert".

All these are in the man pages, which you should read.

> [i]Also let's say that I have done 100 commits with various changes:
1.Is there a way to revert all the tracked files to the state they were before the 60th commit?
2.Is there a way to revert a specific file to the state it was before the 60th commit?[/i]I'm pretty sure there is, but I'd have to look it up.

---

### Post by SledgeHammer_999 on 2009-08-20
> **wmcbrine said:**
> I'm pretty sure there is, but I'd have to look it up.

Very true. I found it confusing at first because I am not familiar with the terminology. Thank you for your help.

Now to answer my own questions:
> 1.Is there a way to revert all the tracked files to the state they were before the 60th commit?

Do a **git log** to find the name of the 59th commit and then do a **git revert <commit-name>**

> 2.Is there a way to revert a specific file to the state it was before the 60th commit?

Do a **git log** to find the name of the 59th commit and then do a **git checkout <commit-name> <path-to-file>**

---

