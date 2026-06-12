---
title: "Missing /data title."
date: 2014-06-16
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-16
When I first installed Ubuntu 14.04 a few weeks ago I found that my /data ntfs partition was listed under 'devices'. I have just re-installed Ubuntu and the /data partition is no longer listed as a device. However, the 'Disks' program shows it to be there and I have a Data folde, containing what I believe to be the contents of the /data partition, within the 'Computer' heading under devices. 
Could anyone explain why the '/data' partition is not now separately listed under 'devices'? Can it be corrected if this is an error I made in the re-install?.

---

### Post by cariboo on 2014-06-17
Check to see if you have ntfs-3g installed

---

### Post by Impavidus on 2014-06-18
Partitions that are mentioned in /etc/fstab are not listed under devices in the file manager. fstab may contain the instruction to automount it at your data directory. That may be the difference with your previous install.

---

### Post by gordon99 on 2014-06-19
Sorry Cariboo and Impavidus for my delay in responding. I'm afraid I am unable to say anything intelligent in reply to to your question/comment, as the matters you raise are outside of my knowledge zone. Perhaps if I enlarge on what I have found it may help you decide whether or not I have a problem with the Ubuntu installation.
I certainly seem to have a separate '/data (D)' partition containing those files I would expect. The partition shows up in Windows.
In Ubuntu, the list under the 'Devices' heading is 'HP Tools', (a repair partition, as you will probably know); '198GB Volume' (C:drive I believe); 'System' ( containing a Boot file, System Volume Information and Re- cycle bin files) and Computer. The latter heading seems to contain all the Ubuntu files including one titled 'data'. This data file seems to hold the files found in the '/data (D)' partition but permissions show it to be in 'root'. I am puzzled as to why the 'data' partition is simply now showing as a folder with many other files or folders, all under the heading 'Computer' whereas, when I initially installed Ubuntu, the 'Devices' list had a separate heading for '/data'. Maybe it is of little or no consequence, or maybe it is an installation error that I need to correct somehow.

---

### Post by Impavidus on 2014-06-19
You're fine.

Every part of the file system that is mounted (=attached to the file system) is shown in one big tree in Linux. It doesn't matter how many partitions there are. In contrast to your previous installation, the data partition is now automatically mounted at boot time. It can only be unmounted at shutdown or by root. As an ordinary user can't mount or unmount it anyway, there is no reason to put it in the side pane of the file manager. During installation you may have chosen for manual partitioning and picked this data partition to mount at /data.

As it is automatically mounted, it is owned by root (by default). That's fine, as ownership and permissions are not supported on ntfs partitions anyway.

If you can't get permission to read or write on this partition, post the contents of /etc/fstab, and we can show you how to get those permissions. It may be instructive to look at that file anyway.

---

### Post by gordon99 on 2014-06-19
Thanks Impavidus for the reasssurance.I don't appear have a problem reading or writing to the partition but I will have a look /etc/fstab..

---

