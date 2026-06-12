---
title: "Can't get old Windows drive access"
date: 2014-04-12
forum: New to Ubuntu
---

### Post by zaivala on 2014-04-12
I went and deleted my Windows section, and used GPartEd to format the partition Ext4.

Now it says the permissions are all Root, and I don't have access to this empty drive.

I hope this is an easy fix...

---

### Post by Double.J on 2014-04-12
Usually it's just the /etc/fstab file.
try opening with gedit and positng the contents?

Jj

---

### Post by zaivala on 2014-04-12
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=017601ed-1684-49ee-9d88-48a4d132cebf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=85104470-f87c-426b-ba8e-5e918f27a01e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Double.J on 2014-04-13
Hi there!

was wirth a shot, not auto mounting at set up.

To see who owns the partition:
```
ls -l /dev/sdax
```
you want your user name to be in the output before root. If it says root root or other users root, thats the problem.

To take ownership, use chown:
```
sudo chown username /dev/sdax 
```note that /dev/sdax could also be where the partition is mounted ie /media/bobs.hdd

To change ownership and add to group:
```
sudo chown user:user /dev/sdax
```note that :user can be whichever group you want to add it too


If you want it to be automatically mounted at boot, an example fstab entry would be:
```
#my ext4 partition on /dev/sdax
UUID=0000-1111-2222-3333     /media/where.to.mount    ext4    rw,user,auto    0    0
```

Your partition's UUID can be found with 
```
blkid
```


hope it helps!

sorry for late reply, real world got in the way!

Jj

---

### Post by Morbius1 on 2014-04-13
[1] You don't want to change ownership or permissions on anything in /dev - that's a system directory and it's meant to be owned by root.

[2] You want to change ownership on the mounted partition.

You didn't post what version of Ubuntu you are using so the partition can be mounted in one of 3 locations. To take ownership of the partition:

```
sudo chown your-user-name /media/something
```
OR
```
sudo chown your-user-name /media/your-user-name/something
```
OR
```
sudo chown your-user-name /media/1000/something
```
You can also do this graphically with a sudo instance of nautilus:
```
gksu nautilus /media
```
Then just right click the mounted partition and change ownership to you.

[3] If you are going to automount it in fstab and you want to use the previosly posted suggestion you are going to have to add another option since the "user" option ( which has no meaning in this context ) disables exec:
> UUID=0000-1111-2222-3333     /media/where.to.mount    ext4    rw,user,auto[COLOR=#0000cd]**,exec**[/COLOR]    0    0
Or you can just make the line look like this:
```
UUID=0000-1111-2222-3333     /media/where.to.mount    ext4 **defaults**    0    0
```

**defaults** = **rw**, **exec**, **auto**, **nouser**.

---

### Post by zaivala on 2014-04-13
> 

If you want it to be automatically mounted at boot, an example fstab entry would be:
```
#my ext4 partition on /dev/sdax
UUID=0000-1111-2222-3333     /media/where.to.mount    ext4    rw,user,auto    0    0
```


This part I didn't understand. However:

zaivala@zaivala-desktop:~$ ls -l /dev/sda1
brw-rw---- 1 root disk 8, 1 Apr 13 09:41 /dev/sda1
zaivala@zaivala-desktop:~$ sudo chown zaivala /dev/sda1
[sudo] password for zaivala: 
zaivala@zaivala-desktop:~$ ls -l /dev/sda1
brw-rw---- 1 zaivala disk 8, 1 Apr 13 09:41 /dev/sda1
zaivala@zaivala-desktop:~$ sudo chown zaivala:zaivala /dev/sda1
zaivala@zaivala-desktop:~$ #my ext4 partition on /dev/sda1
zaivala@zaivala-desktop:~$ blkid
/dev/sda1: UUID="1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775" TYPE="ext4" 
zaivala@zaivala-desktop:~$ 


Did I win?

Moss

---

### Post by zaivala on 2014-04-13
SOMETHING worked. The drive no longer looks as though it is ready to unmount.

Now the question is, is this a "sticky" change? Will it still be like this if I reboot?

Edited to add:
Daggone it. I tried moving files to the drive... Got told I don't have permissions to create a folder in that directory. Now what?

zaivala@zaivala-desktop:~$ ls -l /dev/sda1
brw-rw---- 1 zaivala zaivala 8, 1 Apr 13 09:41 /dev/sda1
zaivala@zaivala-desktop:~$

---

### Post by zaivala on 2014-04-13
To Morbius1:

OK, that had too many generics in it for me to understand what to plug in where.

I'm running 64-bit Ubuntu 13.10 on a Dell Optiplex 740. The drive in question is sda1 (originally the Windoze XP partition, now Microsoft-free).

---

### Post by Morbius1 on 2014-04-13
Post the output of the following command please:
```
ls -al /media/zaivala
```

---

### Post by zaivala on 2014-04-13
I managed to get the files moved, but it raised a lot more questions.

The permissions have not changed. I moved my music and videos to folders on the sda1 drive, and now do not have access to my videos and music. Can't change permissions. Here's the latest report from Terminal:

zaivala@zaivala-desktop:~$ sudo gksu nautilus /media
[sudo] password for zaivala: 

(nautilus:15878): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:15878): IBUS-WARNING **: The owner of /home/zaivala/.config/ibus/bus is not root!
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

