---
title: "Owning a directory"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by gunnerb on 2008-08-05
Hi Folks,  I've been out of this for a few months and have a couple of questions.
1.  Is there a "tree" I can look at to see exactly how Linux is set up.  I figure that if I can visualize the tree and how the OS folders act/interact I may have an easier time picking this up.  (I was familar with MS-Dos, and have used windows for some time.)
2. How do I 'Own' a directory?  I receive an error message that tells me
"users $HOME/.dmrc file is being ignored.  This prevents the default session and language frim being saved.  File should be owned by user and have 644 permissions.  Users $HOME directory must be owned by user and not writable by other users."    I'm the only user of this machine!!

Thanks much
Gunner

---

### Post by sisco311 on 2008-08-05
2. open a terminal(Applications -> Accessories -> Terminal)
and type:
```
sudo chown -R $USERNAME: $HOME
chmod 0644 $HOME/.dmrc
```

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by tamoneya on 2008-08-05
here is some info about the filesystem layout.

[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)

---

### Post by gunnerb on 2008-08-05
Thanks very much folks.  I'll see what the sites you've recommended do for me.
appreciate your time.
Gunner

---

