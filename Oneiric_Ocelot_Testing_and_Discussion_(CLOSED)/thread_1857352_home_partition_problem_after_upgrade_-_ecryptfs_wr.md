---
title: "home partition problem after upgrade - ecryptfs_writepage: Error encrypting page"
date: 2011-10-10
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by nicolasdiogo on 2011-10-10
hello,

i am getting loads of entries on my logs with 
> 
Oct  9 21:02:07 mypc kernel: [ 2646.567534] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
Oct  9 21:02:07 mypc kernel: [ 2646.567538] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000024])
Oct  9 21:02:07 mypc kernel: [ 2646.567579] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
Oct  9 21:02:07 mypc kernel: [ 2646.567581] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000024])
Oct  9 21:02:37 mypc kernel: [ 2676.561009] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
Oct  9 21:02:37 mypc kernel: [ 2676.561013] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000025])
Oct  9 21:02:37 mypc kernel: [ 2676.561054] ecryptfs_encrypt_page: Error attempting to write lower page; rc = [-5]
Oct  9 21:02:37 mypc kernel: [ 2676.561056] ecryptfs_writepage: Error encrypting page (upper index [0x0000000000000025])

why should be the correct action to solve this?

thanks guys,

---

### Post by mdacova on 2011-10-13
I getting these also 

anyone have a idea, I started noticing them after the upgrade to 11.10 and gnome 3.2
:(

---

### Post by tekstr1der on 2011-10-13
See [Bug #870326: ecryptfs_writepage: Error]("https://bugs.launchpad.net/ecryptfs/+bug/870326?comments=all")

I can confirm the same. I recently experienced a flood of thousands of such ecryptfs dmesg errors, so many that I was alerted to the issue by errors regarding zero disk space remaining.

After reading up on Bug #372014, I resolved (hopefully) the issue by deleting all ecryptfs-encrypted files of zero length:

```
find $HOME/.Private/ -size 0c -exec ls '{}' \; | wc -l
```

will output the number of such files. I then proceeded to remove the listed files.

EDIT: I am still running natty 11.04, fully updated. I do use the oneiric kernel, however.

---

### Post by mdacova on 2011-10-13
```
find $HOME/.Private/ -size 0c -exec ls '{}' \; | wc -l
```


I ran the above and got 4, but no list of the files

---

