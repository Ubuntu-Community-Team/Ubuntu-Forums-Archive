---
title: "Changing Permissions on a Share Folder"
date: 2012-08-24
forum: New to Ubuntu
---

### Post by kc5hwb on 2012-08-24
Hi All,

I used to have a thread in this forum bookmarked for creating/sharing a folder on a network for ALL USER access.  I vaguely recall that I could create a folder, and then run a CHOWN and CHMOD command to make it accessible by everyone.  But I can't find that article now, it was a couple years old.

My problem today is that I have a share folder on my network at home, it is actually a NAS drive that I have shared to everyone, but somehow the permissions got change.  When I go to Properties on that share (cd /media/share1) it shows that ROOT is the group owner, and it wont' let me change this.  I've tried to run a CHMOD 777 on the dir and also a CHOWN to my own username and group, but it keeps giving me Permission Denied.  Obviously this is because the group is set to ROOT ownership on this share, but I don't know how that got there.

I need help with changing the ownership of this share back to everyone so that when I drag files over to this share from my Ubuntu box, I can access them with Windows.  I already have SAMBA up and running, and its been in place for a long time.  Like I said, this used to work fine, but somehow I changed it.

Thanks for any help.

---

### Post by Hadaka on 2012-08-24
Hi, perhaps this will help.....
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by cogier on 2012-08-24
If you use **sudo** before your **chown** and other commands that will give you the root access you need.

---

### Post by kc5hwb on 2012-08-24
> **cogier said:**
> If you use **sudo** before your **chown** and other commands that will give you the root access you need.

Tried that, still getting "Permission Denied"

---

### Post by Miljet on 2012-08-24
You mentioned sharing files with Windows, so is the NAS partitioned as NTFS? If so, NTFS doesn't support Linux permissions. You would control sharing by changing the permissions of the mount point and setting options in the /etc/fstab file.

---

### Post by kc5hwb on 2012-08-26
> **Miljet said:**
> You mentioned sharing files with Windows, so is the NAS partitioned as NTFS? If so, NTFS doesn't support Linux permissions. You would control sharing by changing the permissions of the mount point and setting options in the /etc/fstab file.

No, the NAS is ext3 partitioned.

---

### Post by MrGiedi on 2012-08-27
Maybe u should try this [http://superuser.com/questions/19318/how-can-i-give-write-access-of-a-folder-to-all-users-in-linux](http://superuser.com/questions/19318/how-can-i-give-write-access-of-a-folder-to-all-users-in-linux).  Top voted answer seems legit to me. :P Hope so.

---

