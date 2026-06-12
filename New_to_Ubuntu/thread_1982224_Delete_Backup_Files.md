---
title: "Delete Backup Files"
date: 2012-05-18
forum: New to Ubuntu
---

### Post by MadMonkey1966 on 2012-05-18
I got a message this morning saying my HD was running very low of space. I know its only a 40GB one, but could not understand it.

After running Disk Usage, i found the problem. Simple Backup is keeping 30 days of Backups (which i really dont need). I have changed that setting, but how can i get rid of all these Backups.

If i go into File System --> Var --> Backups i can see them all, but it wont let me delete them. 

If i select and right click, there is no delete option (never understood that in Ubuntu) or if i select and push the Delete key (as normal) it does nothing.

A silly problem but......Help please :-k

---

### Post by MadMonkey1966 on 2012-05-18
Well, i just ran Simple Backup again hoping it would sort itself.

It said not enough room to do a Backup, but DID NOT give me any option to delete any old ones.

Surely i must be able to delete my own files ? OR am i guessing i have to do it through Terminal ? If so i will need help as i am no Ubuntu expert :(

Surely i dont have to delete Ubuntu  :roll:

---

### Post by Azdour on 2012-05-18
Hi,

See: [http://ubuntuforums.org/showthread.php?t=1793925](http://ubuntuforums.org/showthread.php?t=1793925) post #7.

You'll need to read the whole post so that files you delete do not end up in the root trash.

---

### Post by MadMonkey1966 on 2012-05-19
> **Azdour said:**
> Hi,

See: [http://ubuntuforums.org/showthread.php?t=1793925](http://ubuntuforums.org/showthread.php?t=1793925) post #7.

You'll need to read the whole post so that files you delete do not end up in the root trash.

Many thanks for your help...i will have a go when i get in from work ;)

---

### Post by MadMonkey1966 on 2012-05-21
> **Azdour said:**
> Hi,

See: [http://ubuntuforums.org/showthread.php?t=1793925](http://ubuntuforums.org/showthread.php?t=1793925) post #7.

You'll need to read the whole post so that files you delete do not end up in the root trash.

Thanks again Azdour :p

I managed to get rid of simple Backup program, BUT how do i delete the old backup files ?

---

### Post by drmrgd on 2012-05-21
If you follow the instructions in the link that Azdour gave you, you should be able to delete the files.  The problem is that the files are owned by root by default, and so you need elevated privileges to delete them.  Following the advice in that post will accomplish the goal.

As Azdour also says, though, be sure to follow the instructions exactly so that you really do remove the files from the system rather than just putting them into root's trash bin.

If it's still not working for you, please post back with any kind of errors you're getting.

---

### Post by Azdour on 2012-05-21
Hi,

I would use the same approach using:

```
gksu nautilus
```

Then navigate to where the old backup files are and do the same with shift+delete to delete them. Of course being very careful because you do not want to delete the wrong file or directory.

Having not used Simple Backup and I have no idea where the old backups are on the system.

---

### Post by MadMonkey1966 on 2012-05-22
> **Azdour said:**
> Hi,

I would use the same approach using:

```
gksu nautilus
```Then navigate to where the old backup files are and do the same with shift+delete to delete them. Of course being very careful because you do not want to delete the wrong file or directory.

Having not used Simple Backup and I have no idea where the old backups are on the system.

Thanks Azdour, i used your approach as it looked easier ;)

It seems to have deleted them. The only message i got back was -

> ** (nautilus:1932): WARNING **: Could not inhibit power management: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Name "org.gnome.SessionManager" does not exist

(nautilus:1932): Eel-WARNING **: "unique eel_ref_str" hash table still has 3 elements at quit time (keys above)

(nautilus:1932): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 3 elements at quit time (keys above)
Have no idea what it means, but as i say the files appear to have gone.

Many Thanks for your help & time, and drmrgd as well :)

---

