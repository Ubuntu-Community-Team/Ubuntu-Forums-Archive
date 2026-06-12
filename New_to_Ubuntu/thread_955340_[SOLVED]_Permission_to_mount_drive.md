---
title: "[SOLVED] Permission to mount drive"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by pluekiller on 2008-10-22
I can't access my windows ntfs drive through ubuntu.. it says i do not have the permission... what should i do?

---

### Post by wardrich on 2008-10-22
Are you able to see it?  Is the permission error happening when you're trying to modify files on, or move files to that drive?

Are you trying to mount the drive?  I can't remember if ubuntu automatically mounts ntfs drives... If you are trying to mount it, did you remember to sudo/su?

---

### Post by taseedorf on 2008-10-22
okay...follow this...

go into synaptic package manager and make sure ntfs-3g is installed....

than in terminal type sudo gedit /etc/fstab

in there, add a line like this

/dev/sda1 /media/windows ntfs-3g defaults 0 0

replace "/dev/sda1" with ur partition info... to find thid type sudo fdisk -l in a terminal and it will tell u.

MAKE SURE to create the directory "windows" in the folder "media" on your linux filesystem.

i think this command would do it

sudo mkdir /media/windows

reboot and everything should work...

---

### Post by OldGrey on 2008-10-22
Does the dialogue offer an "unlock" option. If so click on that put in your password and you will then get access. In my experience having done it once the system remembers next time.

---

### Post by pluekiller on 2008-10-22
taseedorf's solution worked... thanks :)

---

