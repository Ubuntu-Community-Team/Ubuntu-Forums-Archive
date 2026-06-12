---
title: "Help with mount points / fstab"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by jis on 2008-06-27
The information is stored in /etc/fstab text file. Another option is to add a panel item called "Mount devices", see [file:////usr/share/xubuntu-docs/xfce-desktop.html#desktop]("file:////usr/share/xubuntu-docs/xfce-desktop.html#desktop") for instructions. (I suppose you are using Xubuntu 8.04.) BTW Do you have Xubuntu 8.04 Documentation bookmarked by default in Firefox?

Unfortunately the Mount devices panel item does not show USB drives or their partitions.
P.S. That is fixed in some future release, see 
[https://bugs.launchpad.net/ubuntu/+source/xfce4-mount-plugin/+bug/240139](https://bugs.launchpad.net/ubuntu/+source/xfce4-mount-plugin/+bug/240139)

---

### Post by imjscn on 2008-06-27
Hi jis, 
Yes, I installed Xubuntue, so, Xubuntue doesn't have the "Administrator" entry, where can I find something similar to this?
yes, I have Xubuntu Documentation by default, I've read through it, it's helpful, but I still need more details to make things running. 
I just added the "Mount device", Now I see it. As I suspected, I mounted one partition wrongly.I found the Move Mount Point Document.

I still need the "Administrator" entry to manage other job...

Thanks!

---

### Post by jw5801 on 2008-06-27
> **imjscn said:**
> Hi jis, 
Yes, I installed Xubuntue, so, Xubuntue doesn't have the "Administrator" entry, where can I find something similar to this?
yes, I have Xubuntu Documentation by default, I've read through it, it's helpful, but I still need more details to make things running. 
I just added the "Mount device", Now I see it. As I suspected, I mounted one partition wrongly.I found the Move Mount Point Document.

I still need the "Administrator" entry to manage other job...

Thanks!

I don't know what you mean by 'Administrator' entry. You can install GParted and opening that should show you lots of information about your partitions. 'sudo apt-get install gparted' and it turns up under 'System > Partition Editor.'

---

### Post by jis on 2008-06-27
I don't understand what you mean by the "Administrator" entry. What kind of job you mean?

---

### Post by jis on 2008-06-27
By the way, I agree that the icon of the "Mount devices" item in a panel could be more visible. It is hard to see especially, if you make your panel small.

---

### Post by imjscn on 2008-06-27
for example, If I want to enable "univers repostories", how to do it? I read in a guide(can't find the link to that item now), it need to go System/Administrator.. to enable the repostories"

---

### Post by imjscn on 2008-06-27
I have another question: I choose manual partitioning at installing, here are what I have now:

Sda1  /      10G
sda2  /boot   1G
sda3 /Swamp   1G

sda5 /Home   35G ?
sda6 /tmp     1G
sda7 /usr     15G
sda8 /srv     10G  ?

the /srv was because after the above partition, there's still space, so I just mount it as /srv, but I don't know what's the usage of /srv? So, I think, it's better mount it to be /var or merge it into /Home,  Is this worth doing?

---

### Post by jis on 2008-06-27
Use Applications > System > Software Sources

---

### Post by jis on 2008-06-27
> **imjscn said:**
> I have another question: I choose manual partitioning at installing, here are what I have now:

Sda1  /      10G
sda2  /boot   1G
sda3 /Swamp   1G

sda5 /Home   35G ?
sda6 /tmp     1G
sda7 /usr     15G
sda8 /srv     10G  ?

the /srv was because after the above partition, there's still space, so I just mount it as /srv, but I don't know what's the usage of /srv? So, I think, it's better mount it to be /var or merge it into /Home,  Is this worth doing?

First, be strict with the mount point names, I mean capitalization etc.

It is hard to determine proper /tmp size because it fills up during a session. On the other hand it is good to have it separate to not accidentally fill / and deny the use of your system. Same with /var except it fills incrementally session after session, right? (Currently I don't have a separate /var partition, but there is about 800 MB in /var.)

What do you need separate /usr for?

I don't know the purpose of /srv; I guess you don't need a separate partition for it. If you use separate /data partition for data and /home only for configuration, I guess 35GB for /home is exaggerating. IMO separate /data is useful, if you want to share data with different operating systems. (You could even use /data2 for backup in another drive, if you have possibility.) I have no experience on using /home only for configuration files.

P.S. I have made a 100MB /boot partition and it is becoming full of all those new kernels. Can you delete old kernels? How do you do it properly including cleaning the grub menu?

---

### Post by imjscn on 2008-06-27
I have no idea what is a kernels :-)

I made a big /home because I plan to install Virtual Machine to run a statistic software in Windows, I guess the VM will save its disk files in /home, so I prepared extra room for /home. 

Thanks for the suggestion! I just unmounted the /srv through Gparted. yes, it's a good idea to make a /data and /var, I'll make 5G for each of them. I normally save documents in online storage, so my /data can be small.

What do you mean "Configuration files"? In which case we need to configure files? I haven't ever know this idea, please explain?

---

### Post by jis on 2008-06-27
> **imjscn said:**
> I have no idea what is a kernels :-)

I made a big /home because I plan to install Virtual Machine to run a statistic software in Windows, I guess the VM will save its disk files in /home, so I prepared extra room for /home. 

Thanks for the suggestion! I just unmounted the /srv through Gparted. yes, it's a good idea to make a /data and /var, I'll make 5G for each of them. I normally save documents in online storage, so my /data can be small.

What do you mean "Configuration files"? In which case we need to configure files? I haven't ever know this idea, please explain?

By kernels I mean different versions of Linux. You will probably install new versions, if you keep your Xubuntu updated. Linux is (X)ubuntu's core operating system, but (X)ubuntu includes a lot of other software, too.

I am not familiar with virtual machines, but I am interested in how you get it work. Please, keep me informed. (This thread is not the right place to do it.)

By configuration files I mean the hidden files stored in your home directory by applications. Type this in terminal to get a list:
```
ls ~/.*
```
(Note that some of those directories may have subdirectories.)

---

### Post by imjscn on 2008-06-27
I see, so the configuration is not something need us to do manually :-)

I have a software can run only on Windows and I have to keep it running all the working time, that's why I choose VM over dualbooting. I tried VMware player in Windows, it's faster than I expected, will try to figure out things in Linux this weekend. If you don't mind, I'll add you in my friend list, so I can have you posted about my VM progress next week.

I use Gparted unmount and resized the /srv into /var and /data, the job applied but I got the error message like this:

failed to mount "6G" volum"
org.freedesktop.hal.sorage.mount-fixed
auth_admin_keep_always<--(action,result)

failed to mount "5G volume"
you are not privileged to mount the volum"5G volume"

the 6G is the newly created /data, 5G was the /srv(originally 11G)

in the Terminal, fdisk -l shows no problem, the 5G is sda8, 6G is sda9

I don't know what kind of trouble I'm getting into?

---

### Post by jis on 2008-06-27
Did you already install Xubuntu? Creating a separate /var partition after installing ubuntu is not trivial. /var directory exists and is probably nonempty even if there is not a separate partition for it.

---

### Post by imjscn on 2008-06-27
yes, I already isntalled Xutubu, and yes, when I mddir, it says /var already there.

I use this mounted /var

sudo mount -t ext3 /dev/sda8 /var

now, /data is not exist directory, right?

---

### Post by jis on 2008-06-27
I have /srv directory, but not in a separate partition, and the directory is currently empty. Check that you have the directory there.

I guess you have the requested partitions, but you need to set their mount points. I think you could do it in a live session you could boot from e.g. Xubuntu Desktop cd. There you should copy contents of /var (in sda1) to sda8 including subdirectories and possible hidden files, but not the directory itself. After that you could rename the /var directory (in sda1) to be /var_backup. Then edit file /etc/fstab (in sda1) by e.g. mousepad. Add two lines that begin like this: 
/dev/sda8  /var
/dev/sda9  /data
You should add something to the end of the lines. 
Command 
```
man fstab
```
in terminal tells you more. I think you can use other lines in the file as model (especially if you have same file system type in the other partitions). Both lines should end with "2" (without quotition marks); "1" is only for /.

After you have saved the file, you could try to reboot Xubuntu from hard disk and see if everything is fine. Check that ```
ls /
``` shows var and data. Finally, you might want to delete /var_backup.

---

### Post by imjscn on 2008-06-27
wait a moment, I just found something wrong in my # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4cd544d3-c87d-4ef6-bd80-58b31d33f4f9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=ace91e21-60da-4c6d-a814-ffc3616501a2 /boot           ext3    relatime        0       2
# /dev/sda5
UUID=eacac28e-428f-4a0e-acd3-76dffe68c825 /home           ext3    relatime        0       2
# /dev/sda8
UUID=effa6039-72a0-406c-98e1-bc9e2ab5bf7c /srv            ext3    relatime        0       2
# /dev/sda6
UUID=a65e392c-7f36-44a3-bfc6-02faa8b621a5 /tmp            ext3    relatime        0       2
# /dev/sda7
UUID=3aa87b31-f289-4552-99fb-20549a551323 /usr            ext3    relatime        0       2
# /dev/sda3
UUID=7876bdf1-e391-4727-9073-efa44c205819 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


sda8 was the big /srv directory, I already cut it into sda8 and sda9 and mounted the new sda8 as /var. Now in the fstab, sda8 is still /srv.
what to do with this?

---

### Post by bodhi.zazen on 2008-06-27
I moved this conversation to it's own thread for increased visibility. I apologize if I missed any posts.

At any rate to see your partitions you can try :

# list partitions
sudo fdisk -l

# show partitions + mount point
mount

# show uuid
sudo blkid

@imjscn :

You have /dev/sda8 listed twice. Typically you want to list them only once.

The default mount point for a partition is /media (in Ubuntu , some distros use /mnt for internal devices and /media for removable media)

I do not know if there is a specific reason you are using /srv

Edit fstab and change "/srv" to "/var"

```
gksu gedit /etc/fstab
```

---

### Post by jis on 2008-06-27
imjscn, maybe you didnt edit /etc/fstab as superuser so the editor couldn't save the file? On the other hand, if you did the editing in a live session like I suggested, I think you would have been able to save the file anyway.

bodhi.zazen, I don't see two sda8 in his fstab.

---

### Post by bodhi.zazen on 2008-06-27
doh - I mis read the last 3 as an 8 :lolflag:

---

