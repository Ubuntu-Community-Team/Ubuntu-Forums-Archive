---
title: "Swap files"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Troll_the_Great on 2008-05-27
I have recently installed Ubuntu, but I didn't create a partition for swap...Can I create a swap file instead?I don't want to mess with my partitions again.If yes, how? I am a newbee to linux so please guide me step by step.Thx alot.

---

### Post by sayakb on 2008-05-27
Open GParted and shrink any of the existing partitions by the size of the swap you want. Then just create a new partition out of the Unpartitioned space so formed and set the filesystem as Linux Swap. Apply the changes. Then right click on the newly formed swap and select Swapon.

---

### Post by sayakb on 2008-05-27
Now open a terminal and type:
```
sudo fdisk -l
```Anyway, from the above output, check the device link for the swap. For example, it is /dev/sda3
Then at a terminal, type:
```
gksudo gedit /etc/fstab
```A file would open. There, add a line like this at the end:
```
/dev/sda3   swap   swap    defaults   0 0
```Save this and close the file.
This would mount the swap automatically on startup.
Now reboot again and check the system monitor (System->Admnistration->System monitor->Resources tab) for Memory and swap utilization, or just type this to the terminal to view memory and swap:
```
free -m
```

---

### Post by Troll_the_Great on 2008-05-27
I told you I am a noob (zero, nothing, nada, niente) when it comes to linux.I don't know what GParted is, or how to open it.I use dual boot with windows.If I create that partition if wouldn't affect my windows system?Can't I create a swap file instead?Isn't it easier?

---

### Post by sayakb on 2008-05-27
No, creating a swap will not affect your Windows partition.
Now, open a terminal and type:
```
sudo apt-get install gparted
```After it is installed, goto System->Administration->Partition editor.

EDIT: Read [here]("http://www.howtoforge.com/partitioning_with_gparted") for more information. This explains how to resize a drive. After resizing, you are left with some unpartitioned space. This unpartitioned space is a RAW partition. Right-click on the new partition and select "New". There, you have to specify the "filesystem" as Linux-Swap. After doing this, Press Apply button. 
After the changes are applied, you can see your swap partition right there. Just right click on it and click on SwapOn. That would activate the swap. Now follow post #3 as indicated above.

---

### Post by Troll_the_Great on 2008-05-27
Thanks  alot, I will tell you if it worked.

---

### Post by sayakb on 2008-05-27
Creating a swap file: read [here]("http://www.redhat.com/docs/manuals/enterprise/RHEL-5-manual/Deployment_Guide-en-US/s2-swap-creating-file.html")

---

### Post by sayakb on 2008-05-27
> **Troll_the_Great said:**
> Thanks  alot, I will tell you if it worked.

Okay sure. Better to make an entire swap partition than a swap file. ;)

---

### Post by 3rdalbum on 2008-05-27
How much RAM have you got? I get along perfectly well without swap. Unlike Windows, where it uses 400 megabytes of swap even when it doesn't need it; Linux doesn't start using swap unless it's getting low on RAM.

Got a gigabyte? You don't need swap. I've got two gigs of RAM and the closest I came to using it all was when a program in Wine started leaking memory badly :-)

---

### Post by Troll_the_Great on 2008-05-27
I have 1024 MB RAM.It is enough?I don't need swap?And if I do need, how much?

---

