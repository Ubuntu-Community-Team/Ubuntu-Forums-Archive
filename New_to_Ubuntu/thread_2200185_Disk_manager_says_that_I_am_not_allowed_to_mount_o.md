---
title: "Disk manager says that I am not allowed to mount or unmount drives"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by ruwan2 on 2014-01-17
Hi,
I find my USB drive cannot be pasted files. Web search results say Disk Management can change the access attributes. After I install Disk Management, it shows that I am not allowed to mount when I run DM.
The Ubuntu 12.04 has only myself account (automatic login) and a guest account. How can I use DM?

Thanks,

---

### Post by ruwan2 on 2014-01-17
Excuse me, the software is "Disk Management". Its icon is on the bottom third, left column. I did not call it correctly in last post. The error box is also shown in this post. Weirdly, I do not find relevant post on this tool. Please help me if you know it. Thanks, 

Here is the picture link:
[http://tinypic.com/view.php?pic=w84z90&s=5](http://tinypic.com/view.php?pic=w84z90&s=5)

---

### Post by bab1 on 2014-01-17
> **ruwan2 said:**
> Hi,
I find my USB drive cannot be pasted files. Web search results say Disk Management can change the access attributes. After I install Disk Management, it shows that I am not allowed to mount when I run DM.
The Ubuntu 12.04 has only myself account (automatic login) and a guest account. How can I use DM?

Thanks,

My guess is that the USB drive is formatted as vfat or ntfs.  You can't change the permissions with this type of formatting.  The permissions are set at mount time.  Does the drive mount when you plug it in or when you boot up and it is connected?

---

