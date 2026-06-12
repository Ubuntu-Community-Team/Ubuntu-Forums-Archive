---
title: "why i cant read / write file from ntfs drives and flash memory in ubuntu 11.11 ?"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by sistyN on 2011-11-09
why i cant read / write file from ntfs drives and flash memory in ubuntu 11.11 ? 
i changed file access to read/write but it didnt work !

---

### Post by Rodney9 on 2011-11-10
Make sure you have ntfs-3g installed

NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.

---

### Post by Mark Phelps on 2011-11-10
When Ubuntu tries to mount an NTFS partition read/write and that fails, it often falls back to mounting it read-only -- to prevent damage to the filesystem.

If these are External drives, that could be because they were not "safely removed", thus preventing Ubuntu from mounting them read/write.

If that is the case, connect them to a Windows PC and run CHKDSK on the drives.  That should make them mountable in Ubuntu again.

---

### Post by sistyN on 2011-11-10
> **Rodney9 said:**
> Make sure you have ntfs-3g installed

NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.


i already had ntfsprogs !
the os dont give me permission to change file access , i didnt have this problem in previous ubuntus ! 
now i can read files but i cant write them .

---

### Post by sadaruwan12 on 2011-11-10
What I've sees is that when a file is created in NTFS system with an admin account holder mostly that file gets locked down in a Linux environment so mostly what I've done is set the permission part for that NTFS system through terminal and then the file.

---

### Post by Paddy Landau on 2011-11-10
> **Rodney9 said:**
> Make sure you have ntfs-3g installed
> **Mark Phelps said:**
> If that is the case, connect them to a Windows PC and run CHKDSK on the drives.  That should make them mountable in Ubuntu again.
Have you tried these two suggestions yet?

---

### Post by docbop on 2011-11-10
Google is your friend.  There are lots of articles on google about this happening for various reasons and various solutions.  Here's just one.

[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by coffeecat on 2011-11-10
> **sistyN said:**
> i already had ntfsprogs !

That is your problem! Do not install ntfsprogs in 11.10. It removes ntfs-3g, which you do need. The package ntfs-3g provides all the functionality previously supplied by ntfsprogs. Remove ntfsprogs and install ntfs-3g.

---

### Post by Mark Phelps on 2011-11-10
> **coffeecat said:**
> That is your problem! Do not install ntfsprogs in 11.10. It removes ntfs-3g, which you do need.

Good catch!  I should have remembered this because, when I installed 11.10 recently and then started installing my "standard" list of packages, when I went to install ntfsprogs, there was an error message about having to remove ntfs-3g.

I have to remember this better in the future.

---

### Post by sistyN on 2011-11-10
> **sadaruwan12 said:**
> What I've sees is that when a file is created in NTFS system with an admin account holder mostly that file gets locked down in a Linux environment so mostly what I've done is set the permission part for that NTFS system through terminal and then the file.

How can i change permission in terminal , I changed it in gui form but nothing happend ? now , I cant write to ntfs drives but i can read , when i try write , it show me read only !

---

### Post by sistyN on 2011-11-10
> **coffeecat said:**
> That is your problem! Do not install ntfsprogs in 11.10. It removes ntfs-3g, which you do need. The package ntfs-3g provides all the functionality previously supplied by ntfsprogs. Remove ntfsprogs and install ntfs-3g.

why ntfs-3g ? i think they are same !

---

### Post by Rodney9 on 2011-11-10
> **sistyN said:**
> why ntfs-3g ? i think they are same !

This package NTFS-3G also contains the tools previously available in the ntfsprogs package and is updated plus improved.

---

### Post by coffeecat on 2011-11-10
> **sistyN said:**
> why ntfs-3g ? i think they are same !

Because ntfs-3g is the read-write driver which you removed when you installed ntfsprogs. Without ntfs-3g the system falls back to the read-only kernel ntfs module.

So, **please** now install the ntfs-3g package.

---

### Post by sistyN on 2011-11-10
its worked , ty for helping me !

---

### Post by Paddy Landau on 2011-11-11
> **sistyN said:**
> its worked , ty for helping me !
Excellent! Please [URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]mark this thread as solved.
[/URL]

---

