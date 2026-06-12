---
title: "tar options for backup"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by imjscn on 2008-07-04
I have a 2GB folder in /home directory, I want to split archive it, 650MB for each piece is fine.  After some reading, I got some idea like this:

To split archive:
split --bytes=650m myarchive.tar

To join:
cat   > myarchive.tar

Could anybody give me a complete code? Thanks!

---

### Post by imjscn on 2008-07-04
?? please

---

### Post by ghostdog74 on 2008-07-04
check your tar man page. there's an option to create multi volume. you don't have to use split

---

### Post by imjscn on 2008-07-04
I just finished reading man page, tar is not the right operation for spliting, split can't do compressing. 
I want to compress and split, jeepers! Any other method?

---

### Post by ghostdog74 on 2008-07-04
> **imjscn said:**
> I just finished reading man page, tar is not the right operation for spliting, split can't do compressing. 
I want to compress and split, jeepers! Any other method?

have you really read thoroughly? i mentioned you can create multi-volume using tar. No need for split.

---

