---
title: "Can't Access My Partitions After Running fsck Command"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by multisystem on 2011-12-27
Hi all
I had run fsck command . Since then, I can't access my partitions any more.

An error message appears to say
```

You do not have the permissions necessary to view the contents of <partition name>.

```

I tried to run *gksu nautilus, *and it works, but this is the only way to do it.

Is there a way to open my partitions normally again?

Thanks

---

### Post by TeoBigusGeekus on 2011-12-27
Change the ownership of their mount points (if we're talking about linux partitions, ie. ext3, ext4, etc.)
```
sudo chown -R yourusername: /media/mountpoint
```

---

### Post by multisystem on 2011-12-27
Thanks for your fast reply.

What if they're NTFS partitions?

---

### Post by TeoBigusGeekus on 2011-12-27
Try, but I don't know about the result.
Post with the outcome.

---

### Post by multisystem on 2011-12-27
It has no effect.

Actually the following is written in the terminal for every file in the partition
```

/media/<parition name>/<folder>/<file>: Read-only file system

```

---

### Post by TeoBigusGeekus on 2011-12-27
Did you try it with sudo?

---

### Post by multisystem on 2011-12-27
Yes, sure.

---

### Post by TeoBigusGeekus on 2011-12-27
> **multisystem said:**
> Yes, sure.

Then I can't say; anyone else?

---

