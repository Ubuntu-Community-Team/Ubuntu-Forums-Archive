---
title: "Permission problem: mod 755 but can't cd into"
date: 2016-03-20
forum: New to Ubuntu
---

### Post by lochdhu10yr on 2016-03-20
I thought I understood Unix / Linux permissions.  This is Ubuntu 15.10.

```

plex@howardServer:/media$ ls -l
total 4
drwxr-xr-x+ 4 root sambashare 4096 Mar 20 15:26 howard
plex@howardServer:/media$ cd howard
bash: cd: howard: Permission denied

```

User plex should be a member of they sambashare group, but even if it isn't, with permission mod 755 this should work.  Yes?  Why can't user plex enter directory howard?

---

### Post by papibe on 2016-03-20
Hi lochdhu10yr. Welcome to the forum ):P

You can confirm plex's groups by running:
```
groups
```
Also, the directory seems to have additional ACLs set (Access Control Lists) because of the '+' at the end of the permissions. In order to check the list run:
```
getfacl howard
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by lochdhu10yr on 2016-03-21
Thanks papibe,
ACLs were the answer.  This command got me back to the permissions rules I understand:
```

sudo setfacl --remove-all howard

```

---

### Post by papibe on 2016-03-21
Great! :D

When you have the chance, please mark the thread as solved ([here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")'s how to do it).

Regards.

---

