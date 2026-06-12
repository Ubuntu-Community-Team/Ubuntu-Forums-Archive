---
title: "Home folder file permissions"
date: 2011-09-28
forum: New to Ubuntu
---

### Post by Anuovis on 2011-09-28
I did a fresh Ubuntu 11.04 install. 
I am the owner of /home/username and have "Create and delete files" Folder Access (I get this on Properties in GUI) but I can't set any permissions to the files that are there.

Can't change it via graphical menus.

[I]sudo chown -R username:username /home/username
chown: cannot access `/home/username/.gvfs': Permission denied[/I]

*ls -la /home*
[I]total 28
drwxr-xr-x  4 username root       4096 2011-09-28 18:44 .
drwxr-xr-x 22 root      root       4096 2011-09-28 19:15 ..
drwx------  2 username root      16384 2011-09-28 18:42 lost+found
drwxr-x--- 39 username username  4096 2011-09-28 17:33 username[/I]

Is there anything I can do about it? And how did this happen in the first place?

---

### Post by dethorpe on 2011-09-28
can't say how it happend.
 
Folder permissions look fine, can you do "ls -al /home/username" and post results to see whats going on inside the folder?

---

### Post by Anuovis on 2011-09-28
This is the output. Put *** over personal names.

```
                                
 total 376 
 drwxr-x--- 39 username username   4096 2011-09-28 17:33 . 
 drwxr-xr-x  4 username root        4096 2011-09-28 18:44 .. 
 drwxr-x---  3 username username   4096 2011-09-28 10:25 .adobe 
 drwxr-x---  5 username username   4096 2011-09-28 17:35 .anki 
 drwxr-x---  3 username username   4096 2011-09-28 11:27 .anthy 
 drwxr-x--- 11 username username   4096 2011-09-23 00:16 *** 
 -rwx--x--x  1 username username   1714 2011-09-28 17:53 .bash_history 
 -rwx--xr-x  1 username username    220 2011-09-28 18:44 .bash_logout 
 -rwx--xr-x  1 username username   3353 2011-09-28 18:44 .bashrc 
 drwxr-x--- 13 username username   4096 2011-09-28 17:05 .cache 
 drwxr-x---  3 username username   4096 2011-09-28 18:54 .compiz 
 drwxr-x--- 15 username username   4096 2011-09-28 17:24 .config 
 -rwx--xr-x  1 username username     36 2011-09-11 20:03 ***
 drwxr-x---  3 username username   4096 2011-09-28 18:50 .dbus 
 drwxr-x---  2 username username   4096 2011-09-28 17:54 Desktop 
 -rw----r--  1 username username     78 2011-09-28 17:24 .dmrc 
 drwxr-x---  8 username username   4096 2011-09-28 17:35 Documents 
 drwxr-x---  2 username username   4096 2011-09-28 18:50 Downloads 
 -rwx--x--x  1 username username     16 2011-09-28 18:50 .esd_auth 
 drwxr-x---  2 username username   4096 2011-09-28 11:47 .fontconfig 
 drwxr-x---  4 username username   4096 2011-09-28 17:24 .gconf 
 drwxr-x---  2 username username   4096 2011-09-28 17:54 .gconfd 
 drwxr-x---  4 username username   4096 2011-09-28 11:15 .gegl-0.0 
 drwxr-x--- 22 username username   4096 2011-09-28 17:46 .gimp-2.6 
 -rwx--x--x  1 username username      0 2011-09-28 17:20 .gksu.lock 
 drwxr-x---  7 username username   4096 2011-09-28 10:50 .gnome2 
 drwxr-x---  2 username username   4096 2011-09-28 18:52 .gnome2_private 
 drwxr-x---  2 username username   4096 2011-09-28 17:05 .gstreamer-0.10 
 -rw----r--  1 username username    188 2011-09-28 17:25 .gtk-bookmarks 
 dr-x------  2 username username      0 2011-09-28 17:24 .gvfs 
 -rwx--x--x  1 username username   2580 2011-09-28 17:24 .ICEauthority 
 drwxr-x---  2 username username   4096 2011-09-28 11:31 .icons 
 drwxr-x---  4 username username   4096 2011-09-28 17:17 *** 
 drwxr-x---  3 username username   4096 2011-09-28 11:46 .libreoffice 
 drwxr-x---  3 username username   4096 2011-09-28 18:50 .local 
 drwxr-x---  2 username username   4096 2011-09-28 17:16 .macromedia 
 drwxr-x---  4 username username   4096 2011-09-28 18:55 .mozilla 
 drwxr-x---  2 username username   4096 2011-09-28 18:50 Music 
 drwxr-x---  2 username username   4096 2011-09-28 18:50 .nautilus 
 drwxr-x---  6 username username   4096 2011-09-28 17:33 Pictures 
 drwxr-x---  3 username username   4096 2011-09-28 19:13 .pki 
 -rwx--xr-x  1 username username    675 2011-09-28 18:44 .profile 
 drwxr-x---  2 username username   4096 2011-09-28 17:24 .pulse 
 -rwx--x--x  1 username username    256 2011-09-28 18:50 .pulse-cookie 
 drwx------  4 username username   4096 2011-09-22 23:58 ***
 -rwx--xr-x  1 username username      0 2011-09-28 18:51 .sudo_as_admin_successful 
 drwxr-x---  2 username username   4096 2011-09-28 18:50 Templates 
 drwxr-x---  2 username username   4096 2011-09-28 10:25 .themes 
 drwxr-x---  4 username username   4096 2011-09-28 10:25 .thumbnails 
 drwxr-x---  2 username username   4096 2011-09-28 18:50 Videos 
 drwxr-x---  2 username username   4096 2011-09-28 11:24 .xinput.d 
 -rwx--xr-x  1 username username    834 2011-09-28 14:12 .xscreensaver-getimage.cache 
 -rw-------  1 username username 100150 2011-09-28 18:10 .xsession-errors 
 -rwx--x--x  1 username username  71310 2011-09-28 17:24 .xsession-errors.old 
 
