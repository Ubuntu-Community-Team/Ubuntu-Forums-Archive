---
title: "result of the set command"
date: 2019-08-28
forum: New to Ubuntu
---

### Post by hk42 on 2019-08-28
Hi me again.
On most of the linux devices I use typing :
set 
in a console or on SSH gives useful informations.
With Ubuntu it is not the case.
Or it is well hidden in the result.
Is there a way to improve that ?
Or a reason ?

---

### Post by Holger_Gehrke on 2019-08-28
Unless you're used to some device (or distribution) which uses another shell than the bash or has an external 'set'-command, you should be used to 'set' without options dumping the current environment variables and defined functions. That's exactly what it does on Ubuntu, but there's a lot of stuff defined, especially since the command-line completion uses many shell-functions. On my system the output of 'set' is ~2700 lines with the last ~2600 lines being shell functions. So if you're looking for the environment, 'set|less'  and using the search-function of less (key '/') might be easier. Or you could use 'declare -p'  to see just the environment printed as 'declare' statements which give the type and attributes in addition to name and value.

Holger

---

### Post by TheFu on 2019-08-28
Perhaps the output from 'env' is more what the OP seeks?

---

### Post by hk42 on 2019-08-29
Yes I'm happy with the result of the env program.
man env is good too :-)
man bash says that in "posix mode" set only display environnement variables that seems OK too 
to get in posix mode one type 
set -o posix
set +o posix restores the original behavior
this change is only valid in the curent console.
Thanks for your answers.

---

