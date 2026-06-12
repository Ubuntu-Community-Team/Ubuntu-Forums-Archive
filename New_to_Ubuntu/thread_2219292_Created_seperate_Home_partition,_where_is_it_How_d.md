---
title: "Created seperate /Home partition, where is it? How does this work exactly?"
date: 2014-04-23
forum: New to Ubuntu
---

### Post by cadenza2 on 2014-04-23
Dual boot with ubuntu 14.04 installed alongside Windows 8. 
Created a seperate /Home partition during ubuntu installation (/, /Home, and swap partitions).
My question is, where is it? How does this exactly work? As much as I've read about it, I'm still kind of at a loss here simply because my Home directory via the File Manager appears to be the size of the root partition (<40 gb) and not the /home partition (~400 gb).
Using the live usb, I checked the partitions and they all exist (and /home appears on the sidebar. Properties show correct size and is listed under root)
How do I get the files that I want into this /home partition? The answer must be incredibly obvious for the simple lack of questions regarding it.

[html]
NAME   FSTYPE   SIZE MOUNTPOINT                        LABEL
sda           931.5G                                   
&#9500;&#9472;sda1 vfat     100M /boot/efi                         SYSTEM
&#9500;&#9472;sda2          128M                                   
&#9500;&#9472;sda3 ntfs   462.2G                                   OS
&#9500;&#9472;sda4 ntfs    10.9G                                   HP_RECOVERY
&#9500;&#9472;sda5 ext4    41.9G /                                 
&#9500;&#9472;sda6 ext4   402.4G /HOME                             
&#9492;&#9472;sda7 swap      14G [SWAP]                        [/html]

No clue how to wrap the information, just used html.

---

### Post by Paulgirardin on 2014-04-23
You don't need to do anything special.The system will function the same as if  /home  is on the same partition as / . The main difference is that you can reinstall the OS and retain retain your previous settings in /home.Also you can install other *buntus and use the same /home.

---

### Post by cadenza2 on 2014-04-23
Okay, so what happens with the size? I've tried (to test this out) transferring a bunch of files greater than the root size partition. It will not let me (as there is not enough space). How do I access the 400gb?

---

### Post by Impavidus on 2014-04-23
Partitions are mounted at a directory. So if your /home partition is indeed properly mounted at the /home directory, any file stored in the /home directory is automatically on the /home partition. And it's /home, not /Home or /HOME. Linux is case sensitive.

To find out if it has been mounted properly, run these commands in a terminal. You can copy-paste them one by one. There is a graphical way too but that's too complicated to explain in a forum post. It will ask for your password, which you'll have to enter blindly:```
# This one will list partitions, labels and UUIDs.
sudo blkid

# This one will list partition sizes. Note the lower case L.
sudo parted -l

# This one will list the currently mounted file systems.
mount

# This one will show the contents of the fstab file, showing which partitions shoud be automounted where.
cat /etc/fstab
```

---

### Post by CraigPid on 2014-04-23
I notice that /dev/sda4 is mounted on /HOME. Unix file system is case sensitive. It should be /home or even better /home/username. You probably don't even have a /HOME folder. You could create /HOME on your root directory and then in a terminal enter "sudo mount -a". The better option would be to edit /etc/fstab so that /dev/sda4 mounts on /home/your_username so that you don't run into permission problems. "sudo gedit /etc/fstab" in a teminal and look for the line about /dev/sda4 and change /HOME to /home/your_username. Then "sudo mount -a". Leave out the quotation marks of course.Good luck.

---

### Post by bab1 on 2014-04-23
> **cadenza2 said:**
> Okay, so what happens with the size? I've tried (to test this out) transferring a bunch of files greater than the root size partition. It will not let me (as there is not enough space). How do I access the 400gb?
With this you can see what is mounted at /home```
sudo blkid -c /dev/null -o list
```

With this you can see how much storage you have available for each mounted partition```
df -h
```

---

### Post by cadenza2 on 2014-04-23
> **CraigPid said:**
> I notice that /dev/sda4 is mounted on /HOME. Unix file system is case sensitive. It should be /home or even better /home/username. You probably don't even have a /HOME folder. You could create /HOME on your root directory and then in a terminal enter "sudo mount -a". The better option would be to edit /etc/fstab so that /dev/sda4 mounts on /home/your_username so that you don't run into permission problems. "sudo gedit /etc/fstab" in a teminal and look for the line about /dev/sda4 and change /HOME to /home/your_username. Then "sudo mount -a". Leave out the quotation marks of course.Good luck.

this was the key issue. reinstalled with /home and now i've got it. What a silly mistake. it definitely wasn't mounted at /home (root had ownership and i couldn't access it).

thanks for everyone helping me.

---

