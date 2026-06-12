---
title: "I want to see ntfs partition in ubuntu terminal"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by pmn.blazer on 2008-05-30
Hi
I am running dual boot at my laptop which vista(ntfs partition) and ubuntu(ext2).
At ubuntu, I want to run java programs where have got in ntfs partition by terminal. 
How can I run it??

---

### Post by quelx on 2008-05-30
see where the ntfs partition is mounted ```
mount
```

say its **/media/windows**

the terminal command would be ```
java -jar /media/windows/Documents\ and\ Settings/username/Desktop/myjavafile.jar
```

---

### Post by unutbu on 2008-05-30
Please post

```
sudo fdisk -l
cat /etc/fstab
blkid

```

---

### Post by iaculallad on 2008-05-30
> **pmn.blazer said:**
> Hi
I am running dual boot at my laptop which vista(ntfs partition) and ubuntu(ext2).
At ubuntu, I want to run java programs where have got in ntfs partition by terminal. 
How can I run it??

Are you trying to run the .jar file or a class file?

---

