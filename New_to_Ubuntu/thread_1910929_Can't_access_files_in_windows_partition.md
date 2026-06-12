---
title: "Can't access files in windows partition"
date: 2012-01-18
forum: New to Ubuntu
---

### Post by madeel2 on 2012-01-18
I have installed lubuntu along side of windows XP. I thought I can access my windows partition and data saved there. However, in the windows partition, the data saved is not visible. It is showing my document, download folder etc as empty folder. 

I would like to know how can I access my saved file in the windows partition from lubuntu session. Thanks.

---

### Post by Rodney9 on 2012-01-18
You need - 'NTFS-3G' it is available in Synaptic

> NTFS-3G uses FUSE (Filesystem in Userspace) to provide support for the NTFS
filesystem used by Microsoft Windows. It can:

 * create, remove, rename, or move files, directories, hard links, and streams;
 * read and write files, including streams, sparse files, and transparently
   compressed files;
 * handle special files like symbolic links, devices, and FIFOs;
 * provide standard management of file ownership and permissions, including
   POSIX ACLs.


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by Mark Phelps on 2012-01-18
Are just those folders showing as empty?  Try looking into Program Files -- any apps you installed will have folders and files in there.

---

### Post by madeel2 on 2012-01-21
> **Rodney9 said:**
> You need - 'NTFS-3G' it is available in Synaptic



For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

It is installed but still can't see the saved files (like pdf, doc etc). Lubuntu showing the windows partition as local disk.  I am the administrator for windows too. So in the 'document and setting folder' has the administrator folder with 'my document' folder. I can't see any contents in 'my docuement' folder.

---

### Post by sandyd on 2012-01-21
> **madeel2 said:**
> It is installed but still can't see the saved files (like pdf, doc etc). Lubuntu showing the windows partition as local disk.  I am the administrator for windows too. So in the 'document and setting folder' has the administrator folder with 'my document' folder. I can't see any contents in 'my docuement' folder.

Post output of
```

mount -l
```

---

### Post by varunendra on 2012-01-21
Sorry if it sounds utterly stupid or insulting, but are you sure your concerned account is "Administrator" in XP? When you run command prompt (Start > Run > cmd), do you see "Administrator" at the prompt?

Because by default XP keeps that account hidden, and instead provides the first 'user-account' to the user as the account with "administrative privileges". So I was wondering if you might be confusing "Administrative" account with "Administrator's" account.

What other folders do you see in "Documents and Settings"? Have you checked them for the files you are looking for?

---

