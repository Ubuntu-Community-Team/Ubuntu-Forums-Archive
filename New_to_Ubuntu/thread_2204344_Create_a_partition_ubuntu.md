---
title: "Create a partition ubuntu"
date: 2014-02-08
forum: New to Ubuntu
---

### Post by kaushik3 on 2014-02-08
I have 250 gb hard drive for ubuntu I want to resize it and use that unallocated space to store some other data ? how can i do it I see many options etx 2 exts 3 4.. etc etc which one should i chose to use and open that drive when ever i want just as in windows ?

---

### Post by Bucky Ball on 2014-02-08
Welcome. Do you have Ubuntu installed already? Anyhow, boot from live media (install disk or USB), try Ubuntu, open Gparted, resize/remove/create partitions as you wish. You can not resize the / partition that Ubuntu is running on with Ubuntu running on it! Therefore, you need to boot from the Live image even if you have Ubuntu installed already.

If you are sharing data with a Win install, use NTFS filesystem for your partitions. Ubuntu only; EXT4. That's it.

---

### Post by kaushik3 on 2014-02-08
Thank you so much

---

### Post by Bucky Ball on 2014-02-08
You're welcome, and welcome to the forums. Let us know if you have any problems with the partitioning. Mark thread as solved when you're happy and post a new thread for any new problems (if they don't relate to the title of this thread, that is). ;)

---

### Post by kaushik3 on 2014-02-08
The new partition i just created has folder LOST + Found what does that mean ?

---

### Post by Bucky Ball on 2014-02-08
Completely normal and you should get worried if there isn't one there:

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by kaushik3 on 2014-02-08
Uh iam not able to create a folder in it and store my pictures . create new folder option is greyed out

---

### Post by Bucky Ball on 2014-02-08
Lost and found? You don't want to do anything with that. System property. Just ignore it and leave it alone. Not for users to create folders, or anything else, in. ;)

---

### Post by kaushik3 on 2014-02-08
No in the drive itself . :( I am not able to put my pictures in that new volume ive just created

---

### Post by Dennis N on 2014-02-08
> **kaushik3 said:**
> No in the drive itself . :( I am not able to put my pictures in that new volume ive just created

Is this an external hard drive? And what kind of file system - ext4, ntfs, or fat32 does it have?

---

### Post by kaushik3 on 2014-02-08
ext4

---

### Post by Bucky Ball on 2014-02-08
What happens when you're trying to put the data in? Error message or it just won't go? Are you trying to drag and drop and it won't 'drop'? You created in Gparted as discussed and it is mounted, etc?

If you want it to mount at boot we can show you how to do that. Would fix any permission problems you might be having I should think.

---

### Post by Dennis N on 2014-02-08
> **kaushik3 said:**
> ext4

You haven't said if this is an external drive you are plugging into a USB port occasionally, or your main hard drive. If external, this happens with ext4 but is easy to fix.

---

### Post by kaushik3 on 2014-02-08
no internal harddrive  only it sucks man when you cant even put your files in other partitions :( :( . The option to create new folder is greyed out . when i click on properties and see something kinda permissions it says you dont or cant change something because you dont own it some thing else like that .

---

### Post by Dennis N on 2014-02-08
> **kaushik3 said:**
> no internal harddrive  only it sucks man when you cant even put your files in other partitions :( :( . The option to create new folder is greyed out . when i click on properties and see something kinda permissions it says you dont or cant change something because you dont own it some thing else like that .

The problem is you don't own the filesystem on the ext4 partition you made. By default, it is owned by root and only the owner has write permissions. You need write permissions to create a folder or save a file there. 

If it was external, I have an outline how to fix it. But since it isn't, move on.

Since it is the internal HD, one way is to make an entry into fstab so that it is mounted at boot time and you can access it. There are many web articles on this which show how. Google "automount partition at startup ubuntu". You might give this one I saw a look, as it is different, using udisks: 

[http://www.linuxandlife.com/2013/06/automount-ubuntu-1304-linux-mint-15.html](http://www.linuxandlife.com/2013/06/automount-ubuntu-1304-linux-mint-15.html)

good luck

---

### Post by oldfred on 2014-02-08
If you mounted it with Nautilus unmount it first.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Then if you want to have it auto mount every time you reboot. Follow template here:
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

    
More info if desired.

 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

