---
title: "clone Ubuntu installation and incremental updates"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by dabd on 2008-11-15
Hi,

I would like to clone (1:1 image and bootable, of course) my ubuntu installation and be able to incrementally update the cloned image.

I've searched the forums and there are several options for cloning:clonezilla, rsync, etc.

What is the best tool for the job?

Thanks.

---

### Post by cdtech on 2008-11-15
If you have the space, I would use the "dd" command to copy the entire drive contents to the backup drive and use rsync to maintain the backup afterwards.

Just my thoughts.....

---

### Post by Duck2006 on 2008-11-15
The dd commands or part image will do what you want.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by dabd on 2008-11-15
> **cdtech said:**
> If you have the space, I would use the "dd" command to copy the entire drive contents to the backup drive and use rsync to maintain the backup afterwards.

Just my thoughts.....

Will dd create a bootable image?

---

### Post by cdtech on 2008-11-15
Yes

---

### Post by dabd on 2008-11-15
> **Duck2006 said:**
> The dd commands or part image will do what you want.

[http://www.brunolinux.com/02-The_Terminal/The_dd_command.html](http://www.brunolinux.com/02-The_Terminal/The_dd_command.html)
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

If I create an exact clone with dd, the clone will have the same UUID and I won't be able to automount it, isn't it?

Is it possible to incrementally update the image created with partimage, say with rsync?

---

### Post by Duck2006 on 2008-11-15
Yes but be careful.

> I urge you to be very careful with the DD command . . . switching if= with of= can have catastrophic results

---

### Post by Duck2006 on 2008-11-15
> Is it possible to incrementally update the image created with partimage, say with rsync?

yes.

---

### Post by dabd on 2008-11-15
> **Duck2006 said:**
> yes.

Well in that case partimage seems to be safer than dd.
What about clonezilla?

---

### Post by Duck2006 on 2008-11-15
> **dabd said:**
> Well in that case partimage seems to be safer than dd.
What about clonezilla?

I have never used that, This may help with that.

[http://ubuntuforums.org/showthread.php?t=421375](http://ubuntuforums.org/showthread.php?t=421375)

---

