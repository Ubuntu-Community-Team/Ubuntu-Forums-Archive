---
title: "Is it possible to wipe windows from my computer?"
date: 2012-08-22
forum: New to Ubuntu
---

### Post by peterspinella on 2012-08-22
I have it set up so when i boot i can choose whether to run ubuntu or windows. i was wondering if, using ubuntu, i could wipe the computer of everything but ubuntu. if so, how do i do it?

---

### Post by vandorjw on 2012-08-22
Are you completely sure you want to do this?

If you are it is actually really easy. Start up ubuntu and open up "Disk Utility". Go to Dash home and Type Disk.

Take a good look at what you see, and look for your windows Partition. It'll have an NTFS file format. I have no idea on the amount of physical disk drives you have. (I only have one, as you can see in the picture attached.)

Once you find your windows partition, click on it, (It'll be in that horizontal bar, underneath the word volumes. Underneath the bar is a button with the word format on it. Click that.

Format it to ext4. Make sure you had Windows selected.

After this is over, start a terminal, and run "sudo update-grub"

Cheers

PS: If you want to use this newly acquired space to store your files, do the following.

1. Open a terminal and run:
sudo blkid

You'll see something like this
> blbasement@Presario-6350CA:~$ sudo blkid
[sudo] password for basement: 
/dev/sda1: UUID="708f4021-62d0-46d0-8ac2-e1e71d220743" TYPE="ext4" 
/dev/sda5: UUID="f9b395e3-9db7-4ae3-8aba-b5185a34519b" TYPE="swap" 


2. Take note of the UUID's [YOURS WILL DIFFER FROM MINE]

3. run this command:
sudo mkdir ~/My-Data

4. next, run this command:
sudo gedit /etc/fstab

It'll open the file fstab. Mine says this
> 
proc            /proc           proc    nodev,noexec,nosuid 0       0
UUID=708f4021-62d0-46d0-8ac2-e1e71d220743 /               ext4    errors=remount-ro 0       1
UUID=f9b395e3-9db7-4ae3-8aba-b5185a34519b none            swap    sw              0       0


yours will say simular stuff. Notice the UUID: you should have one missing from this file. The one that is missing, add it like this.

UUID="GET THIS FROM BLKID" /home/"YOUR-USER-NAME"/My-Data ext4 defaults 0 0

Save the file, and restart the computer.

---

### Post by peterspinella on 2012-08-22
thank you! im only doing it because i have a new computer, so im just using this old one to play around on. all my files and such have already been moved over. i want this machine to be as empty as possible. thanks again!

---

### Post by blackmail on 2012-08-22
Well now, this should be easy. you could just delete the windows partition/ partitions, and merge them. Then you could also edit the fstab file in the /etc folder, this is the file that mounts your partitions automatically.
but if you could make a better description of the layout you have i could help you better. But rest assured it can be done and it should not be a big problem.

The main operations are, backing up the data from the windows system to the linux /home partition, if any. and then deleting the windows partitions and editing the grub menu, after that forgetting that there ever was a windows on that HDD :)

---

### Post by Cheesemill on 2012-08-22
Is this a normal dual boot or did you use Wubi to install Ubuntu?

If it's a normal dual boot then all of the above suggestions are OK, but they won't work (and could wipe Ubuntu) if it's a Wubi installation.

---

### Post by coldcritter64 on 2012-08-22
> **Cheesemill said:**
> Is this a normal dual boot or did you use Wubi to install Ubuntu?

If it's a normal dual boot then all of the above suggestions are OK, but they won't work (and could wipe Ubuntu) if it's a Wubi installation.
This is a good point to note OP.

In a terminal,
```
sudo fdisk -l
```that is a lower case L.
Look at the "System" column, if it shows only NTFS, you are on a Wubi install, don't follow instructions for a partition install, as Ubuntu is actually installed into a file on the NTFS filesystem, not good to mess with, unless you like (possible) disasters.

---

### Post by vandorjw on 2012-08-22
If it is a wubi install, following my instructions will not work because OP will not be able to unmount the NTFS filesystem, and so he won't be able to format.

Since all your stuff is on a different/new computer, I suggest to just do a clean install.

---

### Post by deadflowr on 2012-08-22
> **cc7gir said:**
> 
Since all your stuff is on a different/new computer, I suggest to just do a clean install.

+1

 If the system with Ubuntu is just for messing around I'd wholeheartedly suggest reinstalling it as the lone OS. Wipe everything and start anew. If it is a WUBI install, then download and burn the latest ISO from Ubuntu. Nothing beats learning Ubuntu like a system that you can go full-throttle on, without worrying about losing vital data.
Here's the link in case
[http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

---

