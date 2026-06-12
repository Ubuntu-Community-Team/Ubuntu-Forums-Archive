---
title: "Writing permanent mount points?"
date: 2006-10-13
forum: Programming Talk
---

### Post by dabear on 2006-10-13
Hi, i am beginning on an app to write permanent mount points. Using the mount command, I can only temporarily mount file systems, they will dissapear on next reboot. I think the only way is to edit /etc/fstab , but this is stopping me:
> **"man fstab"]
       The  file  fstab contains descriptive information about the various file systems. [b] fstab is only read by programs,
       and not written said:**
>  it is the duty of the system administrator to properly  create  and  maintain  this  file.   Each
       filesystem  is  described on a separate line; fields on each line are separated by tabs or spaces.  Lines starting
       with &#8217;#&#8217; are comments.  The order of records in fstab  is  important  because  fsck(8),  mount(8),  and  umount(8)
       sequentially iterate through fstab doing their thing.

Is there a better way of doing it?

---

### Post by meng on 2006-10-13
Better in what sense? Editing the fstab is the standard method - what is it about this method that doesn't suit you?

---

### Post by Peepsalot on 2006-10-13
you can edit your fstab, you just have to do it with administrative permissions aka "sudo".  ubuntuguide.org got me through it pretty painlessly.

here is a specific example for NTFS
[http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://ubuntuguide.org/wiki/Dapper#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by dabear on 2006-10-13
Hi, the issue here isn't how I edit fstab, but the fstab man page, which strictly tells me that «fstab is only read by programs,
and not written;». I was wondering if there were any programs similar to mount, that I could call to do the mounting for me

---

### Post by Peepsalot on 2006-10-13
I think the statement from the man page is not entirely true.  It seems that is a generalization of how it usually works.  ftsab is not normally written to during the boot process or any other time except when the user is doing some administrative configuration.

But, a text editor(gedit,nano,etc.) is obviously just a program like any other, and it is what someone would normally use to write to fstab.  So yes fstab can be read, and written to by a program.

If you want to write an application that writes to fstab, then as long as you invoke your application with sudo, I don't think there is a problem.

Or maybe I just still don't understand your issue.

---

### Post by meng on 2006-10-13
Yes if you edit your fstab, then the next time you boot, all your drives will be mounted according to the fstab, and you will have permanent read/write access!

---

### Post by dabear on 2006-10-13
> **Peepsalot said:**
> I think the statement from the man page is not entirely true.  It seems that is a generalization of how it usually works.  ftsab is not normally written to during the boot process or any other time except when the user is doing some administrative configuration.


If you want to write an application that writes to fstab, then as long as you invoke your application with sudo, I don't think there is a problem.

Or maybe I just still don't understand your issue.
Thank you for your clarification :)

Thinking about using bonobo running in sbin though, so sudo shouldn't be needed, if I'm correct

> **meng said:**
> Yes if you edit your fstab, then the next time you boot, all your drives will be mounted according to the fstab, and you will have permanent read/write access!
Hehe, now really? I kinda knew that already, and that wasn't the issue.

I just thought that there might have been a command similar to mount, that mounts permanently to fstab. I haven't found any flags for mount that do this, either.

---

### Post by meng on 2006-10-13
> **dabear said:**
> Hehe, now really? I kinda knew that already, and that wasn't the issue.
I just thought that there might have been a command similar to mount, that mounts permanently to fstab. I haven't found any flags for mount that do this, either.
Then we're not understanding your problem. You don't mount anything TO fstab! fstab is simply a roadmap indicating which devices should be mounted to which mountpoints. I have to conclude that either you don't really understand what you're talking about, or you're really much more knowledgeable about these things than most of us...

---

