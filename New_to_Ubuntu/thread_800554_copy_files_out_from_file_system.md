---
title: "copy files out from file system?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-05-19
Hi, I know this may be a stupid question. But when I tried to copy some documents from file system to my external hard drive, I just can't "paste" it.

How could I copy the files out? Sorry, I'm an absolute beginner.

EDIT: I just checked the permission of my external hard drive, it's root. How could I make the permission to my current user account?

thanks

---

### Post by RequinB4 on 2008-05-20
Do you want to copy a little bit of files, or a lot of files?  Why do you want to copy your file system?

There is a GUI way to do this, and a command line way to do this, and I'll tell you both, but this is one of the instances where CLI is infinitly faster and better.

the terminal (applications - accessories - terminal) command is "cp" to copy

```

man cp

```

so, for instance, if I wanted to copy file a.odt to /media/disk/, i'd run

```

cp /path/to/a.odt /media/disk

```

BUT the files you want are protected so only people who know what they are doing can copy them :P.

You prefix commands with "sudo" give yourself temporary permissions.  See my signature for more details.  so now we have:
```

sudo cp /dev/configfile.conf /media/disk

```

This also works for directories.  For instance, to copy your entire file system (Not advised)

```

sudo cp / /media/disk/

```

Thus the GUI way is to give yourself permission in the file manager
```

gksudo nautilus

```

REMEMBER, the file system is protected for a reason, because you can make your computer UNBOOTABLE and lose ALL your files with the wrong click.

---

### Post by Psyker7 on 2008-05-20
You shouldn't have to change permissions...

What actually happens when you try to paste?

---

