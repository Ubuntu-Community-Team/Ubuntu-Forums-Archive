---
title: "Errors resulting from moving /home?"
date: 2015-08-27
forum: New to Ubuntu
---

### Post by makem2 on 2015-08-27
I am using Kubuntu and am now getting a series of errors possibly as a result of moving /home to another partition using:

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Although I do remember previously seeing the error: sudo: unable to resolve host newTOSH (newTOSH being the computer name)

Current errors:

Opening partitionmanager (opens and usable)

```

makem@newTOSH:~$ sudo partitionmanager
[sudo] password for makem: 
sh: 0: getcwd() failed: No such file or directory
sh: 0: getcwd() failed: No such file or directory
Error: "/var/tmp/kdecache-makem" is owned by uid 1000 instead of uid 0.
sh: 0: getcwd() failed: No such file or directory
partitionmanager(2844)/kdeui (kdelibs): Attempt to use QAction "toggleDockDevices" with KXMLGUIFactory! 
partitionmanager(2844)/kdeui (kdelibs): Attempt to use QAction "toggleDockOperations" with KXMLGUIFactory! 
partitionmanager(2844)/kdeui (kdelibs): Attempt to use QAction "toggleDockInformation" with KXMLGUIFactory! 
partitionmanager(2844)/kdeui (kdelibs): Attempt to use QAction "toggleDockLog" with KXMLGUIFactory! 

```

Renaming a device (/home partition):

```

makem@newTOSH:~$ sudo e2label /dev/sda9
sudo: unable to resolve host newTOSH

```

This should produce the current name of the device allowing me to check I have the correct one before renaming it.

If I use the following the device is correctly renamed:

```

makem@newTOSH:~$ sudo e2label /dev/sda9 Home

```

The errors to date have not made any difference or stopped me doing anything but I would like to resolve them or at least know what causes them and how to avoid in the future.

I would appreciate help.

---

### Post by TheFu on 2015-08-27
There are 2 ways to give HOME more storage.

a)
* connect and mount the new storage where you want it - usually something like /export/home for a single system using NFS mounts or /u/a/,  /u/b/, ... /u/z/ if there are thousands of uses and you are running automount.
* modify the password entry for every userid to change the HOME setting for each userid to point to the new userid HOME locations.
* move the data from the old /home location to where ever the new storage is. Retain owner, group, permissions ... 
* logout , then login.

Or
b) quickly (less than 1 sec for all of this - which usually means writing a script),  
* move /home to some other name, 
* create a new /home directory
* mount the new storage to /home
* move all the directories files, as root, from the old home location to the new home storage.
* Finally, logout the login. 

When done, the /home/userids each appear in the directory structure with the same owners, groups, permissions and data as before.

For HOME to work, the location in the directory structure needs to match whatever is in the /etc/passwd file ( or what LDAP knows for those userids ).

Don't forget to modify the backup scripts to prevent the old backups from filling up thanks to all the new storage added.  I like to add backup storage when adding any new storage. If I can't afford to get both storage, then I'll wait. 

That should be it.

That's it.  How the storage is mounted doesn't matter - fstab, autofs, automounter, NIS, NIS+ - doesn't matter. It just needs to appear to be in the place that the password-entry says for each different userid.  If it isn't clear, every userid can be on different storage.

I suppose you are trying to change the label to help mount the partition?  It doesn't matter for anything else. Is that the real question? I'm fixated on HOME.

---

### Post by makem2 on 2015-08-27
Home moved correctly and I was renaming  a partition just to 'make it look nice'. It was the errors I was concerned about.

However, since the post I decided to reinstall the OS, rearranging partitions as I went.

The reason for all the messing about was dual booting various flavours before finally swapping to linux. I will stick with kbuntu which is now a fresh install using my previous /Home which has been greatly enlarged.

Thank you for your concern and information.

---

### Post by TheFu on 2015-08-27
Glad you figured it out.  Just be aware that mixing different DEs under the same userid can lead to unexpected results. KDE is pretty stand-alone, so it probably won't interfere with other DEs.  However, the gnome-based DEs are known to use some of the same settings and store those in the same config files, with conflicting results. Best to use different accounts for testing different DEs.

---

### Post by makem2 on 2015-08-27
Hmm, thought I had!

Not so,now lost windows!

[http://ubuntuforums.org/showthread.php?t=2292425](http://ubuntuforums.org/showthread.php?t=2292425)

What a merry go round after I had decided which flavor to use :(

---

