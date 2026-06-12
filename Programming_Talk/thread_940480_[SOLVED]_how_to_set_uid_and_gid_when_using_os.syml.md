---
title: "[SOLVED] how to set uid and gid when using os.symlink()?"
date: 2008-10-07
forum: Programming Talk
---

### Post by | MM | on 2008-10-07
Hi,

I am trying to create symlinks within a /home/user/subdir using pythons os.symlink() but it creates them without my current user privileges.

So, how do i go about creating a symlink with the logged in user's uid and gid?

Thanks for any advice.
Matt

EDIT: OK i think this is a stupid question, because obviously a symlink will inherit the privileges of the file its linked to?  So really i should use a hard link?

EDIT2: OK, ignore this post.  Sorry for wasting your life if you actually read this!  :P

---

### Post by geirha on 2008-10-07
It wasn't a stupid question, but since you solved it yourself, mark it as solved using the "Thread Tools" pull-down and people are more likely to skip this thread in favour of unsolved threads.

---

