---
title: "Accidently changed access to all folders"
date: 2024-08-06
forum: New to Ubuntu
---

### Post by railrash on 2024-08-06
I've broke my system. What i did is:
$ sudo find /. f -print0 | xargs -0 sudo chmod 0644
sudo: unable to execute /usr/bin/chmod: Argument list too long
sudo: unable to execute /usr/bin/chmod: Argument list too long
sudo: unable to execute /usr/bin/chmod: Argument list too long
sudo: unable to execute /usr/bin/chmod: Argument list too long
chmod: changing permissions of '/./sys/fs/cgroup': Read-only file system
xargs: sudo: Permission denied

So i think problem is that all folders now lost +X access

Now i cant use it. Even cant start recovery. What can i do to fix it ? 

Thanks

---

### Post by QIII on 2024-08-06
Unfortunately, this is not the sort of thing that can be "fixed" in any practical way.  To do so would require that one know exactly what permissions are required for each system file used by the OS.  There are thousands of those.  Not to mention what permissions are appropriate for your data, etc.

So let me ask you the hard question first:  Have you been in the habit of backing up your important data?

(Don't feel foolish.  This is the sort of mistake we have all made at one time or another!)

---

### Post by railrash on 2024-08-06
Yes I have backup. I also tried to run sudo find /. f -print0 | xargs -0 sudo chmod 0755 from recovery disk, but it didnt help ...

---

### Post by Rubi1200 on 2024-08-06
I would be curious to understand why you ran that command in the first place.

Surely you realized what it was going to do?

As an experiment? Maybe in a VM. 

On a live working system? Not a very good idea.

You will almost certainly need to reinstall and restore your backups.

---

### Post by currentshaft on 2024-08-06
.

---

### Post by TheFu on 2024-08-06
> **railrash said:**
> Now i cant use it. Even cant start recovery. What can i do to fix it ? 

Permissions and ownership matter.  Reinstall. That's the fix.  There isn't any quick fix that can be completed in 30 minutes like a reinstall will.  Then restore your backup data and in less than 1 hour, you'll be going again, having learned an important lesson.

BTW, stop abusing sudo.

---

### Post by ActionParsnip on 2024-08-06
Reinstall, restore casual user data from backups. Access and permissions is set for a reason. Steamrolling it as you did breaks the system. Unless you want to boot a VM on another system and set each and every single file as it should be which would take (more than likely) years.

---

