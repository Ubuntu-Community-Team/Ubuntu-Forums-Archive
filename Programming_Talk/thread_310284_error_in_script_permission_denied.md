---
title: "error in script: permission denied"
date: 2006-11-30
forum: Programming Talk
---

### Post by Brando569 on 2006-11-30
as some of you know i wrote a script similar to autokernel the script worked before but for some reason i get this wierd error when trying to patch the kernel: 

**** Can't rename file /tmp/prv7jvWf to fs/proc/array.c.rej:Permission denied

even though im using sudo, this is the command im issueing: sudo bzcat ../patch-2.6.$kernel_version-$patch_version.bz2 | patch -p1

where patch and kernel version are the numbers inputted in the beginning of the script.

i tried using the root account through the terminal and it works perfectly, whats the problem??

---

### Post by po0f on 2006-12-01
Brando569,

The [FONT="Courier New"]sudo bzcat ...[/FONT] part of your script doesn't extend (?) through the pipe.  You can try this instead:
```
[FONT="Courier New"]bzcat ../patch-2.6.$kernel_version-$patch_version.bz2 | sudo patch -p1[/FONT]
```

[EDIT]

AFAIK, you don't need sudo privileges to bzcat a file, since it decompresses it to stdout, as opposed to a file where you would need such privileges.

---

### Post by Brando569 on 2006-12-01
awesome thanks

---

