---
title: "The volume &quot;filesystem root&quot; has only 0 bytes disk space remaining"
date: 2015-06-12
forum: New to Ubuntu
---

### Post by YE_XIANG on 2015-06-12
Hello!
Please help me

Throws this error message: "The volume "filesystem root" has only 0 bytes disk space remaining".
OS Ubuntu 12.04

```
ascc@ascc-HP-Elite-7000-Microtower-PC:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        92G   92G     0 100% /
udev            4.0G  4.0K  4.0G   1% /dev
tmpfs           1.6G  912K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            4.0G  8.0K  4.0G   1% /run/shm
/dev/sda6       360G  9.8G  332G   3% /home
overflow        1.0M   36K  988K   4% /tmp
ascc@ascc-HP-Elite-7000-Microtower-PC:~$ df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda5       6111232 316785  5794447    6% /
udev             198411    534   197877    1% /dev
tmpfs            202360    459   201901    1% /run
none             202360      3   202357    1% /run/lock
none             202360      3   202357    1% /run/shm
/dev/sda6      23937024 109625 23827399    1% /home
overflow         202360     18   202342    1% /tmp

```

Yesterday I ran the command to set the root like:
chmod -R 777
which leads to multiple problems in Ubuntu, one of them is the disk space problem.
When I open "Disk Utility", it is totally blank.

Besides, I can not excute "sudo"
"sudo: must be setuid root"

I know I srewed up the whole System, but I don't want to reinstall the system, coz there in a bunch of important compiled files on it
can any superhero save my computer? >.<::

---

### Post by yetimon_64 on 2015-06-12
> but I don't want to reinstall the system, coz there in a bunch of important compiled files on it

Those files can easily be recovered by running a live dvd image and copying/moving the files to an external drive if a full reinstall is necessary. 

Sometimes a full reinstall is much easier/quicker than trying to check hundreds of system files for varying permissions settings. I think this may be one case where a reinstall may be necessary, await further advice from other helpers here though.

I would advise you to use a live image to back up those important files off the drive before attempting any "repairs" to the filesystem, even if you don't do a full reinstall. Sometimes a data disaster can occur during such repairs.

---

### Post by ajgreeny on 2015-06-12
> **YE_XIANG said:**
> 
Yesterday I ran the command to set the root like:
chmod -R 777
which leads to multiple problems in Ubuntu, one of them is the disk space problem.
When I open "Disk Utility", it is totally blank.

Besides, I can not excute "sudo"
"sudo: must be setuid root"

I know I screwed up the whole System, but I don't want to reinstall the system, coz there in a bunch of important compiled files on it
can any superhero save my computer? >.<::
I don't think you have a choice other than reinstalling as you will have totally messed up your system. I am not even sure if you will be able to do anything in recovery-mode from grub-menu as the permissions mess you have got yourself into may make that useless now.

The files and folders in the root filesystem have many and varied permissions which are absolutely and completely set; change them at your peril as you can not now just change them back to what they were previously with a similar single command.

Remember; **do not mess with your root filesystem** unless you really know what you're doing, why you're doing it, and how to reverse it if necessary.

---

### Post by YE_XIANG on 2015-06-15
thanks a lot

---

### Post by YE_XIANG on 2015-06-15
so, what should I do if I have no permission to edit or move a file?

---

### Post by yetimon_64 on 2015-06-15
> **YE_XIANG said:**
> so, what should I do if I have no permission to edit or move a file?

Boot your system to a live dvd/usb image, recover any needed files using the live dvd and copy to external storage, then reinstall the system and restore the backed up files. **Edit:** I would also suggest you back up your home folder completely, if during a reinstall you happen to format it, then you can recover the home folder as well as the system. 

To get a root terminal or launch a filebrowser as root on a live dvd/usb boot does not even require a password. This makes backing up and/or repairing an installed system relatively easy. Nautilus on the live dvd should be able to see your drive/partitions etc and can be used to copy most files, including system files, for backup/reinstall purposes.

---

