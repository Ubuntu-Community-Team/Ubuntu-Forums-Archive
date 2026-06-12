---
title: "apt sources.list.d"
date: 2006-01-12
forum: Repositories &amp; Backports
---

### Post by marekdef on 2006-01-12
Hello,

I used apt on debian and redhat, where there were additional configuration
files placed in sources.list.d directory.

However, in ubuntu it does not work this way.

I tried to solve the problem on my onw and set
```
Dir::Etc::sourceparts "sources.list.d";
```
in /etc/apt/apt.conf.d/999sourceparts
and after doing ```
apt-config dump
``` i see that this exist.

But this does not cause apt-get update to fetch sources from the locations from files in sources.list.d directory.

Can you help me to enable this?
THX.

---

### Post by Mr_Grieves on 2006-01-12
I think this is what you're after: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

---

### Post by marekdef on 2006-01-13
[QUOTE=Mr_Grieves]I think this is what you're after: [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)[/QUOTE]

Thanks man,
but this is not the solution i am looking for.
This just adds custom line to the source.list file and that of course works.
Works means that i can download from repository.

But I just want to enable reading repositories from the sources.list.d directory.
It may be qustion more apt specyfic rahter that ubuntu related, anyway somebody knows the solution?

---

### Post by marekdef on 2006-01-13
[QUOTE=marekdef]
But this does not cause apt-get update to fetch sources from the locations from files in sources.list.d directory.
[/QUOTE]

Ok I solved the problem after looking at apt source.
Files in the sources.list.d should end with .list.
I changed and it works :KS.

---

### Post by refried on 2009-09-05
> **marekdef said:**
> Ok I solved the problem after looking at apt source.
Files in the sources.list.d should end with .list.
I changed and it works :KS.

Thanks marekdef.

---

### Post by graemev on 2009-12-16
Thanks also, that was what I was looking for

---

### Post by pletiplot on 2010-08-02
Thanks to marekdef as well. ;)

---

