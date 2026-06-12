---
title: "Delete hidden files"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by yragrelluf on 2008-08-30
What would happen if I deleted all of the hidden folders in my home folder? Just curious.

---

### Post by Vivaldi Gloria on 2008-08-30
> **yragrelluf said:**
> What would happen if I deleted all of the hidden folders in my home folder? Just curious.

I don't know but you may run into trouble because gnome and a lot of programs keep their settings there.

---

### Post by gmxgeek on 2008-08-30
You probably wouldn't be able to boot properly past the login screen, since those hidden files hold config files for everything having to do with your user account.

---

### Post by louieb on 2008-08-30
**:confused:Weird** things. Those hidden folders and files contain all your personalized settings.

---

### Post by yragrelluf on 2008-08-30
So what if my home folder is on its own partition, and I want to do a clean install, but keep my pics and music intact, but start fresh with all the default settings? Would I want to delete the files, or would the installer overwrite the existing ones?

---

### Post by gmxgeek on 2008-08-30
> **yragrelluf said:**
> So what if my home folder is on its own partition, and I want to do a clean install, but keep my pics and music intact, but start fresh with all the default settings? Would I want to delete the files, or would the installer overwrite the existing ones?

Back up your pics etc to an external source then format and reinstall

---

### Post by Vivaldi Gloria on 2008-08-30
> **yragrelluf said:**
> So what if my home folder is on its own partition, and I want to do a clean install, but keep my pics and music intact, but start fresh with all the default settings? Would I want to delete the files, or would the installer overwrite the existing ones?

That's why I have a partition where I keep my files but I don't mount it as /home. /home is on the root partition. I mount the partition with my files to /mnt/disk and put a symlink to my home. So I can do a fresh install deleting /home and keep my files at the same time.

So use your current /home partition as a partition for keeping files. And don't choose it as /home when reinstalling. Then you will have a fresh home.

---

### Post by gmxgeek on 2008-08-30
> **Vivaldi Gloria said:**
> That's why I have a partition where I keep my files but I don't mount it as /home. /home is on the root partition. I mount the partition with my files to /mnt/disk and put a symlink to my home. So I can do a fresh install deleting /home and keep my files at the same time.

So use your current /home partition as a partition for keeping files. And don't choose it as /home when reinstalling. Then you will have a fresh home.

quite clever. I will have to try that next time i do a reinstall.

---

