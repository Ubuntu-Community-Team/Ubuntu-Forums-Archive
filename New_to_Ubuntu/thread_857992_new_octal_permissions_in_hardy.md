---
title: "new octal permissions in hardy?"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by hovzio on 2008-07-13
Hi, I've noticed that the octal permissions seem to have slightly changed. ( I am assuming.) I set up nautilus to show the permissions and I'm getting numbers like 40700, 100644 and so on. I'm used to have three numbers. (UGO) If a stickybit, setgid etc. is set it will be set in in front of the three traditional octals. What is this 100 and 40 all about. Does it affect chmod and so forth? (I'm assuming/hoping not...) Thanks for any input:)

---

### Post by cariboo on 2008-07-13
Permissions haven't changed they've alway been that way. Hve a look here:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

It will explain things better than I can.

Jim

---

### Post by hovzio on 2008-07-13
> **cariboo907 said:**
> Permissions haven't changed they've alway been that way. Hve a look here:

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)

It will explain things better than I can.

Jim

hi, thanks but that link isn't really explaining why I have numbers such as 40700 and 100644 and so forth. I have not seen this before. I understand the sheer basics of permissions such as 700, 644, 4755 and so on. What I fail to get (and maybe I'm just dumb) is these 40 and 100 prefixes. 

What does this mean:  40700, 100644 ??

---

### Post by logos34 on 2008-07-13
> **hovzio said:**
> What I fail to get (and maybe I'm just dumb) is these 40 and 100 prefixes. 

I believe 40 is for directories, and 100 for files

---

