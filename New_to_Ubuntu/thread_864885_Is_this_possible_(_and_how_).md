---
title: "Is this possible ( and how )"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by will_s54 on 2008-07-20
Ok have a Samsung 1,000 gb with Ubuntu on about 700gb and XP on the rest.
Also have two other drives and have named them windows and Ubuntu.

Now what I want is when using Ubuntu not to be able to see the XP partition or the Eindows Hard drive. Just want to see the 700G and the Ubuntu hard drive ( this is where I will back up my important data ).
Also it would be good when using XP to not be able to see the Ubuntu partition and the Unbuntu hard drive .

Any ideas how to do any of the above ?

---

### Post by hyper_ch on 2008-07-20
It is advised to use a descriptive topic title; that means use a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;)

---

### Post by Hossie on 2008-07-20
You could only "hide" them, but with appropriate rights it will always be possible to access them. Edit your /etc/fstab (sudo vi /etc/fstab) and remove the lines for the other hard disks. Of course, any administrator can add them again. For windows there is probably no such thing, I think the hard disk will always be there.

---

