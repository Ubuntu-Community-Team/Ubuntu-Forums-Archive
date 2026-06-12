---
title: "weird permissions problem"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by jaskah on 2008-09-15
hello

i'm trying to move files to the trash but i get the following message:

Unable to trash file: Permission denied

i have access as owner and can read and write files.

what else could the problem be?

thanks in advance for any help!

---

### Post by jemate18 on 2008-09-15
> **jaskah said:**
> hello

i'm trying to move files to the trash but i get the following message:

Unable to trash file: Permission denied

i have access as owner and can read and write files.

what else could the problem be?

thanks in advance for any help!

what is the output of ls -l of your file?

---

### Post by jaskah on 2008-09-15
hello again

i just found the problem (maybe this will be useful for others...)

the "files" folder in

~/.local/share/.Trash/files

had only root permissions (don't ask me how this happened....).

i changed the permissions back to user and now i can delete everything as usual.

---

### Post by jemate18 on 2008-09-15
> **jaskah said:**
> hello again

i just found the problem (maybe this will be useful for others...)

the "files" folder in

~/.local/share/.Trash/files

had only root permissions (don't ask me how this happened....).

i changed the permissions back to user and now i can delete everything as usual.

please mark this thread as SOLVED

---

### Post by Kevbert on 2008-09-15
> **jaskah said:**
> hello again

i just found the problem (maybe this will be useful for others...)

the "files" folder in

~/.local/share/.Trash/files

had only root permissions (don't ask me how this happened....).

i changed the permissions back to user and now i can delete everything as usual.

It may have been that you copied some files from a CD/DVD that only had read permissions, hence the problem.

---

