---
title: "adding users to ssh login..."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by B34ST1Y on 2008-12-01
Hi,

I want to add an additional user to my ssh login (run off my ubuntu desktop 8.10) ...how would I go about doing this, without adding a full fledged account to my desktop?

---

### Post by hyper_ch on 2008-12-01
why do you want the user then to have ssh access?

---

### Post by Joeb454 on 2008-12-01
Well if the user didn't have an account they wouldn't be able to do a whole lot on the computer. What exactly are you wanting to set the account up to do other than login

---

### Post by B34ST1Y on 2008-12-01
well...let's say I want (theoretically) 1,000 ssh accounts to hand out for students to log into for several classes. Do I have to muddy up my user list in the whole OS to do that? I guess perhaps i'm missing a concept here, or something

---

### Post by DGortze380 on 2008-12-01
> **B34ST1Y said:**
> well...let's say I want (theoretically) 1,000 ssh accounts to hand out for students to log into for several classes. Do I have to muddy up my user list in the whole OS to do that? I guess perhaps i'm missing a concept here, or something

'ssh accounts' are user accounts.
create a group named students
run a script to create the 1,000 users in the group students with appropriate access/permissions

---

### Post by spiderbatdad on 2008-12-01
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---

