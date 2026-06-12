---
title: "USB FAT32 memory stick permissions"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by ubername on 2008-09-24
HI 

I have just got an 8Gb memory stick and I am having problems getting it functional across linux and windows platforms. It is formatted as FAT32 and works OK across different windows systems but when I try and use it in linux it gets owned by the first user who plugged it in (since it was last formatted) and gksu nautilus can't change that, nor su chmod 777 <device path>. I don't get error messages in either case, (although in the GUI nautilus environment, when I change the setting for group, user others etc, they instantly revert to the previous settings of no access.)

I have searched the forums, which mostly seem to say that you won't have any problems with FAT32 as it isn't a file system with permissions. However Ubuntu 8.04 seems to see things differrently.


What I would like is, as with my many other working memory sticks, that it is just a portable storage unit that all users can access and read/write (and execute) things in the stick, whether it is a Linux or Windows system. (For the avoidance of doubt, what I mean is that I have many other memory sticks that work just how I want - I can plug them into any old machine, whether Linux or Windows, and they work - users can see / read / delete files). 

I need it to be Windows compliant because it is for my daughter to use at school, and I need it to be Linux because that is what we use by default at home (although I do have windows.)

---

### Post by sneeks on 2008-09-24
what did you use to format and partition the drive with,eg what program?

---

### Post by ubername on 2008-09-24
> **sneeks said:**
> what did you use to format and partition the drive with,eg what program?

Thanks for the reply.

I used 'quick format' under windows vista

---

### Post by The Cog on 2008-09-24
Formatting has nothing to do with it. It gets owned by whoever is logged in when you plug it in. If you change users, I think unplugging it and plugging it in again are all that is needed.

You could make an entry in /etc/fstab for it. Then you can set the option umask=0 to 0 which will allow anyone to write to it.

---

### Post by sneeks on 2008-09-24
this could be your problem,as i have had this before,you need to get a program called gparted(i think they do one for bill,but if not most Linux distro's have it on the live cd).
format and partition with this,you may get an error the first time you do it but keep at it and it will format and partition it in the end.
if it is just for storage make sure it is not made bootable,you can do this by checking the flags in gparted.
ps you do not need to install the distro to do this,it will do it from the live cd.
just make sure you click the correct drive when doing it,it will normallly start with sda,not hda etc.
have done a few vids on this but im not sure if i can give the link as it would be a bit of self advertising .

---

### Post by The Cog on 2008-09-24
Re-formatting won't help. Except that reformatting it then remounts it, and remounting it makes it take on the ownershi of the currently logged-in user. Unplugging and replugging it is faster and won't wipe the contents.

Verify what I'm saying by experiment. Use the mount command to see the mount options, especially the uid value it's mounted with.

---

