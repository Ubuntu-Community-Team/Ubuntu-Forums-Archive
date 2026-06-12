---
title: "password not asked while mounting a partition"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by rahul_bhise on 2008-06-21
when in gutsy and before when i used to mount a partition (which where of my windows xp) i was asked for my password but in hardy i am not asked for one. also in system > administration > users and groups i cannot edit my account properties of users privilege. and author users property. also the unlock button is disabled.

---

### Post by Gallienus on 2008-06-21
I also use Hardy, and at first I was always asked for a password to mount my XP partition. However, one time I accidentally left 'Remember authorization' checked, and after that the system stopped asking me for a password. Maybe you did the same - it's an easy mistake to make.

If so, here's the solution:

1) System -> Administration -> Authorizations
2) Look at 'Storage' authorizations,  'Mount file systems from internal drives'.
3) If your user IS listed as having an explicit authorization there, select that user and press 'Revoke' to take away that authorization.

Now you will be asked for a password to mount the partition.

Hope this solves your problem. :)

---

### Post by rahul_bhise on 2008-06-21
also in system > administration > users and groups i cannot edit my account properties of users privilege. and author users property. also the unlock button is disabled.

---

### Post by rahul_bhise on 2008-07-03
also in system > administration > users and groups i cannot edit my account properties of users privilege. and author users property. also the unlock button is disabled.

---