zaivala@zaivala-desktop:~$ sudo gksu nautilus /media

(nautilus:15905): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(nautilus:15905): IBUS-WARNING **: The owner of /home/zaivala/.config/ibus/bus is not root!
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

wrestool: /vmlinuz: file contains no resources

(nautilus:15905): Gtk-CRITICAL **: gtk_application_uninhibit: assertion 'cookie > 0' failed

(nautilus:15905): Gtk-CRITICAL **: gtk_application_uninhibit: assertion 'cookie > 0' failed

(nautilus:15905): Gtk-CRITICAL **: gtk_application_uninhibit: assertion 'cookie > 0' failed
zaivala@zaivala-desktop:~$

---

### Post by zaivala on 2014-04-13
> **Morbius1 said:**
> Post the output of the following command please:
```
ls -al /media/zaivala
```

zaivala@zaivala-desktop:~$ ls -al /media/zaivala
total 12
drwxr-x---+ 3 root root  4096 Apr 13 10:41 .
drwxr-xr-x  4 root root  4096 Apr 10 00:58 ..
drwxrwxr-x  6 root users 4096 Apr 13 11:44 1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
zaivala@zaivala-desktop:~$

---

### Post by Morbius1 on 2014-04-13
And why would you run "sudo gksu nautilus"?

gksu is a graphical sudo by itself. All you needed to do is run "gksu nautilus /media" to bring up nautilus with sudo privileges.

---

### Post by Morbius1 on 2014-04-13
> zaivala@zaivala-desktop:~$ ls -al /media/zaivala
total 12
drwxr-x---+ 3 root root  4096 Apr 13 10:41 .
drwxr-xr-x  4 root root  4096 Apr 10 00:58 ..
drwxrwxr-x  6 root users 4096 Apr 13 11:44 1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
So all you needed to do to solve your original problem was to take ownership of the mounted partition:
```
sudo chown zaivala /media/zaivala/1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
```

---

### Post by zaivala on 2014-04-13
> **Morbius1 said:**
> So all you needed to do to solve your original problem was to take ownership of the mounted partition:
```
sudo chown zaivala /media/zaivala/1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
```

zaivala@zaivala-desktop:~$ sudo chown zaivala /media/zaivala/1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
[sudo] password for zaivala: 
zaivala@zaivala-desktop:~$

Did anything actually happen?  Doesn't seem like it...

zaivala@zaivala-desktop:~$ ls -al /media/zaivala
total 12
drwxr-x---+ 3 root    root  4096 Apr 13 10:41 .
drwxr-xr-x  4 root    root  4096 Apr 10 00:58 ..
drwxrwxr-x  6 zaivala users 4096 Apr 13 11:44 1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
zaivala@zaivala-desktop:~$

---

### Post by zaivala on 2014-04-13
> **Morbius1 said:**
> And why would you run "sudo gksu nautilus"?

