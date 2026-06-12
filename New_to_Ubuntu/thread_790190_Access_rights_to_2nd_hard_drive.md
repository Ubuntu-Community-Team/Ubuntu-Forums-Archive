---
title: "Access rights to 2nd hard drive"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by kg4tah on 2008-05-11
I have two hard drives in my pc, both maxtor.  I use my second hard drive to backup the contents from my main drive.  It was initially formatted in fat32 and I could read and write to it with no problem however I wanted to format it to the ext3 format so I used gpart.  I deleated the fat32 partition and did a reformat in ext3.  Now I do not have write access to the drive unless I go into a terminal and do the gksudo natilus command.  What steps do I need to preform in order to give it write rights like I had before I did the reformat?

---

### Post by ajmorris on 2008-05-11
hi there,
edit /etc/fstab as root, and in the options section for that hard drive, add: users,user
then a normal user can mount it, and can also read and write to it.

AJ

---

### Post by volkswagner on 2008-05-11
This should help.

[http://www.psychocats.net/ubuntu/mountlinux]("http://www.psychocats.net/ubuntu/mountlinux")

If you already have it working, and entry is in fstab, you may just need the chown command.  edit accordingly for your user name and mount point.

---

### Post by kg4tah on 2008-05-11
Thanks, that looks simple enough.  I will give it a try tonight when I get off work and ill post my results.

---

