---
title: "samba shares - USB drive on xubuntu to be accessed by various Windows"
date: 2013-04-20
forum: New to Ubuntu
---

### Post by squakie on 2013-04-20
Well, I sort of screwed up my thoughts on this and went off in the wrong direction, so........I have an old laptop running xubuntu that has a 750gb USB drive attached.  I'd like to set up Samba shares that require a login - ex:  folder1 to be accessed by user1.  User1 will be running on a Windows machine.  I have 3 laptops in the house that I'd like to access their own shares on the 750GB drive on the xubuntu machine.  1 is XP, 1 is Windows 7 and the last is Windows 8.  I'd like to be able to do the following:  at logon on each Windows machine, automatically connect that "user" with a userid and password to the xubuntu share for that user.  That way the users of each of those laptops doesn't have to know squat about shares - just that there is another disk available.  It's been a long LONG time, but I remember back when working with Windows shares we would log the user in and connect a logical drive to their share (folder) on the server.  I would think I could do the same thing with Samba and the various Windows laptops.  I know how to set up a share in Samba.  I know how to create a Samba user - but I don't know how to use this on the Windows side logon, connect, whatever you want to call it (or even from another Ubuntu box) and assign a drive letter to the share - something along the lines of //server/share - but I don't remember any of the syntax or specifics anymore.  Nor do I remember how to get the default Windows group from homegroup to something like "mygroup" (obviously it will be different from that).  So, can anyone point me to a good how-to for setting things up on the xubuntu side and the various Windows laptops?  Thanks!

---

### Post by squakie on 2013-04-20
I find the plot thickens:  I need to mount the external USB drive somewhere before I can share it.  I noticed xubuntu lets me use file manager and examine the drive contents, but the option shows to mount the device.  I'm assuming this apparently not-done mount is what is stopping the "share" option from showing when I right-click on any folder on the drive.  So I guess I need an fstab entry so the device is mounted at boot - not real sure how to do that - especially when it's a USB device - how do I know at mount where the device is in the /dev tree?  Can I mount it to a folder under /home so the device is not mounted in any given user's file structures?   Hummmmmm, been trying to read man pages on fstab but can't figure out how to create an entry for a USB device.  Help?? (!!)  ;)

---

### Post by mikewhatever on 2013-04-21
You don't really  need to bother with the /dev/... notion, as you don't mount a device, but a file system, which can be uniqely referenced through its UUID, and it shouldn't really matter how the device is connected.  So, find out the UUID with 'sudo blkid', create a mount point, say /mnt/share, then create an fstab entry (the file system is probably NTFS, verify that):
```

UUID=<uuid here> /mnt/share ntfs-3g  defaults,locale=en_US.utf8  0 0
```
Check out the help page for more info: [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table)

