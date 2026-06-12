---
title: "how can i safely delete ubuntu temp files by putty?"
date: 2024-06-03
forum: New to Ubuntu
---

### Post by oeyestvd on 2024-06-03
Hello! i am suspicious about having a full harddrive on ubuntu. i can only access it by putty, how can i safely delete content (temporary? or not necessary files) by command? can someone give some help?

---

### Post by oeyestvd on 2024-06-03
More information: I have inherited an ubunt running 20.04.02 LTS with an OsTicket server. Its working fine since 2021. This morning i woke up with the error "http 500 error" when i try to access the ubuntu server through IP/browser.  Altough i can access it by putty, however i am affraid of doing something wrong. I have a 500gb ssd and i think its impossible the database is taking that much space so can it be some temporary files or updates consuming all the space? how can i find out this? thanks!

---

### Post by currentshaft on 2024-06-03
"df -h" will show you volumes and how much they've used

"du -hd1 ." will print directory sizes under the current working directory. You can run it in your homedir and the root directory ("/") to find what's taking up space.

My guess is no one set up log rotation and /var/log is completely full.

---

### Post by ActionParsnip on 2024-06-03
What is the output of:
```

cd /; du -sh *; echo; df -h | grep -v tmpfs

```
This will give us the size of all directories and the file system sizes

---

### Post by oeyestvd on 2024-06-03
hi! i am having alot of permission denied so i unplugged the ssd and i installed the ssd on another ubuntu computer.
I plugged the ssd by an USB interface to a laptop with ubuntu. one partition popped up (around 2.7gb) with "efi" and "grub" on the inside, no other partitions appeared. i did a 'sudo fdisk -l' and i see a /dev/sda3/ with 444.1Gb which i guess its tha partition i am looking for. so i did 'sudo mount /dev/sda3/ /mnt' and i am getting this: "mount: /mnt unkown filesystem type 'LVM2_member'. dmesg(1) may have more information after failed mount system call. Any hint on what should i do next? thanks!

---

### Post by oeyestvd on 2024-06-03
update:
i installed lvm2 using "[FONT=var(--ff-mono)]$ sudo apt-get install lvm2" and after that i can see the partition on ubuntu but i cant delete files. only see.
[/FONT]hints? thanks!

edit: maybe i should close this thread and start a new one since the subject its completely different?

---

