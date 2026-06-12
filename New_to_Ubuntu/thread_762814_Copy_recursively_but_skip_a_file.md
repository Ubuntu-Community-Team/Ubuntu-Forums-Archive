---
title: "Copy recursively but skip a file"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by JDVyska on 2008-04-22
Hey guys.

I'm learning my way around Ubuntu, but I'm puzzled on this one.  I need to copy a directory (and all contents) with a couple exceptions.  I figure I can accomplish this by piping either find or ls results to copy, but I have no idea what the line would look like.

To give an example, let's take something I'm currently trying to do:

```
sudo cp -r /home/guest /etc/guest.bak
```

I need the cp to skip "/home/guest/.gvfs".   Any thoughts?

---

### Post by scorp123 on 2008-04-22
> **JDVyska said:**
>  I need the cp to skip "/home/guest/.gvfs".   Any thoughts? ```
rsync -av --exclude=/home/guest/.gvfs --exclude=/some/other/file/here --exclude=/even/one/more/file/here /path/to/original/files /path/to/where/they/should/go 
```

Please see "man rsync" for the manual and more details.

---

