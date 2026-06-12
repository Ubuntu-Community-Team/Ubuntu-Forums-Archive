---
title: "[SOLVED] Strange message at startup after restoring home directory"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-08-25
Hi.  I recently had to reinstall my system. (I fooled around where I shouldn't have fooled around. . .it was beyond repair)  I backed up everything in my home directory (hidden files and all) to my external drive, reinstalled, installed all my old packages, and then restored my home directory.  Everything is back to normal, except I get this message at the GDM after login:

users $HOME/.dmrc file is being ignored.  This prevents the default session and language form being saved.  File should be owned and have 644 permissions.  user's $HOME directory must be owned by user and not be writable by other users.

Any ideas?

Thanks!

---

### Post by iaculallad on 2008-08-25
> **pi.boy.travis said:**
> Hi.  I recently had to reinstall my system. (I fooled around where I shouldn't have fooled around. . .it was beyond repair)  I backed up everything in my home directory (hidden files and all) to my external drive, reinstalled, installed all my old packages, and then restored my home directory.  Everything is back to normal, except I get this message at the GDM after login:

users $HOME/.dmrc file is being ignored.  This prevents the default session and language form being saved.  File should be owned and have 644 permissions.  user's $HOME directory must be owned by user and not be writable by other users.

Any ideas?

Thanks!

On your terminal:
```

sudo chmod 644 /home/your_username/.dmrc
sudo chown your_username /home/your_username/.dmrc
sudo chmod -R 700 /home/your_username
sudo chown -R your_username /home/your_username
```

---

### Post by pi.boy.travis on 2008-08-25
> **iaculallad said:**
> On your terminal:
```

sudo chmod 644 /home/your_username/.dmrc
sudo chown your_username /home/your_username/.dmrc
sudo chmod -R 700 /home/your_username
sudo chown -R your_username /home/your_username
```

Thanks for posting.  The first two turn out fine.  The last two give me:

chmod: cannot access `/home/travis/.gvfs': Permission denied

chown: cannot access `/home/travis/.gvfs': Permission denied

I think that this is the very problem. . .

---

### Post by iaculallad on 2008-08-26
I don't know of a solution to that FUSE mount point problem. You might have bumped the bug:

[Bug 534284 – Root user can not access .gvfs]("http://bugzilla.gnome.org/show_bug.cgi?id=534284")

[Superuser cannot access ~/.gvfs folder when mounted]("https://bugs.launchpad.net/gvfs/+bug/225361")

---

### Post by pi.boy.travis on 2008-08-26
Hmmm. . . interesting.

The commands you posted seem to have fixed my issue though.  Thanks again!

Now if I can get eBox working on my server, I'll be all set!

---

