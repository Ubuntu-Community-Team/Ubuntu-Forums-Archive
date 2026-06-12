---
title: "[SOLVED] I'm admin and I can't delete files"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by AlanInVancouverBC on 2008-10-26
I'm the only one on this computer. I installed ubuntu. I believe I've given myself permission to do everything. But I can't delete some files.

---

### Post by SunnyRabbiera on 2008-10-26
> **AlanInVancouverBC said:**
> I'm the only one on this computer. I installed ubuntu. I believe I've given myself permission to do everything. But I can't delete some files.

For this sort of thing in a terminal put in gksudo nautilus to do what you want here.
Files such as those are top level stuff and are locked off for a reason.

---

### Post by Crandom on 2008-10-26
You are an admin but do not have admin (or [font=monospace]root[/font]) powers unless you use the sudo command. This is a security feature, and is one of the reasons that linux is so secure. Type this command into a terminal:
```
gksudo nautilus /
```
and you will have full powers to change and delete files.

---

### Post by AlanInVancouverBC on 2008-10-26
Thanks. That worked.

---

