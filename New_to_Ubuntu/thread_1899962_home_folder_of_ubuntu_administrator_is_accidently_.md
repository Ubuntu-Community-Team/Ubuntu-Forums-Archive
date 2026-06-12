---
title: "home folder of ubuntu administrator is accidently deleted."
date: 2011-12-24
forum: New to Ubuntu
---

### Post by visakh0474 on 2011-12-24
I have two user accounts. one was administrative account and the other was normal account. My administrative account is accidently deleted in nautilus with sudo power.Now I can not log in to that account.When I check the free space in my ubuntu system, no free space is increased after the deletion of administrative account and so I assume that my home adminstrative account is still existing, but as all of the subfolders in the administrative account including trash is deleted, I can not restore my deleted account from trash.My second account which is not administrative account is still functioning.Is there any way to recover my deleted administrative account and all of its contents.I searched a lot, but cannot find a solution.

---

### Post by hansdown on 2011-12-24
Welcome to the forum, visakh0474.

Hope this psychocats tutorial helps.  

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

### Post by mcduck on 2011-12-25
> **visakh0474 said:**
> I have two user accounts. one was administrative account and the other was normal account. My administrative account is accidently deleted in nautilus with sudo power.Now I can not log in to that account.When I check the free space in my ubuntu system, no free space is increased after the deletion of administrative account and so I assume that my home adminstrative account is still existing, but as all of the subfolders in the administrative account including trash is deleted, I can not restore my deleted account from trash.My second account which is not administrative account is still functioning.Is there any way to recover my deleted administrative account and all of its contents.I searched a lot, but cannot find a solution.

If you deleted the directory while running Nautilus as root, it will be in root's trash directory. Take a look inside /root/.Trash...

---

### Post by visakh0474 on 2011-12-26
Thank you mcduck and hansdown.
I can able to find my deleted home folder in /root/.local/share/Trash/files.

---

### Post by visakh0474 on 2011-12-28
> **visakh0474 said:**
> Thank you mcduck and hansdown.
I can able to find my deleted home folder in /root/.local/share/Trash/files.
[QUOTE]The problem is thus solved.

---

