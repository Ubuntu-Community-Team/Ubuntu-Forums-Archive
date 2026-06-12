---
title: "Can't access IDE drive"
date: 2014-06-08
forum: New to Ubuntu
---

### Post by Paper Pusher on 2014-06-08
I have a home built computer running Ubuntu 12.04 with a gigabytle ultra durable  motherboard, 78LMT-USB3. This board has both IDE and SATA connections. The SATA connection has my 120GB SSD. It is my boot drive. The IDE connection has a 160GB harddrive. It is for storing data. Both drives are visible from gparted. I have formated the IDE drive to EXE for file format. The IDE drive is also visible from my file manager, but I cannot access the drive. I get error that says the folder contents could not be displated, and that I do not have the permission necessary to view the contents. I also cannot create a new folder there. Also when I drag a file onto the IDE drive I get an error that says I do not have persmission to make the folder in that destiniation. 

What can I do to make the IDE disk drive writable?

---

### Post by jdeca57 on 2014-06-08
> **Paper Pusher said:**
>  I have formated the IDE drive to EXE for file format. 
I'm sorry, but could you explain what a EXE file format is?  Or is this a typo?

---

### Post by Paper Pusher on 2014-06-08
I apologize, the format is ext4 it was a typo.

---

### Post by arpanaut on 2014-06-08
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Couple of links to get you going with properly mounting your drive for access.

---

### Post by coffeecat on 2014-06-08
@Paper Pusher, at the moment the ext4 filesystem is owned by root, which is why you don't have the necessary permissions. You can change the ownership of a Linux filesystem by chowning the mountpoint while it is mounted, which has the slightly curious effect of changing the ownership of the filesystem, not the mountpoint. Make sure the filesystem/partition is mounted first:

```
sudo chown yourusername:yourusername /path/to/mountpoint
```

---

### Post by Paper Pusher on 2014-06-10
Hi coffeecat,

          I would love to do what you told me to do, but I need a little more help. 

-Thanks!

---

### Post by Paper Pusher on 2014-06-10
Hi arpanaut,

       I tried the below and I didn't have any luck. I have even updated to Ubuntu 14.04 and I still am having issues. 

              The third - simple - method is to install the pysdm package (in Gutsy) and then use System-Administration-Storage Device Manager without any manual editing of the fstab file, and disregard most of the   instructions that follow. (NOTE: psydm removed from repositories in 12.10 and presumably beyond - see [http://ubuntuforums.org/showthread.php?p=12338212](http://ubuntuforums.org/showthread.php?p=12338212). Use of arios automount or mount manager not recommended)

---

### Post by coffeecat on 2014-06-11
> **Paper Pusher said:**
> Hi coffeecat,

          I would love to do what you told me to do, but I need a little more help. 

-Thanks!

You don't mention how you are mounting the new partition, except that you were not able to install pysdm, and I'm really glad you weren't able to install it. When it was around it seemed to cause more problems than it solved. Assuming you haven't yet manually edited /etc/fstab to mount the partition, and seeing as you have updated to 14.04, if you use the file manager to mount the partition in 14.04, it will be automounted to /media/yourusername/mountpoint. Where "yourusername" will be your Ubuntu login name and "mountpoint" will be the partition label if there is a partition label, or the UUID (a long apparently random string) if not. Example UUID for an ext4 partition: 2f485718-97d1-42d7-96bb-5d00d71c4136 .

So - assuming all the above, open a file manager window, find your new partition in the left pane (if it doesn't have a label it will be identified by size) and click on it. The right pane will then open in the now-mounted partition, probably showing only the lost+found folder. Now open a terminal and run this command:

```
sudo chown yourusername: /media/yourusername/mountpoint
```

Substitute "yourusername" in the two places with your login name, and substitute "mountpoint" with the mountpoint as described above. To find out what this is, with the file manager window still open, press ctrl-L and the address breadcrumb bar will change to an address bar with the full mountpoint path already highlighted so that you can copy it with ctrl-c and then paste it into your terminal command with ctrl-shift-v.

By the way, I've simplified the chown command slightly. Originally "yourusername:yourusername" in my earlier post which defines user and group ownership, if you simply use "yourusername:" (with a trailing colon) the chown command will automatically apply your default usergroup as group ownership.

---

### Post by Paper Pusher on 2014-06-13
Thanks Coffeecat! That was very understandable and it worked great. I would just like to know if it will still work tomorrow after I turn off the machine?

---

### Post by coffeecat on 2014-06-14
Once you have chown'd a filesystem in this way, the ownership remains even when unmounted and remounted. For instance, if you were to remove the hard drive with the chown'd partition and put it in another machine, and then mount the partition from Ubuntu installed in that other machine, you would find that you were still the owner of he filesystem. That is, so long as your UID in the second Ubuntu system was the same as in the first. The chown command works with UID (user ID) and GID (group ID). The first created user in Ubuntu is allocated the UID of 1000 and the default group for that user has the GID 1000. The second created user 1001:1001 and so on. So an Ubuntu account with the same UID:GID as the ownership of the filesystem would be able to access it.

Another curious thing is that the mountpoint itself (the directory) is not chown'd, rather the actual ext4 filesystem in the partition. This can be tested by running ls -l on a manually created mountpoint while the partition is mounted and after unmounting. While mounted, ownership will show up as yourusername:yourusername. After unmounting, the output of ls -l for the mountpoint reverts to root:root, if it was created by root, which is usual. You won't be able to test this when mounting from the file manager, because the mountpoint is dynamically created and then erased when the partition is unmounted.

---

