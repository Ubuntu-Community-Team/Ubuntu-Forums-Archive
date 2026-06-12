---
title: "NTFS problem"
date: 2011-10-19
forum: New to Ubuntu
---

### Post by niladrithedon on 2011-10-19
I am a complete novice so frnds help me with this- I have set up a dual boot system. ubuntu opens up my NTFS volumes in read only mode. How to solve it without formatting the hard drive

---

### Post by spcwingo on 2011-10-19
Can you post the output of this command ran from a terminal:

```
sudo fdisk -l
```

I need that to identify your Win partition.

If all looks well, we can automount it via fstab (a boot-time mount list, kind of).

---

### Post by coffeecat on 2011-10-19
Welcome to the forum.

> **niladrithedon said:**
>  ubuntu opens up my NTFS volumes in read only mode. 

That is most unusual. If you are automounting the NTFS partition from the Nautilus file browser, it should be mounted read-write. To be mounted read-only may mean that there is a filesystem error that needs repairing. Linux will mount Microsoft filesystems read-only (or not at all) if it detects an error. Even if the partition in question can be used from Windows without problem, I suggest you do a filesystem check and repair in Windows. You can use chksdk from a command prompt or there is a way from the GUI, but I can't remember the details offhand.

---

### Post by askord on 2011-10-19
i get this same trouble in startup,maybe 1 apps not supported AMD integrated  . . . help me

---

### Post by ducky12432 on 2011-10-23
> **niladrithedon said:**
> I am a complete novice so frnds help me with this- I have set up a dual boot system. ubuntu opens up my NTFS volumes in read only mode. How to solve it without formatting the hard drive

i already posted this in a different thread but I will post it here incase one gets lost.

install ntfs-3g and you will be able to read/write to ntfs.

---

### Post by Mark Phelps on 2011-10-23
> **ducky12432 said:**
> install ntfs-3g and you will be able to read/write to ntfs.

NOT if the filesystem is corrupted or marked as "dirty".

You STILL need to follow the previous advice and run CHDSK in Windows against the partition.

---

### Post by coffeecat on 2011-10-24
> **ducky12432 said:**
> i already posted this in a different thread but I will post it here incase one gets lost.

install ntfs-3g and you will be able to read/write to ntfs.

> **Mark Phelps said:**
> NOT if the filesystem is corrupted or marked as "dirty".

You STILL need to follow the previous advice and run CHDSK in Windows against the partition.

+1 to what Mark Phelps says. However, I've now seen a few threads where the package ntfs-3g has gone missing in Oneiric/11.10, and this seems to be the cause of NTFS filesystems becoming read-only. (I can only assume that the system is falling back to the kernel read-only ntfs driver module in the absence of ntfs-3g). Quite why people are losing ntfs-3g in Oneiric, I'm not sure. It's possible that they are mistakenly installing the ntfsprogs package in Oneiric which is no longer needed since the Oneiric version of ntfs-3g includes the utilities formerly provided by ntfsprogs. If you install ntfsprogs in Oneiric, the package manager removes ntfs-3g. So, if anyone needs to install ntfs-3g, it's because they removed it - even if unknowingly.

---

### Post by frank_claessen on 2012-01-16
> **coffeecat said:**
> +1 to what Mark Phelps says. However, I've now seen a few threads where the package ntfs-3g has gone missing in Oneiric/11.10, and this seems to be the cause of NTFS filesystems becoming read-only. (I can only assume that the system is falling back to the kernel read-only ntfs driver module in the absence of ntfs-3g). Quite why people are losing ntfs-3g in Oneiric, I'm not sure. It's possible that they are mistakenly installing the ntfsprogs package in Oneiric which is no longer needed since the Oneiric version of ntfs-3g includes the utilities formerly provided by ntfsprogs. If you install ntfsprogs in Oneiric, the package manager removes ntfs-3g. So, if anyone needs to install ntfs-3g, it's because they removed it - even if unknowingly.

I am having trouble checking my ntfs disk for errors. It would work OK in previous versions but now I get a message saying that fsck.ntfs-3g cannot be found. Meanwhile I understood that this is a bug.

So, I downloaded the package from debian squeeze, solved a dependency problem and voila - i am back in business.

Hope this helps other too

Cheers Frank

Success is a journey, not a destination

---

