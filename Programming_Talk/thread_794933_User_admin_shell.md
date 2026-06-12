---
title: "User admin shell"
date: 2008-05-15
forum: Programming Talk
---

### Post by Soulsmith on 2008-05-15
Hi, I need to create some way of allowing a user to do a few admin tasks from a menu (some of which may require root eg. restarting, shutting down) without being able to do anhything else. Im looking to do something like the new trixbox user menu if thats possible. I was thinking maybe locking a certain user into a bash script or something?

Any ideas would be greatly appreciated

---

### Post by Patb on 2008-05-15
Soulsmith, one way to do that would be to edit the sudoers file
```
sudo visudo
```
First "man sudoers" then probably you will want to do a search for examples to get the correct syntax. 

Cheers, Pat.

---

### Post by Soulsmith on 2008-05-15
Thanks Patb, I'll give that a shot, looks promising.

---