Once mounted, you should be able to connect to the defined shares from Windows, and assign drive letters through the file browser. Windows calls it "mapping a drive".
[http://compnetworking.about.com/od/windowsxpnetworking/ht/mapnetworkdrive.htm](http://compnetworking.about.com/od/windowsxpnetworking/ht/mapnetworkdrive.htm)

---

### Post by squakie on 2013-04-22
Well, I don't have a clue what I did (except remove everything Samba and start over ;) ), but I now have the "Network" option in the file manager and can see the system.

I have it using user, have set up a Samba user in the Samba users file (dave = dave), created a share (/mnt/NAS/dwedell) and have set access to that share as user dave.  I changed the Samba user password to match that coming from Windows 8 (it has a capital letter first - i.e., "Axxxxxxx").  The actual Ubuntu user dave has an Ubuntu password (example) of "axxxxxxx".

Now the problem I'm have is getting Windows 8 to see it.  I assigned the Windows 8 laptop to a workgroup that matches the Samba defined workgroup, and removed the Windows 8 laptop from the homegroup it had defined by default.  Right now I  see the Samba "server" - xubuntu - in Windows 8 file manager, but when I try to expand it I get an error window saying "Windows cannot access \\XUBUNTU" with the detail saying network path not found.

When I try to define a share in Windows 8, it gives me the access error again for [\\XUBUNTU\some-dir]("file://\\XUBUNTU\some-dir").  

I don't quite understand why the server "XUBUNTU" shows in "Network" in Windows 8, but it can't be accessed.  I've even done the following:

-  modified the register with Win 7 changes to allow access to other/older file sharing systems (like XP, and presumably Ubuntu).

-  changed the share in Samba to be accessable by all users, not just "dave"

Something that might be causing a problem(?):

- I used "sudo" to set up the mount point for the external USB drive as "/mnt/NAS", and added it to fstab

- the external USB drive is formatted in NTFS

I read a post that said this can be a problem for who the owner is.  If I change the ownership on the given folder I want to share to "dave", would this in someway make a difference?

I guess the biggest thing is actually being able to see ANYTHING on my Windows 8 laptop on the Samba "server" - xubuntu with Samba.

---

### Post by squakie on 2013-04-22
> **mikewhatever said:**
> You don't really  need to bother with the /dev/... notion, as you don't mount a device, but a file system, which can be uniqely referenced through its UUID, and it shouldn't really matter how the device is connected.  So, find out the UUID with 'sudo blkid', create a mount point, say /mnt/share, then create an fstab entry (the file system is probably NTFS, verify that):
```

UUID=<uuid here> /mnt/share ntfs-3g  defaults,locale=en_US.utf8  0 0
```
Check out the help page for more info: [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Editing_Ubuntu.27s_filesystem_table)

Once mounted, you should be able to connect to the defined shares from Windows, and assign drive letters through the file browser. Windows calls it "mapping a drive".
[http://compnetworking.about.com/od/windowsxpnetworking/ht/mapnetworkdrive.htm](http://compnetworking.about.com/od/windowsxpnetworking/ht/mapnetworkdrive.htm)

Forgot to thank you!   I've got it mounted as /mnt/NAS.  I'm going to take a look at the options for a fstab entry to see if I can mount it as being owned by a group (like "nasusers").  Currently it's owned by root, and I'm not able to change permission/owner/group on the drive or it's folders.  I'm creating new user names under a group of "davesa" and just pointing their home folder to a folder on that device. 

I guess more hours of trying to make this work.  One time Windows 8 will see "XUBUNTU" under "Network" - the next time not.  Not sure what's going one their but even when "XUBUNTU" shows in "Network" in Windows 8, trying to expand it results in path not found messages.  I'm wondering if those are from permission problems on the mount point and device.

---

### Post by squakie on 2013-04-22
I'm giving up on this for now.  I think it has something to do with trying to use an external USB drive that is a NTFS file system.  I know you can't really change permissions on such a thing (when it's NTFS).  I might look and see if writing a udev rule for it can help at mount time, but I doubt it.

I'm going to have to start over again.  For now I'll mark this as solved until I do a whole lot more trying, pulling my hair our (hey - there's not much there to begin with! ;) ), punting, reloading xubuntu so I have a clean slate to start over again, and repeat all the above.

I really just want:

- shares defined via folders on an external USB hard disk
- somehow, for each Windows user, have their machines automatically log to the Samba server and by user id (having the same userid/password as their Windows logon) point them to the share and assign a dirve letter.  I want it to be invisible to the user that they are accessing something on a remote disk.

I've done a lot of reading on the net about this.  I'm must be really dumb, as I don't understand why what I'm doing doesn't work.  Have the time the Samba server (by default it shows as "XUBUNTU") doesn't even show on the Linux host machine.  When it does, if I try to manually map a network drive in Windows it says the path can't be found and to check the net connection.

---

### Post by squakie on 2013-04-24
Marking this as solved, as the exernal USB drive works as intended.  Windows, on the other hand, doesn't seem to be cooperating.

---

### Post by mörgæs on 2013-04-24
This is how to do it:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by squakie on 2013-06-25
I have this all figured out and working now.

---