gksu is a graphical sudo by itself. All you needed to do is run "gksu nautilus /media" to bring up nautilus with sudo privileges.

Um, because I'm a stupid n00b and didn't know that?

---

### Post by zaivala on 2014-04-14
Bump? Got so close yesterday and y'all stopped talking to me...

---

### Post by Morbius1 on 2014-04-14
So what's the problem?

You now have a partition that when mounted is owned by you with read / write access by you:
> zaivala@zaivala-desktop:~$ ls -al /media/zaivala
total 12
drwxr-x---+ 3 root    root  4096 Apr 13 10:41 .
drwxr-xr-x  4 root    root  4096 Apr 10 00:58 ..
[COLOR=#0000cd]**d_rwx_**[/COLOR]rwxr-x  6 _[COLOR=#0000cd]**zaivala**[/COLOR]_ users 4096 Apr 13 11:44 1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775

---

### Post by zaivala on 2014-04-15
No. I don't. I have a drive which is owned by Root and controlled by Root and is only read/write by Root. And because this is Ubuntu, I don't have Root password. I want it owned, read/write, and controlled by zaivala.

---

### Post by Mark Phelps on 2014-04-15
> And because this is Ubuntu, I don't have Root password.

The "root password" should be the same as the one you created when you installed Ubuntu.

---

### Post by Morbius1 on 2014-04-15
> **zaivala said:**
> No. I don't. I have a drive which is owned by Root and controlled by Root and is only read/write by Root. And because this is Ubuntu, I don't have Root password. I want it owned, read/write, and controlled by zaivala.
If we are still talking about the partition mounted at /media/zaivala/1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775 you have a partition that is **[COLOR=#0000cd]owned by zaivala[/COLOR]** and **[COLOR=#0000cd]controlled by zaivala[/COLOR]** and is **[COLOR=#0000cd]read / write by zaivala[/COLOR]** and anyone who is a member of the "users" group. It says so right in the output of the "ls" command you did earlier:

> zaivala@zaivala-desktop:~$ ls -al /media/zaivala
total 12
drwxr-x---+ 3 root    root  4096 Apr 13 10:41 .
drwxr-xr-x  4 root    root  4096 Apr 10 00:58 ..
[COLOR=#0000cd]**d_rwx_**[/COLOR]rwxr-x  6 _[COLOR=#0000cd]**zaivala**[/COLOR]_ users 4096 Apr 13 11:44 1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775                      
Easy way to test it out. Open a terminal and run this command:
```
touch /media/zaivala/1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775/test.txt
```
Based on the output of the "ls" command you should not receive an error message and you should have an empty file named "test.txt" in your partition.

Now if you added anything to that partition as another user or as root itself then that's another story. You will have to change permissions or ownership on any of those sub-directories or files to you if you want to edit them. If this is just a data partition and not a system directory you can do a recursive chown to change ownership of everthing in it to you:
```
sudo chown -R zaivala /media/zaivala/1683ec7a-7bfd-4b8c-bccc-20bbeb2a5775
```

[COLOR=#0000cd]BUT NOTE[/COLOR]: If this new partition is now another OS or has any system files in it you will make a mess of things by doing this so it all depends on what you did to this partition after creating it.

---

### Post by zaivala on 2014-04-15
No, it's not. That password works for sudo and other things, but not root. And if you read up, you'll see that Ubuntu keeps the root password secret.

Anyhow, I finally solved the problem. By formatting the partition NTFS instead of ext_. Then I went into Nautilus to delete the protected directories on my sda6... I must have done something else stupid, for it deleted the directory listings but did not free up the space (nothing got moved to Trash).

So I have access to my files, but still have a fairly full sda6 partition.  Any ideas here?

---

### Post by zaivala on 2014-04-15
We are talking about a drive which REPORTS as being OWNED and CONTROLLED by zaivala... until I try to access it, and then it says it is OWNED and CONTROLLED by root.  If I could get access to my files, I wouldn't still be reporting an issue.

However, as I stated in my previous post, I solved the issue by formatting it back to NTFS, where "ownership" is not an issue apparently.

---

