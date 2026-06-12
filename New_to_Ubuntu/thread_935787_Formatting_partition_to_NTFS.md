---
title: "Formatting partition to NTFS"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by neil6412 on 2008-10-02
Hi,

I am having trouble converting a partition to NTFS so that I can re-load vista.  Using GParted I created the partition but when I want to format as NTFS using GParted, the NTFS option is greyed out.

Thanks

---

### Post by jamesrl on 2008-10-02
[I]I'm pretty sure gparted can't create NTFS partitions (it being proprietary and a file system basically only useful for windows users, though it can resize them ... as linux users may need more space for their partitions).  
[/I] **See edit below**
So just leave some space unused by the linux partitions, and then when you install windows  it can do the ntfs partitioning to the unused space (making sure the sizes of the things windows reformats is correct so you don't overwrite the ubuntu partition).

Actually looking at :
[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)
I find that the latest versions of gparted should support creating ntfs partitions.  Are you running it as root from a recent live cd (so the partition isn't mounted)?  You also may have to delete the partition and then create a new ntfs partition rather than reformat a partition.

---

### Post by iaculallad on 2008-10-02
Surely that partition could be active so the option of formatting it NTFS is greyed out in GParted. Try to boot using your Desktop LiveCD and format it to your desired NTFS filesystem.

NOTE: GParted supports NTFS formatting.

---

### Post by vanadium on 2008-10-02
```

GParted supports NTFS formatting
```
It does not, unless you install ntfsprogs, which includes a linux utility to create an ntfs file system (and gparted will use that for you if available).

---

### Post by iaculallad on 2008-10-02
> **vanadium said:**
> ```

GParted supports NTFS formatting
```
It does not, unless you install ntfsprogs, which includes a linux utility to create an ntfs file system (and gparted will use that for you if available).

Forgot to mention that, you need the prerequisite application, ntfsprogs, to be able to format a drive to NTFS using GParted.
Thanks for pointing it out.

---

### Post by JDorfler on 2008-10-02
> **iaculallad said:**
> Forgot to mention that, you need the prerequisite application, ntfsprogs, to be able to format a drive to NTFS using GParted.
Thanks for pointing it out.

And all this time I was using the LiveCD to do all my partitioning in GParted for NTFS, and, well, everything else.  Ntfsprogs sounds like a job for ....dun da da dun....Synaptic.... and we're done.

---

### Post by bumanie on 2008-10-02
I have had the same issue with gparted from ubuntu, but ntfs formatting works fine if you use the stand-alone gparted live cd. In most cases, I prefer the gparted live cd, because it is a dedicated partitioning tool.

---

### Post by neil6412 on 2008-10-04
> **bumanie said:**
> I have had the same issue with gparted from ubuntu, but ntfs formatting works fine if you use the stand-alone gparted live cd. In most cases, I prefer the gparted live cd, because it is a dedicated partitioning tool.

Thanks! that worked, I have now converted a partition into NTFS.  

However when I tried to install Vista on the new NTFS partition, Windows installer gave me an error again saying that the requirements for a Windows drive were not met by my new NTFS partition. Do you know of anything else that I have to do in order for Windows to be happy with it?

Secondly, once I have them both installed, can someone tell (or point me to an easy to follow thread) how to create a dual booting start up?  

Thanks
Neil

---

