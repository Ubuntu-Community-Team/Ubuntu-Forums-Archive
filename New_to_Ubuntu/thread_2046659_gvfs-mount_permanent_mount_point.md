---
title: "gvfs-mount permanent mount point"
date: 2012-08-23
forum: New to Ubuntu
---

### Post by wltiii on 2012-08-23
I am running 12.04 (Hybryde distro), that I just installed yesterday. I have a NAS (network drive or network storage device). I wish to mount the shares so that I can peruse them at will from any app.

I followed a lot of discussions and felt that using gvfs-mount should work. Sure enough, I can see the shares mounted in Home Folder (I am currently using the Unity Desktop). So far so good. However, when I look into ~/.gvfs, I see nothing. I expected to see something like "share on server" as others have stated. Am I missing something, not understanding correctly?

BTW - I am trying to mount to shares, again they both appear in Home Folder under Network, but they both point to the same server. Here are the commands I used:

gvfs-mount smb://192.168.1.199/wltiii
gvfs-mount smb://192.168.1.199/public

If I cannot see names in ~/.gvfs, I am not sure how to create the symbolic link. My intention is to mount these devices upon start up.

Thanks!

---

### Post by Lisiano on 2012-08-23
If you need them to automount at boot, one way would be to use fstab.
Open a terminal (Ctrl+Alt+T) then type in the following
```
gksudo gedit /etc/fstab
```
Then add the following 2 lines to the end of the file.
```
//192.168.1.199/wltiii          /media/wltiii          cifs            rw,workgroup=WORKGROUP,auto,user=USER,password=PASSWORD,iocharset=utf8      0     0
//192.168.1.199/public          /media/public          cifs            rw,workgroup=WORKGROUP,auto,user=USER,password=PASSWORD,iocharset=utf8      0     0
```
You can replace /media/wltiii and /media/public if you want to mount those somewhere else. Also please replace the USER, PASSWORD and WORKGROUP values. If you don't need to login, you can remove the user and password options then.

EDIT: You might have to install [cifs-utils](apt://cifs-utils) first. Just click the name to install it.

---

### Post by Morbius1 on 2012-08-23
> However, when I look into ~/.gvfs, I see nothing.It sounds like you are missing one or more packages:
```
sudo apt-get install gvfs-backends
sudo apt-get install gvfs-fuse
sudo apt-get install fuse
```And / Or you are not a memeber of the fuse group:
```
sudo gpasswd -a your-user-name fuse
```Then logout and login again to make the group change.

If you can now see the .gvfs/whatever mounts and you want to have these automount I would suggest Gigolo: [http://ubuntuforums.org/showpost.php?p=9941016&postcount=3](http://ubuntuforums.org/showpost.php?p=9941016&postcount=3)

And if you want an easier time getting to the mountpoints you can create a bookmark to the .gvfs folder:
```
nautilus $HOME/.gvfs
```Then when nautilus opens up select Bookmarks > Add bookmark. From then on it will show up in things like nautilus and Save As dialog boxes.

---

### Post by wltiii on 2012-08-23
Unfortunately, this did not work. I did see folders in /media named wltiii and public, however they were empty.

I am going to examine the post by morbius1 next. That will have to wait a few hours, though.

---

### Post by wltiii on 2012-08-24
morbius1 -

all the packages were already installed and up-to-date. i added myself to the fuse group. restarted. ran command gvfs-mount **smb://192.168.1.199/wltiii**. then i looked into .gvfs folder (**ls -a**). it remains empty.

---

### Post by Morbius1 on 2012-08-25
I'm beginning to think that the gvfs-fuse daemon isn't running at all.

Run the following commands to start it:
Unmount the .gvfs mount point:
```
 sudo umount ~/.gvfs
```
Then start the daemon:
```
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```If that works you may have to add it to your startup applications unless I can figure out the root case of why it's not starting.

---

### Post by wltiii on 2012-08-28
Morbius1,

> I'm beginning to think that the gvfs-fuse daemon isn't running at all.

This worked. I have not re-booted to see if the daemon is running upon startup. If not, I should be able to add that to a startup script. I presume I will need to add the gvfs-mount to a startup script, too. Just wondering... Would this be in my .bashrc? .bash_profile? Or?

---

### Post by Morbius1 on 2012-08-29
Create a little script at say ... $HOME/gvfs-mount with this content:
```
#! /bin/bash
fusermount -zu ~/.gvfs
/usr/lib/gvfs/gvfs-fuse-daemon ~/.gvfs
```Then make it executable:
```
 chmod +x $HOME/gvfs-mount
```Then add it to your start up applications:
Dash Home > Startup > Startup Applications > Add
Then point it to your script.

*[COLOR=Blue]Possibly interesting side note[/COLOR]: You can use this technique to change the mount point to something other than a hidden directory:*

Create a new directory, for example:
```
 mkdir $HOME/GVFS
```
Then change the script to this:
```
#! /bin/bash
fusermount -zu ~/.gvfs
/usr/lib/gvfs/gvfs-fuse-daemon ~/GVFS
```

---

### Post by jasonhendry on 2013-05-23
Lisiano's tip worked a treat for me, thanks!

edit: Ubuntu 12.04 on Dell XPSM1530 to Windows 7 Professional shared volume with user/pass read/write permissions.

---

