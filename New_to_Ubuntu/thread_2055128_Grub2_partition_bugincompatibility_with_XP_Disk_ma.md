---
title: "Grub2 partition bug/incompatibility with XP Disk management?"
date: 2012-09-08
forum: New to Ubuntu
---

### Post by Greyriver on 2012-09-08
I'm very new to Linux and I'm in the middle of changing from Windows XP to ubuntu so I'm dual booting.

This works, but then if I do anything at all to any partition from XP's disk management then most of the partitions become corrupted.

Now I realise this might be an XP bug, but if it's triggered by ubuntu doing something non-standard to the partitions then I need to understand it better.

Example:
C: Windows XP   Primary
D: Ubuntu  20gb Primary
Extended:
   Swap    2gb  Logical
E: NTFS    20gb Logical
F: NTFS    20gb Logical

If I now use windows to delete F: then the partitions after the swap become scrambled and meaningless.

It looks though XP doesn't understand linux partitions, but surely the partition structure would be identical and only the filesystem would change so this shouldn't happen. 
Anyway if this always happens wouldn't there be 1000s of people posting about it? I've been searching with no luck.

---

### Post by coffeecat on 2012-09-08
> **Greyriver said:**
> 
Now I realise this might be an XP bug

It is, or rather it's a "feature" of Disk Management in all versions of Windows. DM gets hopelessly confused by logical partitions that are formatted with Linux flesystems, even going so far as to refer to logical partitions with Linux filesystems as primary partitions.

> **Greyriver said:**
> , but if it's triggered by ubuntu doing something non-standard to the partitions then I need to understand it better.

It isn't. Partitioning tools in Linux are far more respectful of mbr partition tables, than Windows ones in my experience.

> **Greyriver said:**
> 
If I now use windows to delete F: then the partitions after the swap become scrambled and meaningless.


Unfortunately, that doesn't surprise me.

> **Greyriver said:**
> It looks though XP doesn't understand linux partitions, but surely the partition structure would be identical and only the filesystem would change so this shouldn't happen.

I quite agree but see my comment above. 

> **Greyriver said:**
> Anyway if this always happens wouldn't there be 1000s of people posting about it? I've been searching with no luck.

Not 1000's but this does come up. I'm posting in haste at the moment, but when I get time, I'll post links to some other threads that cover these issues. Your eyebrows will rise, I do assure you!

In the meantime, if you post details of how you would like your partition layout to be, I can give you pointers for how to achieve this with a reliable partitioning tool - Gparted in Ubuntu! :)

---

### Post by oldfred on 2012-09-08
Welcome to the forums.

We have seen where Windows will rewrite a partition table. That may then change sda6 to sda5 or make other changes. But since Ubuntu now uses UUIDs that has become less of an issue.

Windows cannot see Linux partitions, but Linux can see Window NTFS partitions. If deleting a partition in the extended partition I would suggest using gparted from a Linux liveCD or gparted liveCD.

With Windows Vista or 7 it is better to use Windows to shrink the Window NTFS system partition, but to use gparted to create other partitions.

---

### Post by Greyriver on 2012-09-08
Thank you both. If this is 'normal' or at least 'normal for Windows' then I can accept it and use other methods for partitioning. I was beginning to think I must be doing something completely wrong

I'll take a look at Gparted. I'm just so used to using Windows that it seemed easier to do it in there.

I like what I see of Ubuntu and I think I could get used to it. I resisted changing up to Vista and resisted Windows 7 and now 8 sounds even worse. I've got to retire XP sometime.

---

### Post by coffeecat on 2012-09-08
> **Greyriver said:**
>  I've got to retire XP sometime.

Good plan! :)

As promised, some reading for you. 

Windows Disk Management sees Linux logical partitions as primary (telling me I had 6 primary partitions on a single drive at one point).:

[http://ubuntuforums.org/showthread.php?t=1675458](http://ubuntuforums.org/showthread.php?t=1675458)

Windows XP installer corrupting partition table with pre-exisiting Linux logical partitions, by "converting" one logical partition into a primary, but still within the extended partitition:

[http://ubuntuforums.org/showpost.php?p=10468958&postcount=42](http://ubuntuforums.org/showpost.php?p=10468958&postcount=42)

Windows Vista installer going one better than the above by wiping out the Linux partition without notice:

[http://ubuntuforums.org/showpost.php?p=10470071&postcount=44](http://ubuntuforums.org/showpost.php?p=10470071&postcount=44)

---

