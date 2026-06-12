---
title: "Add a home directory to user"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Gias Kay on 2011-09-28
I created a new user using the --no-create-home option, but now I would like to see this new user having its default home directory. What should I do? Is there anyway to give it its default home directory straight, or I'll have to delete and recreate the user account? Thanks!

---

### Post by papibe on 2011-09-28
Be sure that the new user is not logged in. Then do:
```
$ sudo usermod -d /home/newuser newuser
```
Replace newuser with the actual homeless user.

Hope it helps.
Regards.

---

