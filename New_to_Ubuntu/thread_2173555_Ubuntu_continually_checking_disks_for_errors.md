---
title: "Ubuntu continually checking disks for errors"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by han2 on 2013-09-10
Hello, everytime I start the computer Ubuntu checks disks for errors, and it takes a lot of time. Is there any way to stop Ubuntu from doing so?

---

### Post by Mark Phelps on 2013-09-10
> Is there any way to stop Ubuntu from doing so?  NOT really a good idea -- the repeated filesystem checks indicates an underlying problem with the drive.  Most likely, the drive is failing.  If you disable the filesystem checks, that is not going to do anything useful about the drive.

---

### Post by han2 on 2013-09-10
I see. I don't understand why it happens. The computer always shuts down correctly and everything seems to be working fine. 

This is the second time I have Ubuntu installed. The first one I installed it solely (without any other OS), and never had this problem. Now I have Ubuntu installed along with Windows XP (first I installed Win XP in one partition, then I installed Ubuntu in the other one), so it seems the problem has something to do with that, but I don't know how to solve it. :-?

---

### Post by newb85 on 2013-09-10
Have you tried viewing the SMART data for the drive in gparted?

---

### Post by deadflowr on 2013-09-10
> **han2 said:**
> Hello, everytime I start the computer Ubuntu checks disks for errors, and it takes a lot of time. Is there any way to stop Ubuntu from doing so?

It is possible, but as stated not really recommended to do so as it won't solve or make none existing disk problems.
You'd have to change the pass number from 1 to 0 in the fstab file.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You'd probably be better served posting the result of SMART
look here
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

### Post by han2 on 2013-09-15
Thanks newb85 and deadflowr. I've checked the drive in Gparted and there seems to be a problem with the linux-swap partition.

[IMG]http://s21.postimg.org/gcujhfg87/Gparted.png[/IMG]

After seeing that, I used the live-cd to reformat /dev/sda5 to linux-swap. Reboot, and when I enter (after checking drives for errors) in Ubuntu it finds a problem with blueman (something I don't use). I check the drive in Gparted and everything seems fine. I reboot again, Ubuntu keeps checking the drive for errors, I check the drive in Gparted, and the linux-swap partition has disappeared again. So this time instead of just reformating /dev/sda5 I decide to delete /dev/sda5 and /dev/sda3 and start anew. This time, I create a new primary partition (not extended), and set it to linux-swap. Now, linux keep checking drives for errors and I have the following message:

> /dev/mapper/cryptswap1 not ready or not present

I guess I have to set the linux swap partition in Ubuntu to /dev/sda3. How can I do that? Is it better to have the linux-swap partition as a primary partition or as an extended one?

Sorry for this long message.

---

### Post by coffeecat on 2013-09-15
This:

> **han2 said:**
> /dev/mapper/cryptswap1 not ready or not present 

Means that your system is looking for an encrypted swap partition (presumably you chose an encrypted home when you installed?). The unknown message you saw in Gparted for sda5 before you removed it is what Gparted shows when confronted with an encrypted swap. My guess is that your original problem is nothing to do with the swap partition.

I notice that your / (root) sda1 partition is formatted ext2, which is a non-journalled filesystem, more at risk of corruption than ext3 or ext4. One likely explanation for what you describe in your OP is that there is filesystem damage, possibly serious. Why did you choose ext2 when you first installed?

---

### Post by han2 on 2013-09-15
Thanks for your response coffeecat. 

Well, right now I'm not sure what I chose when I installed Ubuntu, but I think I selected the encrypted home option as I wanted maximum security (Is there any way to check if my home is encrypted?). As for ext2, I'm also not sure why I chose that option. Maybe I thought it will work better to move files between Ubuntu and WinXP partitions, or I read something somewhere... I don't know. I'm a total beginner, I'm sorry. I guess is not possible to change a partition from ext2 to ext3 without formatting, am I guessing right?

I'll try to check the filesystem with the live cd to see what happens.

---

### Post by coffeecat on 2013-09-15
> **han2 said:**
> Well, right now I'm not sure what I chose when I installed Ubuntu, but I think I selected the encrypted home option as I wanted maximum security (Is there any way to check if my home is encrypted?).

Run this terminal command:

```
ls -A ~
```

Check to see if there is a folder named .ecryptfs. If there is then your home is encrypted.

> **han2 said:**
> As for ext2, I'm also not sure why I chose that option. Maybe I thought it will work better to move files between Ubuntu and WinXP partitions, or I read something somewhere... 

Maybe you came across an old howto which recommended the use of a Windows driver for ext2 fileystems. I believe there are Windows drivers for ext4 now, but I wouldn't touch them myself. Since the Microsoft NTFS filesystem is handled well in Xubuntu/Ubuntu, I prefer to set up a shared data partition, formatted NTFS, for use between both operating systems when dual-booting Ubuntu and Windows. 

> **han2 said:**
> I guess is not possible to change a partition from ext2 to ext3 without formatting, am I guessing right?

It is possible, but you would need to edit /etc/fstab as well as running a terminal command to add an ext3 journal to the ext2 filesystem. However, since it is possible that you have major filesystem corruption, you have the complication of getting a usable swap partition back, and you might want to think about a separate NTFS data partition, it might be quicker in the long run to backup your personal files and do a fresh install. 100GB is rather large for an Ubuntu/Xubuntu root partition. You could use a lot of that for a separate data partition. Don't forget to check the SMART data for your drive, as a failing drive is still a possibility. In Ubuntu with the Unity desktop, you use the app variously named "Disks" or "Disk Utility" depending on release to check for SMART data, but I don't know whether that's included in Xubuntu.

> **han2 said:**
> I'll try to check the filesystem with the live cd to see what happens.

Good idea, but think about a reinstall after you've checked the SMART status.

---

### Post by han2 on 2013-09-21
Sorry for the delay in replying. Thanks again for your response, coffeecat.

> **coffeecat said:**
> Run this terminal command:

```
ls -A ~
```

Check to see if there is a folder named .ecryptfs. If there is then your home is encrypted.

Yes, I have the folder.

> **coffeecat said:**
> [...] it might be quicker in the long run to backup your personal files and do a fresh install. 100GB is rather large for an Ubuntu/Xubuntu root partition. You could use a lot of that for a separate data partition.

I think I'll do that. I don't have many files to backup, so I prefer to start anew, formatting the Ubuntu partition as ext3.

> **coffeecat said:**
> Don't forget to check the SMART data for your drive, as a failing drive is still a possibility. In Ubuntu with the Unity desktop, you use the app variously named "Disks" or "Disk Utility" depending on release to check for SMART data, but I don't know whether that's included in Xubuntu.

I've checked the SMART with "Disks" (using Xfce, as I couldn't access the utility using Xubuntu) and everything is OK, but there's a message saying that the partition has not been correctly unmounted. So I guess that's the problem, although the computer always seems to shut down fine.

I read in another post that some user had the same problem, and it was related to the network drivers. But I tried disabling the network before shutting down the computer, and Ubuntu keeps checking the drives at every boot. Apart from that, I keep getting a recurring message about the blueman-applet crashing. I'm not using bluetooth so I could try disabling blueman, how could I do that?

I'm a total newbie with Xubuntu/Ubuntu/Linux, but the more I use it the more I like it. I'm even enjoying working with the terminal, something that terrified me at first :roll:

---

