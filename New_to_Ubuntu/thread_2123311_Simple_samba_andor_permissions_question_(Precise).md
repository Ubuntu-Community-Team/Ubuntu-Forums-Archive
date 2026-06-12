---
title: "Simple samba and/or permissions question (Precise)"
date: 2013-03-07
forum: New to Ubuntu
---

### Post by MrDetermination on 2013-03-07
Three users:
mrd (M)
samba (S)
test (T)

M is the user account on the machine
T is a read only account except one place where it can write
S is the samba account that all the machines backing up to the server use (needs full access)

I want M to have full access to the files and folders S makes. And T needs to be able to read them.

There are only four main directories shared:

/mnt/raid5/temp/ - all full access

/mnt/raid5/purgatory/ - all full access

/mnt/raid5/projects/ - M and S full access

/mnt/raid5/vault/ - M and S full access. Sub directories of this one need read access for T.
E.g. /mnt/raid5/vault/movies - T needs to see this as a read only share. Also, S needs to be able to create this. Example: S creates /mnt/raid5/vault/movies/Bond and a media center using T as a login sees /server/movies as a read only share where they can open Bond and play Goldfinger.avi

---

### Post by MrDetermination on 2013-03-07
Almost there...

Everyone can read where I want them to read and write where I want them to write. One last thing to fix. 

If S writes in /temp T should be able to delete and vice versa. Right now when either tries to delete the other I'm getting denied due to permissions.

---

