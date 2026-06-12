---
title: "[SOLVED] Cannot share/change permissions on a 2nd int hdd"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by warped0ne on 2008-09-02
My computer was originally a dual boot between WinXP and Ubunutu 8.04.  I have since ditched Windows altogether and formatted the drive it was on to ext3 using GParted.  This means my Ubuntu loaded hard drive is /dev/sdb and _my blank hard drive is /dev/sda_ (both formatted to ext3).  I would like to save movies, music, pictures, etc to the empty drive, but I'm told I don't have the permission to do so:

"Error opening file '/media/disk/xxx.xxx.avi': Permission denied"

I have also tried to share it with my laptop, which has a tiny hdd in it, however I get the following message whenever I try to share it:

"'net usershare' returned error 255: net usershare add: cannot share path /media/disk as we are restricted to only sharing directories we own.
Ask the administrator to add the line "usershare owner only = False" to the [global] section of the smb.conf to allow this."

I have Samba enabled and I can share folders (music, pictures, video) with my laptop with no problem.  I have tried to **sudo chmod -R 755 /media/disk** to change the permissions, but that doesn't work.  I have tried to create a new directory using '**mkdir**', I get the same error message as above.

I was looking at this post, [http://ubuntuforums.org/showthread.php?t=826891&highlight=changing+permissions+disks](http://ubuntuforums.org/showthread.php?t=826891&highlight=changing+permissions+disks), and it recommended a lot of things, but it was for a computer with a NTFS file system.  I have already ran the following commands

[B]sudo fdisk -l 
gedit /etc/fstab
sudo mount [/B]

and posted their results in the attached .txt file.  Please help.

Thank you

---

### Post by warped0ne on 2008-09-02
Sorry, just tried one last command I had forgotten.  Stumbled upon this post [http://ubuntuforums.org/showthread.php?p=5716901#post5716901](http://ubuntuforums.org/showthread.php?p=5716901#post5716901) and it reminded me of the chown command.

sudo chown -R username /media/disk

This resolved my issue.

---

### Post by falcon61102 on 2008-09-03
Nice.  If you go up Thread Tools you can mark this thread SOLVED.

---

