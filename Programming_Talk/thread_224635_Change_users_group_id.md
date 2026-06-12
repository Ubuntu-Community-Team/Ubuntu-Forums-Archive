---
title: "Change users group id"
date: 2006-07-28
forum: Programming Talk
---

### Post by krisravn on 2006-07-28
Is it somehow possible for a user to change he/her own gid(group id). If the user is member of 3 groups, and he/her now want to change primary user group to another he/her is a member of? And how to do it?

regrads
krisravn

---

### Post by harisund on 2006-07-28
Are you using the console? If so you could execute "newgrp new_group_name" and you would be logged in, only this time your primary group would be new_group_name. 

I do not know how to do it over the GUI.

---

### Post by LordHunter317 on 2006-07-28
One uses the setgid() or setregid() function to change primary group for a process, but you can only set it to an arbitrary value if you're privileged.

Why in the world would you want to do that, though?

---

