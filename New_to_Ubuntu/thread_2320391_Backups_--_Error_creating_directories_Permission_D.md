---
title: "Backups -- Error creating directories: Permission Denied"
date: 2016-04-13
forum: New to Ubuntu
---

### Post by kat7 on 2016-04-13
I formatted an external SSD drive today with the intention of using it for backups.
I'm using 'Backups' but it reports error,  "Error creating Directories:Permission denied."
I'm logged in as Administrator in the ubuntu desktop.

Any help would be greatly appreciated.

Kat

---

### Post by kat7 on 2016-04-13
I can backup to my laptop's hard disk no problem,but not to the external drive.[I]
I can also use the filemanager to view the external drive, and make directories on it.

Kat
[/I]

---

### Post by kat7 on 2016-04-13
'Properties' of the external drive are owner:root, group:root.

I guess I have to find some way of changing the properties of owner and  group in the terminal before backups will work.
I'm not really sure how to do this.

Kat

---

### Post by yancek on 2016-04-13
> I guess I have to find some way of changing the properties of owner and  group in the terminal before backups will work.

Yes, you do.  A basic principle in Linux is that almost anything outside the /home/user directory is owned by root so you need sudo to prefix any command. 

Use the chown command to change the owner.  You would do this by first creating a directory to use as a mount point.  The standard place to do this is in the /mnt directory but you can do it elsewhere.  As an example:  sudo mkdir /mnt/external

After that you would have to manually mount it or put and entry in the /etc/fstab file to have it mounted on boot if it will be permanently attached and that is what you want.   
To manually mount using the example above with an ext4 filesystem:   sudo mount -t ext4 /dev/sdb1 /mnt/external

The above would be if the drive/partition you want to mount is actually sdb1.  You haven't posted that info so this is just an example.

---

### Post by kat7 on 2016-04-13
I think I jumped too quickly.


1. I tried :-
sudo chown kat /dev/sdb1

2.then, because I read I shouldn't do 1.:-
sudo chown root /dev/sdb1

have I ruined my file system?

Kat

---

### Post by SeijiSensei on 2016-04-13
No. /dev/sdb1 refers to the partition.  It doesn't have an ownership, the location in the directory tree where it is mounted (the "mount point") does.

If you plug an external drive into Ubuntu, it will be mounted at /media/username/some_drive_identifier, and you should have write privileges to it.  

There isn't an "Administrator" login in Ubuntu unless you created an account with that name yourself.  The administrative user is "root".  When you run a command with "sudo" it runs with root's privileges.  All other activities occur as the user who has logged in.

---

### Post by jay_bowles2 on 2016-04-14
How are you trying to make your backup? If using the command line just use sudo. If its a gui app then you may need to use raised privileges to do this (hence the error) in which case launch in the terminal with gksu (you may need to install that).

---

