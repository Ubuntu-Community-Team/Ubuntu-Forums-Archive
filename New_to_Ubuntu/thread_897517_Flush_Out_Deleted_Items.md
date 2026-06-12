---
title: "Flush Out Deleted Items"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by petronell on 2008-08-22
Hi,

I know this is going to be a simple question for someone with more knowledge than me.

In my deleted items are a couple of folders and for some reason I do not have permission to delete them. When I choose empty deleted items it says I do not have permission to delete some of the files.

When I look at the permissions on the file it is owned by root rather than me. If I try and restore the files to my desktop then it says I do not have permission to restore them.

So who can tell me the sudo command line to flush out my deleted items?

Thanks,

daveR

---

### Post by Paqman on 2008-08-22
You could do that a few different ways. 

In the terminal you could chown the files so that you owned them then empty the trash normally, or you could just use the rm command, so either
```

sudo chown -R username/username /path/to/file

Or JUST

sudo rm -rf /path/to/file

```

Or you could just open Nautilus as root with, Alt-F2 > gksu nautilus then delete them from there.

---

### Post by WRDN on 2008-08-22
In the Terminal, type:

```
sudo rm -rf ~/.local/share/Trash
```

---

### Post by petronell on 2008-08-22
Thanks for your help guys.

All sorted now.

daveR

:guitar:

---

### Post by porchrat on 2008-08-22
please mark thread solved

---

