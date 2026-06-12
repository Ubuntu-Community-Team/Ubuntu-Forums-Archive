---
title: "users and groups"
date: 2014-04-24
forum: New to Ubuntu
---

### Post by sniper8752 on 2014-04-24
I have a user that is part of the group, itdept.  in /etc/group, it looks like this:
itdept:x:1000:bob,sally
When I am logged in as bob, and run the command groups, this is what I see:
bob, sudo

Why doesn't idept come up in there as well?

---

### Post by steeldriver on 2014-04-24
When did you add the user bob to the group? group membership only applied when a new login shell is started

---

### Post by sniper8752 on 2014-04-24
didn't know that - thanks!  it fixed it.

---

