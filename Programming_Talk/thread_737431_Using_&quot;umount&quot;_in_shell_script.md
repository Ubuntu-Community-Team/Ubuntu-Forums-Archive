---
title: "Using &quot;umount&quot; in shell script?"
date: 2008-03-27
forum: Programming Talk
---

### Post by Gerlads Mod on 2008-03-27
I am having trouble formatting my PSP's Memory Stick within a shell script.

I won't post the whole script just the part that is messing up.
Shell Script:
```

device=/dev/sdb1

mkfs.vfat "$device"

```

That outputs:
```

mkfs.vfat 2.11 (12 Mar 2005)
/media/disk: No such file or directory

```
/media/disk is were the PSP was mounted but I unmounted it earlier in the script.


And I don't want to do this:
```

mkfs.vat /dev/sdb1

```
I do not want that in my case.

Thanks.

---

### Post by WW on 2008-03-27
Don't put spaces around the =, and don't use the $ in front of the name when you assign the value.  E.g.
```

device=/dev/sdb1
echo $device

```

---

### Post by Gerlads Mod on 2008-03-27
Thanks for the advice.
I edited the first post and fixed it.

---

### Post by Gerlads Mod on 2008-03-27
This is really wierd.

I tried:
**mkfs.vfat "$device"**
And I tried:
**mkfs.vfat $device**
And it doesn't work.

But this works with things like:
**fdisk "$device"**
And
**umount "$device"**

Does anyone know how this works.

---

### Post by WW on 2008-03-27
> **Gerlads Mod said:**
> This is really wierd.

I tried:
**mkfs.vat "$device"**
And I tried:
**mkfs.vat $device**
And it doesn't work.

What do you mean "...it doesn't work."?  What happened?

EDIT: Does the command "mkfs.vat" even exist?  The mkfs.* commands are in /sbin, and on my system, there is no "mkfs.vat".

---

### Post by Gerlads Mod on 2008-03-27
> Does the command "mkfs.vat" even exist? The mkfs.* commands are in /sbin, and on my system, there is no "mkfs.vat".

Sorry typo. I meant mkfs.vfat.
And it just says:
```

mkfs.vfat 2.11 (12 Mar 2005)
/media/disk: No such file or directory

```

/media/disk is were it was mounted earlier in the script, until I unmounted it.

---

### Post by bvmou on 2008-03-27
Have you looked at pmount and pumount?

---

### Post by Gerlads Mod on 2008-03-27
No I tried to change the title but it didn't work.

I need help with mkfs.vfat

---

### Post by mssever on 2008-03-27
> **Gerlads Mod said:**
> I need help with mkfs.vfat
Assuming you've fully updated the original post (since you haven't re-posted the relevant code), you have an error in assigning the device. It should be ```
device=/dev/sdb1
```The $ means to get the value, which doesn't make sense if you're trying to set a variable.

---

### Post by Gerlads Mod on 2008-03-27
Godamn another typo.

I'll fix that too.

---