```

---

### Post by mcduck on 2011-09-28
There are some files in user's home directory that require certain permissions or ownership other than your user.

For example .gvfs and of course the ".." (which is a link to parent directory, in this case /home, so you obviously aren't supposed to own it)

And lost+found always belongs to root, it's used for storing recovered files in case fsck repairs any file system errors.

Based on your "ls" output, everything seems to be normal. Are you really unable to change *any* file's permissions, or is the problem only related to trying to change *every* file's permissions?

(this is of course assuming that your user name really is "username" as in the output, or that you've changed it when posting the output here. Otherwise make sure to replace the "username" in such commands with your actual user name... ;))

---

### Post by mikewhatever on 2011-09-28
The .gvfs directory is readable and executable by default and by design. You've tried modifying its permission, in other words, writing changes to the non-writable dir.

If you plan on playing with chmod and chown, I'd recommend making a backup of your files asap, and keeping the installation CD at hand.

---

### Post by Anuovis on 2011-09-28
> **mcduck said:**
> 
Based on your "ls" output, everything seems to be normal. Are you really unable to change *any* file's permissions, or is the problem only related to trying to change *every* file's permissions?


It seems that I actually can modify files in Home. I was copying a bunch of them from a FAT32 system before, then tried to change or remove one and got some error that  mentioned the permissions in Home. After that I checked the Properties and was unable to add any permissions. I can't do that now either, with any folder. But it seems individual files are working properly at the moment.

It has been a hectic day and frankly I don't remember what the exact error was and when did it pop up. :???:

> **mikewhatever said:**
> If you plan on playing with chmod and  chown, I'd recommend making a backup of your files asap, and keeping the  installation CD at hand.

I will keep that in mind, thanks.


I guess I will wait a bit and mark this as solved if everything goes well from now on. Still very curious what could have caused that misbehavior. It's possible I might have misunderstood something. Smells like a noobcake ... Thank you all.

---

### Post by Demon1986 on 2011-10-15
well, you havent missunderstood something, i have exact same problem, trying to host a game server, where you can dl the maps directly from it, and i use symlinks, problem is i cant access the folder from the webserver, and when i try to put read/write permissions on the folders, they get reset, the files are no problem, it has been submitted as a bug, but status is triaged, for reasons idk, i use seperate root and home partitions on same disk, both using ext4

---

