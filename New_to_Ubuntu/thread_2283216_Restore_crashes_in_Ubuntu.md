---
title: "Restore crashes in Ubuntu"
date: 2015-06-20
forum: New to Ubuntu
---

### Post by anbu-s on 2015-06-20
I was running gnome 14.04.02 and have a full backup on an external drive. I installed ubuntu 15.04 from scratch and when i try to restore from the backup, it starts restoring some chrome cache files and crashes and logs me out of the system. After multiple tries i get the same result. Some of my settings such as evolution email accounts are already back with the restore.Bu

But how do i restore the system fully from the backup?

---

### Post by dino99 on 2015-06-20
[https://help.ubuntu.com/community/DuplicityBackupHowto](https://help.ubuntu.com/community/DuplicityBackupHowto)

you can find a bunch of ubuntu wikis & howtos; hit the links below for an overview

---

### Post by RobGoss on 2015-06-21
If I'm understanding you correctly you want to restore your system back to [COLOR=#000000]**14.04.02**  right?

If this is correct just wipe the drive and reinstall the [/COLOR][COLOR=#000000]14.04.02,  distribution and after it's complete try running the restore disk or USB, you have and it should restore your system back to the way it was... [/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by sandyd on 2015-06-21
> **anbu-s said:**
> I was running gnome 14.04.02 and have a full backup on an external drive. I installed ubuntu 15.04 from scratch and when i try to restore from the backup, it starts restoring some chrome cache files and crashes and logs me out of the system. After multiple tries i get the same result. Some of my settings such as evolution email accounts are already back with the restore.Bu

But how do i restore the system fully from the backup?

I've generally found that a full restore is not possible on a running system. Deja-Dup seems to replace files that the system is using (i.e libc and other libs), and it causes the system to crash. Since I found the issue, I moved to creating images of my disk instead.

---

### Post by Yordan_Itsov on 2016-02-24
How to restore without a running system, live CD? Also how to restore just my files- documents, downloads and so on?

---

