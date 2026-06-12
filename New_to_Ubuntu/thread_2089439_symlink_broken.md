---
title: "symlink broken"
date: 2012-11-29
forum: New to Ubuntu
---

### Post by qurrat09 on 2012-11-29
Hi,
I am a beginner to Ubuntu. I have placed my data in a shared file server but now I am unable to access it. The error message is link (broken) (inode/symlink) and I can no more access my data from the folder. I do not want to delete it and make a new link because I am afraid of loosing my data.
TEll me how can I fix this error?

---

### Post by sandyd on 2012-11-29
> **qurrat09 said:**
> Hi,
I am a beginner to Ubuntu. I have placed my data in a shared file server but now I am unable to access it. The error message is link (broken) (inode/symlink) and I can no more access my data from the folder. I do not want to delete it and make a new link because I am afraid of loosing my data.
TEll me how can I fix this error?

If you delete the link that is broken (should show up as red, or blinkinb on ssh), it will not cause you to lose data.

Only the link that is.

There is an easy way of verifying that it is indeed broken, and not going to affect your data if you delete it.

Run\```

ls *filename*
```
where filename can be a folder or a file

if it doesn't exist, then deleting it will not delete any data, other than the link.

Also, if you run rm on the link, it will only delete the link.

---

